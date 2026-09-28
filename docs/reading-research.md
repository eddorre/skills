# Reading research: comprehension, speed, and what helps

Status: research findings, 2026-09-27. These are the sources behind the `reader-first` skill (`skills/writing/reader-first/`).

Verification tags: [paper] full text checked, [abstract] official abstract checked, [snippet] search results only, [not peer-reviewed] practitioner, vendor, or doctrine source. Treat [snippet] figures as unconfirmed.

## Summary

People decide within seconds whether to keep reading, and they give the most attention to the start of a document, a section, and a paragraph. Careful reading of non-fiction runs about 240 words per minute, and slower for dense or technical text. Working memory holds about four items. The best-supported interventions are signaling (meaningful headings, a preview up front), cutting material the reader doesn't need, putting the conclusion or action first, and plain syntax. More explanation raises readers' trust in AI output without making them more accurate. Reviewing AI-drafted text has so far cost professionals time rather than saving it, partly because the drafts are too long.

## 1. General reading

### Speed

- Adult silent reading in English averages 238 wpm for non-fiction and 260 for fiction, with most adults between 175 and 300. The popular 300+ figures are overestimates. Brysbaert 2019, J. Memory and Language 109:104047, doi:10.1016/j.jml.2019.104047 [abstract]
- Readers change rate with their goal. Carver's rates for college students are scanning 600, skimming 450, normal reading 300, learning 200, and memorizing 138. These are six-character "standard words", not actual words. Normal reading in actual words fell from about 320 wpm on easy text to about 200 on graduate-level text. Carver 1997, Sci. Studies of Reading 1(1):3-43, doi:10.1207/s1532799xssr0101_2 [paper]
- Readers can't go much faster than about 250 wpm without losing comprehension, and speed reading doesn't avoid that. Skimming runs 2-4x faster, with lower comprehension. Rayner et al. 2016, PSPI 17(1):4-34, doi:10.1177/1529100615623267 [paper]
- IReST's 184 wpm, which is often quoted, is for reading aloud. Trauzettel-Klosinski & Dietz 2012, doi:10.1167/iovs.11-8284 [abstract]

Estimated reading times at these rates:

| Words | ~240 wpm (non-fiction) | ~200 wpm (learning, technical) | ~138 wpm (close study) |
| --- | --- | --- | --- |
| 250 | 1 min | 1.3 min | 1.8 min |
| 500 | 2.1 min | 2.5 min | 3.6 min |
| 1,000 | 4.2 min | 5 min | 7.2 min |
| 2,500 | 10.4 min | 12.5 min | 18 min |

### Skimming and stopping

- Visitors leave web pages quickly. In one study, 52% of page visits lasted under 10 s and 25% lasted under 4 s. Pages abandoned within 12 s averaged 430 words. Weinreich et al. 2008, ACM TWeb 2(1), doi:10.1145/1326561.1326566 [paper]
- The chance a reader leaves a page is highest in the first few seconds and falls after that. A page has to pass a quick screening before anyone reads it closely. Liu, White & Dumais 2010, SIGIR, doi:10.1145/1835449.1835513 [abstract]
- When readers only had time for half a text, skimming preserved the important ideas better than reading half, but it did not help with details or inferences. Skimmers concentrate on the start of paragraphs, the top of pages, and early pages. Duggan & Payne 2009, JEP: Applied 15(3):228-242, doi:10.1037/a0016995 [abstract]
- Skimmers keep reading a section until they stop learning much from it, then jump to the next. Duggan & Payne 2011, CHI, doi:10.1145/1978942.1979114 [paper]
- Readers who pay more attention to headings write better summaries. Hyönä et al. 2002, cited in Rayner 2016 [paper]

### Memory, attention, and screens

