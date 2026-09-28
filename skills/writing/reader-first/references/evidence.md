# Evidence behind the rules

Each rule in `SKILL.md` and the research that supports it. Tags show how each source was checked: [paper] means the full text, [abstract] means the official abstract only, and [secondhand] means the figures come from another peer-reviewed paper that cites it. Full notes are in the repo's `docs/reading-research.md`.

## Reading rates and attention

- Adults read non-fiction silently at about 238 wpm on average, with most between 175 and 300. Brysbaert 2019, J. Memory and Language 109:104047, doi:10.1016/j.jml.2019.104047 [abstract]
- Reading speed depends on the goal. For college readers, learning runs about 200 wpm and memorizing about 138, both measured in 6-character standard words. Normal reading falls to about 200 actual words per minute on graduate-level text. Carver 1997, Sci. Studies of Reading 1(1):3-43, doi:10.1207/s1532799xssr0101_2 [paper]
- Readers can't go much past about 250 wpm without losing comprehension. Rayner et al. 2016, PSPI 17(1):4-34, doi:10.1177/1529100615623267 [paper]
- Working memory holds about four chunks. Cowan 2001, BBS 24:87-114, doi:10.1017/S0140525X01003922 [abstract]
- Readers' minds wander during roughly 15-40% of reading, and more often on hard text. Schooler et al. 2004 [paper]; Feng, D'Mello & Graesser 2013, doi:10.3758/s13423-012-0367-y [paper]
- On screen, readers understand informational text less well than on paper, and they overestimate how much they understood. Delgado et al. 2018, doi:10.1016/j.edurev.2018.09.003 [paper]; Clinton 2019, doi:10.1111/1467-9817.12269 [abstract]

## Lead with the outcome; put anything that needs action where it will be read

- 52% of web page visits lasted under 10 s. Pages left within 12 s averaged 430 words. Weinreich et al. 2008, ACM TWeb 2(1), doi:10.1145/1326561.1326566 [paper]
- The chance of leaving a page is highest in its first few seconds. Liu, White & Dumais 2010, SIGIR, doi:10.1145/1835449.1835513 [abstract]
- Skimmers spend more time early in paragraphs and pages. They move to the next section once the current one stops paying off. Duggan & Payne 2009, doi:10.1037/a0016995 [abstract]; 2011, doi:10.1145/1978942.1979114 [paper]
- 262 naval officers read memos that put the main point first, kept it short, and used active voice 17-23% faster, and understood them better. Suchan & Colucci 1989, Mgmt Commun Q 2(4), doi:10.1177/0893318989002004002 [abstract]
- Readers of layered privacy notices rarely went on to the full policy. When the answer wasn't in the short layer, accuracy fell to 28%. McDonald et al. 2009, PETS, doi:10.1007/978-3-642-03168-7_3 [paper]
- People spent a mean of 51 s on terms of service that take 15-17 minutes to read, and 98% missed a planted clause. Obar & Oeldorf-Hirsch 2020, doi:10.1080/1369118X.2018.1486870 [abstract]
- Of 64 clinicians, 81% said data was easier to find in assessment-first (APSO) notes. When timed, they read APSO and SOAP notes equally fast, so the benefit was perceived rather than measured. Lin et al. 2013, JAMA Intern Med 173(2):160-162 [paper]

## Open each section and paragraph with its point

- A meta-analysis of 103 studies found signaling (headings, previews, cue phrases) improved retention (g = .52) and transfer (g = .31). Prior knowledge didn't change the effect. Schneider et al. 2018, Educ. Res. Review 23:1-24 [abstract]
- Signals improve memory for the content they point to. Lorch 1989, doi:10.1007/BF01320135 [abstract]

## Cut the process story; cut what the reader already has

- Interesting but irrelevant details hurt retention and transfer. Rey 2012, Educ. Res. Review 7(3):216-237 [abstract]. One meta-analysis reports retention g = −.37. Sundararajan & Adesope 2020, doi:10.1007/s10648-020-09522-4 [secondhand, via PMC8442593]
- These details do the most harm when they come first. Harp & Mayer 1998, J. Educ. Psych. 90(3):414-434 [abstract]
- A short captioned summary did as well as or better than the full 600-word text, and adding text to the summary made it less effective. Mayer et al. 1996, doi:10.1037/0022-0663.88.1.64 [abstract]
- Clinicians took 21.8% longer to read AI-drafted replies and saved no time on replying. The replies were 17.9% longer. Tai-Seale et al. 2024, doi:10.1001/jamanetworkopen.2024.6565 [paper]. Clinicians complained the drafts were too long. Garcia et al. 2024, doi:10.1001/jamanetworkopen.2024.3201 [paper]
- With an LLM reviewer, PR closure time went from 5h52m to 8h20m, and developers reported irrelevant comments. Cihan et al. 2025, arXiv:2412.18531 [abstract]

