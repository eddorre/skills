# Examples

## PR description

The reader is the PR reviewer, an engineer who knows the codebase but not this session.

### Before (about 230 words)

```markdown
## Summary
This PR introduces a comprehensive improvement to the order sync pipeline to
enhance reliability and robustness. I started by exploring the codebase to
understand how order syncing currently works, then identified that failures
from the upstream fulfillment API were not being handled gracefully.

## Changes
- Added `RetryPolicy` class in `sync/retry.py`
- Updated `OrderSyncWorker` to use `RetryPolicy`
- Implemented exponential backoff with jitter
- Added configuration options
- Added unit tests
- Updated documentation

## Motivation
Previously, when the fulfillment API returned errors such as 503 Service
Unavailable, the worker would log the error and move on, which meant that
orders could be lost. Exponential backoff is a well-established pattern for
handling transient failures in distributed systems, as it prevents
overwhelming a recovering service...

## Testing
I added comprehensive unit tests covering the retry logic and verified that
all existing tests pass.

## Notes
Let me know if you have any questions or would like changes!
```

### After (about 110 words)

```markdown
Retry order sync on upstream 503s instead of dropping the order

Orders were silently lost when the fulfillment API returned 503, about 40 a
day in last week's logs. The worker now retries up to 5 times over ~2 minutes,
then sends the order to the dead-letter queue.

Please check: the 2-minute cap in `sync/retry.py:30-58`. Longer means fewer
dead letters but blocks the worker; I picked 2 minutes because the API's
outages in the logs lasted under 90 seconds.

Not in this PR: `payments/retry.py` does the same job. Worth merging later.

Tested: replayed last week's 41 failed orders against staging; all 41 synced.
```

### What changed

1. The title and first sentence now give the problem and the fix. Before, the reader had to get through the process story to find them.
2. "I started by exploring the codebase" and the paragraph explaining exponential backoff are cut. The reviewer doesn't need the first, and already knows the second.
3. The file list is cut because the diff shows it. Those words now go to the one decision that needs review and the reason for it.
4. "Please check" points at the decision and gives its line range, so the reviewer knows where to look.
5. "Comprehensive unit tests" became a result the reviewer can check: 41 of 41 replayed orders synced.
6. One line names the related code that was left out on purpose, so the reviewer doesn't wonder whether it was missed.
7. The closing offer is cut. It told the reviewer nothing.

Removing what the reader didn't need made it half as long.