- Working memory holds about 4 chunks. Miller's "7 ± 2" is outdated. Cowan 2001, BBS 24:87-114, doi:10.1017/S0140525X01003922 [abstract]
- The mind wanders during roughly 15-40% of reading. In Schooler et al. 2004, readers were caught mind wandering at 13% and 23% of probes in two experiments [paper]. In Feng, D'Mello & Graesser 2013, the rates were 36% on easy texts and 42% on difficult ones [paper]. The widely repeated "20-40%" does not appear in Schooler 2004. Mind wandering is weakly negatively correlated with comprehension (r = −.21). Bonifacci et al. 2022, doi:10.3758/s13423-022-02141-w [abstract]
- Mind wandering is more frequent, and more damaging, on difficult text. Feng, D'Mello & Graesser 2013, doi:10.3758/s13423-012-0367-y [abstract]
- Lapses early in a text do the most harm. Smallwood et al. 2008, doi:10.3758/MC.36.6.1144 [abstract]
- For informational text, comprehension on screens is worse than on paper (g ≈ −.21 to −.32), and the gap is larger under time pressure. Delgado et al. 2018, doi:10.1016/j.edurev.2018.09.003 [paper]; Clinton 2019, doi:10.1111/1467-9817.12269 [abstract]
- Screen readers overestimate how well they understood (g = .20). Clinton 2019 [abstract]; Ackerman & Goldsmith 2011, doi:10.1037/a0022086 [abstract]

## 2. Software engineering

- Reviewers' main job is understanding the change, and current tools don't support that well. Finding defects was developers' top stated motive for review, but defects made up only 14% of review comments. Bacchelli & Bird 2013, ICSE, doi:10.5555/2486788.2486882 [paper]
- Cisco's review data supports keeping reviews under 200-400 LOC and under 60-90 minutes. Authors who annotated their own changes had far fewer defects. Cohen 2006, SmartBear [paper, not peer-reviewed]
- At Google the median change is 24 lines. Small changes get their first feedback in under an hour, and very large ones take about 5 hours. Sadowski et al. 2018, ICSE-SEIP, doi:10.1145/3183519.3183525 [paper]
- Developers say a change is reviewable when it has a good description, a small size, and a coherent commit history. Ram et al. 2018, FSE, doi:10.1145/3236024.3236080 [paper]
- More than 34% of PRs have no description at all. Liu et al. 2019, ASE, arXiv:1909.06987 [abstract]
- Across 18,256 PRs with Copilot-drafted descriptions, compared with 54,188 without, review time dropped by an average of 19.3 hours and the odds of merging were 1.57 times higher. Developers often edited the drafts. Xiao et al. 2024, FSE, doi:10.1145/3643773, arXiv:2402.08967 [paper]
- Developers spend about 58% of their time on comprehension, much of it outside the IDE. Xia et al. 2018, TSE, doi:10.1109/TSE.2017.2734091 [abstract]
- Developers read documentation opportunistically, scanning for one specific item and leaning on code examples. Meng et al. 2019, doi:10.1145/3274995.3274999 [paper]
- Developers read code less linearly than prose, and experts less linearly than novices. Busjahn et al. 2015, ICPC, doi:10.1109/ICPC.2015.36 [abstract]
- After an interruption, only 10% of sessions resumed editing within a minute. Parnin & Rugaber 2011, doi:10.1007/s11219-010-9104-9 [abstract]
- Developers most value steps to reproduce, stack traces, and test cases in a bug report. Bettenburg et al. 2008, FSE, doi:10.1145/1453101.1453146 [abstract]

Reviewing AI output:

- With an LLM reviewer, 73.8% of the bot's comments were resolved, but mean PR closure time rose from 5h52m to 8h20m, and developers reported irrelevant comments. Cihan et al. 2025, ICSE-SEIP, arXiv:2412.18531 [abstract]
- Participants with an AI assistant wrote less secure code and were more confident that it was secure. Perry et al. 2023, CCS, doi:10.1145/3576915.3623157 [abstract]
- Experienced OSS developers were 19% slower with AI but believed they were 20% faster. Becker et al. (METR) 2025, arXiv:2507.09089 [preprint, not peer-reviewed]

## 3. Other domains

### Medicine