## Fit the depth to the reader

- Guidance that helps novices can hurt experts (the expertise reversal effect). Kalyuga et al. 2003, doi:10.1207/S15326985EP3801_4 [abstract]
- Readers who know little about a topic learn more from highly coherent text. Readers who know a lot sometimes learn more from sparse text. McNamara et al. 1996, doi:10.1207/s1532690xci1401_1 [abstract]

## Put evidence next to the claim

- Placing related information together in space or time helps, most of all with complex material. Ginns 2006, Learning and Instruction 16(6):511-525 [abstract]

## Make claims checkable, and state real uncertainty

- Explanations raised acceptance of AI recommendations whether the AI was right or wrong. Bansal et al. 2021, CHI, doi:10.1145/3411764.3445717 [abstract]
- People over-rely on AI when checking its output is costly. Harder-to-read explanations increased over-reliance. Vasconcelos et al. 2023, arXiv:2212.06823 [abstract]
- Longer LLM explanations raised user confidence without improving accuracy. Steyvers et al. 2025, Nat. Mach. Intell., doi:10.1038/s42256-024-00976-7 [abstract]
- Citing sources and pointing out inconsistencies reduced reliance on wrong LLM answers. Kim et al. 2025, CHI, doi:10.1145/3706598.3714020 [abstract]

## Name what you left out

- In LLM-written clinical notes, 3.45% of transcript sentences were omitted and 1.47% of note sentences were hallucinated. The two rates use different denominators. No study has tested whether flagging omissions helps readers, so this rule is a safeguard rather than a proven technique. Asgari et al. 2025, npj Digit Med 8:274 [paper]

## Choose the format by the shape of the content

- Fact boxes in table form beat text on comprehension, 79.6% vs 69.7% (d = .39, N = 2,305). Brick et al. 2020, doi:10.1098/rsos.190876 [paper]
- Bulleted lists improve recall of the listed items but reduce recall of the surrounding text. Jansen 2014, Information Design Journal 21(2) [abstract]

## Write plain sentences, even for experts

- Center-embedding, jargon, and passives made legal text harder to recall and understand, including for experienced readers. The difficulty came from the writing, not from the legal concepts. Martínez, Mollica & Gibson 2022, Cognition, doi:10.1016/j.cognition.2022.105070 [abstract]
- Classic readability formulas predict comprehension worse than newer language-model measures. Crossley et al. 2017, doi:10.1080/0163853X.2017.1296264 [abstract]

## Software engineering context

- Understanding the change is a reviewer's main task, and tools don't support it well. Bacchelli & Bird 2013, ICSE [paper]
- Reviewers rate a change as reviewable based on its description, its size, and a coherent commit history. Ram et al. 2018, FSE, doi:10.1145/3236024.3236080 [paper]
- Developers scan documentation for one specific item rather than reading it through. Meng et al. 2019, doi:10.1145/3274995.3274999 [paper]
- PRs with Copilot-drafted descriptions, which developers often edited, were reviewed 19.3 hours faster on average and had 1.57 times the odds of merging. Xiao et al. 2024, FSE, arXiv:2402.08967 [paper]

## Reading-time labels

- No peer-reviewed study of "X min read" labels was found. The closest research is on progress indicators in web surveys. There, an accurate constant indicator did not reduce drop-off, and early discouraging feedback increased it. Villar, Callegaro & Yang 2013, doi:10.1177/0894439313497468 [abstract]; Conrad et al. 2010, Interact. Comput. 22(5) [paper]

## Known gaps

- No study gives a correct length for a PR description, review report, or chat reply. The reading-time thresholds in `SKILL.md` are judgment calls, not findings.
- The limit of about four findings is an extrapolation from working-memory research and hasn't been tested on documents.
- No study has measured comprehension of LLM-written reports or reviews against their length.