- Physicians spend about 5.9 of an 11.4-hour workday in the EHR. Arndt et al. 2017, doi:10.1370/afm.2121 [abstract]
- Median note length rose 60% from 2009 to 2018 (401 to 642 words). By 2018, 58.8% of each note's text was duplicated from the previous note. Rule et al. 2021, JAMA Netw Open, doi:10.1001/jamanetworkopen.2021.15334 [paper]
- APSO puts the assessment and plan first. Of 64 clinicians surveyed, 81% said relevant data was easier to find and 83% said they browsed notes faster, but most noticed no difference in writing time. When 14 providers were timed answering questions from APSO and SOAP notes, there was no difference in time (P = .37) or errors (3/120 vs 4/120). The benefit is perceived, not measured. Lin et al. 2013, JAMA Intern Med 173(2):160-162 [paper]
- With AI-drafted patient replies, physicians spent 21.8% more time reading, reply time did not change significantly, and replies got 17.9% longer. Tai-Seale et al. 2024, doi:10.1001/jamanetworkopen.2024.6565 [paper]
- Clinicians used about 20% of AI drafts, and complained they were too long and sounded robotic. Task load still improved. Garcia et al. 2024, doi:10.1001/jamanetworkopen.2024.3201 [paper]
- In LLM clinical notes, 1.47% of 12,999 note sentences were hallucinated, and 44% of those errors were rated major. Separately, 3.45% of 49,590 source-transcript sentences were omitted, and 16.7% of those omissions were rated major. The rates use different denominators, so they can't be compared directly. Hallucinations were more often serious. Asgari et al. 2025, npj Digit Med 8:274, doi:10.1038/s41746-025-01670-7 [paper]

### Law

- Center-embedded clauses, jargon, and passives lowered recall and comprehension of legal text, even for experienced readers. The difficulty comes from poor writing, not from specialized legal concepts. Martínez, Mollica & Gibson 2022, Cognition, doi:10.1016/j.cognition.2022.105070 [abstract]
- Terms of service should take 15-17 minutes to read. People actually spent 51 s on average, and 98% missed a planted "first-born child" clause. Obar & Oeldorf-Hirsch 2020, doi:10.1080/1369118X.2018.1486870 [abstract]
- Of 153 US judges who returned a plain English vs legalese survey, 66% of those stating a preference chose plain English. Flammer 2010, J. Legal Writing Inst. 16:183-221 [paper]. Kimble's surveys of Michigan judges and lawyers found 80-85% preferred plain English [not peer-reviewed].

### Business, government, military

- For 262 naval officers, memos with the main point first, short length, and active voice took 17-23% less time to read, with better comprehension. This is the best empirical test of BLUF-style writing found. Suchan & Colucci 1989, doi:10.1177/0893318989002004002 [abstract]
- The Minto pyramid principle, Army AR 25-50's BLUF rule, the email length data (Boomerang), and the plain-language cost savings (Kimble) are all practitioner sources or doctrine with no peer-reviewed tests.

## 4. What improves comprehension

Ranked by strength of evidence.

1. Signaling: headings, a preview up front, and cue phrases. Across 103 studies, retention improved by g = .52 and transfer by g = .31. Prior knowledge did not change the effect, so it helps experts too. Signaling redirects attention to the cued content. Schneider et al. 2018, Educ. Res. Review 23:1-24 [abstract]; Lorch 1989, doi:10.1007/BF01320135 [abstract]
2. Cutting material the reader doesn't need. Interesting but irrelevant details ("seductive details") reduce learning. Rey 2012 found small-to-medium harm to retention and medium harm to transfer [abstract]. Harp & Mayer 1998 found the damage is worst when the details come first [abstract]. Sundararajan & Adesope 2020 (doi:10.1007/s10648-020-09522-4) is closed access. A peer-reviewed secondary source (PMC8442593) reports its figures as 58 papers, 68 effect sizes, and N = 7,521, with retention g = −.37, retention and transfer combined g = −.41, and no significant effect on transfer alone. Those numbers are secondhand; confirm them from the PDF before citing. In Mayer et al. 1996, college students who read a short captioned summary recalled the steps and solved transfer problems "as well as or better than" students given the 600-word text, and adding text to the summary reduced its effectiveness. doi:10.1037/0022-0663.88.1.64 [abstract]. Whether the participants were screened as low-knowledge is unverified.
3. Main point first, with plain syntax. Suchan & Colucci 1989 and Martínez et al. 2022, above.
4. Evidence next to the claim it supports. Placing related information together helps, most of all for complex material. Ginns 2006 [abstract]
5. Matching detail to expertise. Explanation that helps novices can hurt experts, and readers who know the subject can learn more from terse text because filling the gaps forces them to think. Kalyuga et al. 2003, doi:10.1207/S15326985EP3801_4 [abstract]; McNamara et al. 1996, doi:10.1207/s1532690xci1401_1 [abstract]
6. Tables for parallel facts. In a registered report with N = 2,305, fact boxes beat text on comprehension (79.6% vs 69.7%, d = .39). Brick et al. 2020, doi:10.1098/rsos.190876 [paper]. Bulleted lists improve recall of the list items but reduce recall of the prose around them. Jansen 2014 [abstract]

Weak or counterproductive:

- Advance organizers help learning and retention across 135 studies, but the effect sizes couldn't be verified. The often-quoted ES ≈ .21/.26 traces only to a blog. The studies are also old. Luiten et al. 1980, doi:10.3102/00028312017002211 [abstract]
- Readability formulas such as Flesch predict comprehension poorly, so they make a bad target. Crossley et al. 2017, doi:10.1080/0163853X.2017.1296264 [abstract]
- Layered disclosure was faster but less accurate. With layered privacy policies, readers took 5.7 minutes against 8.2 for the full text. But when the answer wasn't in the short layer, they didn't go on to the full policy: accuracy on one such question was 28%, against 39% for the full text. McDonald et al. 2009, PETS, doi:10.1007/978-3-642-03168-7_3 [paper; the digits were extracted from a garbled PDF, so they are high-confidence rather than certain]

### Trust in AI text

- Explanations raised acceptance of AI recommendations whether the AI was right or wrong. Bansal et al. 2021, CHI, doi:10.1145/3411764.3445717 [abstract]
- Readers over-rely on AI output when checking it is costly. Explanations that were harder to read increased over-reliance. Vasconcelos et al. 2023, arXiv:2212.06823 [abstract]
- Longer LLM explanations raised user confidence without improving accuracy. Stating uncertainty in words that match the model's confidence narrowed the gap. Steyvers et al. 2025, Nat. Mach. Intell., doi:10.1038/s42256-024-00976-7 [abstract]
- Citing sources and pointing out inconsistencies reduced reliance on wrong answers. Kim et al. 2025, CHI, doi:10.1145/3706598.3714020 [abstract]

## Commonly misquoted figures

- The F-pattern article is NN/g 2006, and "How Little Do Users Read?" is 2008. Neither is peer-reviewed. The 20-28% figure is Nielsen's own calculation from Weinreich et al.'s data.
- Carver's rates are in six-character standard words.
- The mind-wandering "20-40%" figure is misattributed to Schooler 2004. The primary studies found 13-42%.
- The seductive-details figures first reported here (g = −.16 and similar) could not be traced to any source and were replaced.
- Cohen 2006 and Kimble are not peer-reviewed.
- "Let the reader ask for depth" conflicts with the layered-disclosure evidence. Anything the reader must act on belongs in the part they will actually read.

## Open tensions

- Brevity versus completeness. Short text helps experts and cuts out distracting detail, but LLM summaries do omit source material (Asgari: 3.45% of transcript sentences). The skill needs a way to say what was left out without including it.
- Expertise. The right depth depends on the reader, and the agent often doesn't know who that is.
- Evidence gaps. There's no peer-reviewed study of LLM-written reports or PR reviews and their length. Most of the professional-domain evidence measures time or self-report, not comprehension.
