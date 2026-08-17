---
title: Texts queue
description: Books, papers, essays, blog posts to read. Entries with @-bibkeys are in Zotero; promote each to a `refs/<bibkey>.md` once read.
tags:
  - antilibrary
  - queue
---

Grouped by topic to mirror the [[concepts/_index|concepts taxonomy]]. Reading status is `unread` by default; only explicit annotations from Zotero are noted inline. The "To process" block lists items already in Zotero; "Without a bibkey yet" lists items still to triage; "Long-form essays" gathers URL-based reads.

## To process

### Psychotherapy, voice, dyadic process

The active research line. The prosodic-analysis initiative (foundations → dyadic synchrony → thymia line → computational context) is the curated reading order.

**Acoustic-feature foundations**

- @eyben2016 #acoustic-features #eGeMAPS #method — GeMAPS / eGeMAPS minimal feature set. Implementation cornerstone for openSMILE-based pipelines; defines the 88-parameter extended set used as the affective-computing lingua franca.
- @cummins2015 #speech-analysis #depression #review — Cummins et al.'s field-defining review of speech analysis for depression and suicide risk. Read first to orient.
- @baevski2020 #speech #self-supervised — wav2vec 2.0 for self-supervised speech representations; the alternative to hand-crafted features.

**Dyadic vocal synchrony in psychotherapy**

- @imel2014 #vocal-synchrony #F0 #dyadic — Imel et al.'s mean-F0 synchrony × empathy in motivational interviewing. r=.80 high-empathy vs r=.36 low-empathy. Foundational for the synchrony framing.
- @gaume2019 #vocal-synchrony #replication — Gaume et al.'s direct failure-to-replicate of @imel2014. Read together; methodological lessons.
- @ramseyer2011 #nonverbal-synchrony #dyadic — Ramseyer & Tschacher on body-movement synchrony predicting alliance and outcome. The non-vocal analogue.
- @sherer1980 #nonverbal — Sherer & Rogers, canonical early result that therapist nonverbal cues drive perceived empathy/warmth/skill independent of verbal content.

**thymia.ai line**

- @norbury2026 #vocal-biomarkers #depression #anxiety #thymia — Norbury et al. (Sci Reports). Multimodal Bayesian network over 30 135 speakers; ROC-AUC 0.84 / 0.83 from voice. Reading task = Aesop's *North Wind and the Sun* + free mood description.
- @fara2022 #vocal-biomarkers #bayesian #thymia — Fara et al. Bayesian-networks precursor to @norbury2026.
- @fara2022a #vocal-biomarkers #depression #thymia — Fara et al. at Interspeech 2022. Speech + n-Back; symptom-cluster-level analysis.

**Computational psychotherapy context**

- @miner2020 #precision-psychiatry #asr — ASR accuracy in therapy (transcript prerequisite to the prosodic layer).
- @goldberg2020 #alliance #method — Goldberg, Imel, Atkins on ML/NLP in psychotherapy with alliance as the worked example.
- @imel2015 #method — Imel, Steyvers, Atkins on computational psychotherapy research at scale (the framing paper).
- @cummins2019 #method — TIM tool, interpretable therapist-utterance annotation.
- @eberhardt2024 #nlp — Eberhardt et al. on sentiment-analysis validity in psychotherapy; explicit "combine with vocal cues via NOVA" — natural integration target.
- @lin2022a #alliance — Working Alliance Transformer.
- @lin2024 #alliance — COMPASS, the follow-on framework.
- @ryu2023 #alliance — First-person pronouns + non-fluency as alliance markers.
- @buchholz2017 #conversation-analysis — Buchholz & Kächele on turn-taking and CA in therapy.
- @rogers1942 #history — Rogers, on electrically recorded interviews. Historical depth for the recorded-session research tradition.

### Surveillance, technology, power

- @snowden2019 — *Permanent Record*.
- @zuboff2018a (skimmed, 1 annotation) — *The Age of Surveillance Capitalism* (English).
- @eubanks2018 (skimmed, 1 annotation) #algorithms #inequality #politics — *Automating Inequality*.
- @black2012 (skimmed, 3 annotations) #nazi #ibm #ma #state-corp-crime — *IBM and the Holocaust*.
- @williams2018 #free-will — *Stand Out of Our Light*. (Also relevant under attention/workflow.)
- @bogard1996 #simulation — *The Simulation of Surveillance*.
- @bollmer2019 #networks — *Inhuman Networks: Social Media and the Archaeology of Connection*.
- @burke2015 #ma #state-corp-crime — State-corporate crime / NSA.
- @chandler2019 #politics #philosophy — *Digital Objects, Digital Subjects*.
- @demontjoye2013 — Unique-in-the-crowd mobility re-identification.
- @finley2014 #state-corp-crime — *Digital Blackwater* / NSA contractors.
- @froomkin2014 #privacy-pollution — Mass surveillance and privacy as pollution.
- @gadotti2019 #cryptography — Diffix sticky noise / re-identification.
- @harding2018 #religion — Speck and beam, critique adjacent to Lyon.
- @levine2018 — *Surveillance Valley*.
- @lyon2018 #religion — *The Culture of Surveillance*.
- @mann2003 — Sousveillance / wearable computing.
- @mcquillan2015 #algorithms — Algorithmic states of exception.
- @medrano2015 — The dilemma of surveillance.
- @morente2019 — Gary T. Marx interview.
- @muhlhoff2019 #ai — Human-aided AI / media sociology.
- @rocher2019 #cryptography #anonymisation — Re-identifications with generative models.
- @vandervlist2017 #geography — Counter-mapping surveillance.
- @eggers2013 #fiction — *The Circle*. (Cross-listed under fiction.)

### Cognition, epistemology, method

- @pearl2018 #causality #method — *The Book of Why*.
- @postman2005 #tv — *Amusing Ourselves to Death*.
- @oreskes2010 #disinformation — *Merchants of Doubt*.
- @tarnas2010 #history #philosophy — *The Passion of the Western Mind*.
- @andrejevic2013 #attention — *InfoGlut*.
- @baudrillard1995 #simulation — *Simulacra and Simulation*.
- @fairfield2017 #politics #method — Bayesian process tracing.

### Economics, finance, political economy

- @fisher2009 #philosophy — *Capitalist Realism*.
- @kuran1997 #preference-falsification — *Private Truths, Public Lies*.
- @taibbi2010 #finance — *Griftopia*.
- @zuckerman2019 #finance — *The Man Who Solved the Market*.

### Meta-crisis, existential risk

- @bostrom2014 #ai #philosophy — *Superintelligence*.
- @ord2020 #fhi — *The Precipice*.
- @lovelock2019 #intelligence — *Novacene*.

### Programming, computing, AI

- @isaacson2014 #history — *The Innovators*.
- @rid2016 #cybernetics — *Rise of the Machines*.
- @sejnowski2018 #ai #ml — *The Deep Learning Revolution*.
- @preskill2018 #physics #quantum — NISQ / quantum computing.

### Pharmacology, psychedelics

- @grof2006 #psychoanalysis — *When the Impossible Happens*.
- @lee1994 #lsd #history — *Acid Dreams*.
- @feustel2015 #lsd #cybernetics — LSD and cybernetics.

### Workflows, productivity, social skills

- @newport2012 — *So Good They Can't Ignore You*.
- @newport2016 — *Deep Work*.
- @newport2019 — *Digital Minimalism*.
- @young2019 #meta-learning — *Ultralearning*.
- @cabane2012 #charisma — *The Charisma Myth*.
- @manson2011 #seduction — Manson on attraction.
- @greene2003 #seduction — *The Art of Seduction*.
- @kerner2004 #sex — *She Comes First*.
- @easton2017 #polyamory — *The Ethical Slut*.
- @jeffers2007 #fear — *Feel the Fear and Do It Anyway*.
- @gazipura2013 #fear — *The Solution to Social Anxiety*.

### Fiction, literature

- @knausgard2013 #autobiography — Knausgard, vol. 1 (*Sterben*).
- @knausgard2018 #autobiography — Knausgard, vol. 6 (*Kämpfen*).
- @lem1984 — Lem, *His Master's Voice*.
- @lem1989 — Lem, *Return from the Stars*.
- @stephenson1999 #linux — *In the Beginning Was the Command Line*.
- @stephenson1999a #cryptography — *Cryptonomicon*.
- @stephenson2000 — *Snow Crash*.
- @stephenson2002 — *Interface*.
- @stephenson2011 — *Reamde*.
- @thompson1992 #journalism — Hunter S. Thompson, *Fear and Loathing in Elko*.

### Body, biology, math, miscellany

- @sapolsky2017 #biology #neuroscience #free-will — *Behave*.
- @walker2017 #sleep — *Why We Sleep*.
- @montgomery2015 #animals — *The Soul of an Octopus*.
- @emmerich2016 #keto #nutrition — 30-day keto cleanse.
- @acheson2018 #mathematics — *The Calculus Story*.
- @strogatz2019 #mathematics #calculus — *Infinite Powers*.

## Without a bibkey yet

Add to Zotero (BBT key) when promoting to a ref note.

### Psychotherapy, parts-work

Recommended in an HN thread as books framing the psyche as a system of parts or sub-selves, in the same family of thought as [[internal-family-systems|IFS]]:

- *Three Pillars of Zen* — Philip Kapleau
- Ken Wilber — integral writings
- *Introduction to NLP* (esp. chapter V on the Meta Model)
- *Structure of Magic vol. II* — communication, incongruity
- *Mind and Nature* — Gregory Bateson (also: epistemology, cybernetics)
- *Embracing Our Selves* — Hal & Sidra Stone. **Voice Dialogue** method; close kin to IFS without the therapeutic-modality packaging.
- *I Don't Want to Talk About It* — Terrence Real (male depression / relational therapy)
- *Das Gehirn — ein Beziehungsorgan* — Thomas Fuchs
- *Sexuality Beyond Consent* — Avgi Saketopoulou

### Surveillance, institutions, power

- *The Brass Check* — Upton Sinclair
- *Influencer: Die Ideologie der Werbekörper* — Ole Nymoen & Wolfgang M. Schmitt

### Meta-crisis, civilizational

- *Sapiens* / *Eine kurze Geschichte der Menschheit* — Yuval Noah Harari
- *How the World Really Works* — Vaclav Smil
- *Recapture the Rapture* — Jamie Wheal
- *World as Lover, World as Self* — Joanna Macy
- *Against the Grain* — James C. Scott
- *Revolution für das Leben* — Eva von Redecker
- *Métamorphoses* — Emanuele Coccia
- *Le Deuxième Sexe* / *Das andere Geschlecht* — Simone de Beauvoir

### Economics, finance

- *The Dawn of Everything* — David Graeber & David Wengrow
- *Smarter Investing* — Tim Hale

### Pharmacology, psychedelics

- *The Electric Kool-Aid Acid Test* — Tom Wolfe
- *Neuropsychedelia* — Nicolas Langlitz
- *Sacred Knowledge: Psychedelics and Religious Experiences* — William A. Richards
- *Psychonauts* — Mike Jay
- *Realms of the Human Unconscious* / *LSD Psychotherapy* — Stanislav Grof
- *Cosmic Trigger* — Robert Anton Wilson (and adjacent)

### Programming, computing, AI

- *Working in Public: The Making and Maintenance of Open Source Software* — Nadia Eghbal
- *Statistical Machine Learning* — Lindholm, Wahlström, Lindsten, Schön ([smlbook.org](http://smlbook.org/))
- *Deep Learning: Foundations and Concepts* — Christopher Bishop ([bishopbook.com](https://www.bishopbook.com/))
- *Zero to Production in Rust* — Luca Palmieri ([zero2prod.com](https://www.zero2prod.com/))

### Workflows, productivity, social skills

- *Rethinking Positive Thinking* — Gabriele Oettingen (WOOP method)
- *The Artist's Way* — Julia Cameron
- *Das Ende der Monogamie* — Friedemann Karig
- *Meditations* — Marcus Aurelius (Gregory Hays translation)

### Fiction, literature

- *Voyage au bout de la nuit* — Louis-Ferdinand Céline
- *The Overstory* — Richard Powers
- *Life and Fate* — Vasily Grossman
- *Say Nothing* — Patrick Radden Keefe
- *Vernichten* / *Anéantir* — Michel Houellebecq
- *The Maniac* — Benjamín Labatut
- *Faserland* — Christian Kracht
- *Anatomie eines Abschieds* — Franka Potente (autobiography)
- *Panikherz* — Benjamin von Stuckrad-Barre (autobiography)

### Body, biology, math, miscellany

- *Entangled Life* / *Verwobenes Leben* — Merlin Sheldrake
- *The Image: A Guide to Pseudo-Events in America* — Daniel Boorstin
- *The Emperor of Scent* — Chandler Burr
- *The Flavor Bible* — Karen Page & Andrew Dornenburg
- *Heraclitean Fire* — Erwin Chargaff
- *Die sieben Geheimnisse guten Sterbens*
- *The World Order Reset* — N.S. Lyons (essay, *The Upheaval*)
- *Against Identity* — Leon Wieseltier (essay)

## Long-form essays / blog posts

URL-based reads — substantive enough to warrant a focused read rather than skim.

### Surveillance, technology, power

- *AI and Mass Spying* — Bruce Schneier ([schneier.com](https://www.schneier.com/blog/archives/2023/12/ai-and-mass-spying.html))
- *The Pentagon's Silicon Valley Problem* — Andrew Cockburn, *Harper's* ([harpers.org](https://harpers.org/archive/2024/03/the-pentagons-silicon-valley-problem-andrew-cockburn/))
- *Inside Mark Zuckerberg's Hawaii Compound* — *Wired* ([archived](https://archive.vn/2023.12.14-112402/https://www.wired.com/story/mark-zuckerberg-inside-hawaii-compound/))
- *Computer Security Is a Political Struggle* — Cybershow ([cybershow.uk](https://cybershow.uk/blog/posts/computer-security-is-a-political-struggle/))
- *The Reality of Dating Apps* — Paul ([blog.luap.info](https://blog.luap.info/the-reality-of-dating-apps.html))

### Meta-crisis, civilizational

- *Meta-Crisis 101* / *Meta-Crisis Meta-Resource* — Sloww ([sloww.co](https://www.sloww.co/meta-crisis-101/))
- *The End Is Nigh, and Here's Why* — Adam Mastroianni, Experimental History ([experimental-history.com](https://www.experimental-history.com/p/the-end-is-nigh-and-heres-why))
- *Base Rates of Catastrophes* — Jacob Steinhardt, Bounded Regret ([bounded-regret.ghost.io](https://bounded-regret.ghost.io/base-rates-of-catastrophes/))
- *Peak Population Projections* — Tom Murphy, Do The Math ([dothemath.ucsd.edu](https://dothemath.ucsd.edu/2024/06/peak-population-projections/))
- *Civilization Emerging — Reading List* — Daniel Schmachtenberger ([civilizationemerging.com](https://civilizationemerging.com/resources/books/))

### Cognition, epistemology

- *Living in a Lucid Dream* — Noema Magazine ([noemamag.com](https://www.noemamag.com/living-in-a-lucid-dream))
- *What Are Dreams For?* — The New Yorker ([newyorker.com](https://www.newyorker.com/science/elements/what-are-dreams-for))
- *Out of Your Head* — Nautilus ([nautil.us](https://nautil.us/out-of-your-head-791745/))
- *Models: A Summary* — Ozy Brennan ([thingofthings.wordpress.com](https://thingofthings.wordpress.com/2018/05/25/models-a-summary/))
- *The Real Lesson of 'The Truman Show'* — The Atlantic ([theatlantic.com](https://www.theatlantic.com/culture/archive/2023/06/the-truman-show-25-years-later/674456/))
- *The Realism of Our Times* (KSR on how science fiction works) — Public Books ([publicbooks.org](https://www.publicbooks.org/the-realism-of-our-times-kim-stanley-robinson-on-how-science-fiction-works/))

### Pharmacology, psychedelics

- *Why Scientists Need to Get High* — Nautilus ([nautil.us](https://nautil.us/why-scientists-need-to-get-high-305830/))
- *What Can Psychedelic Science Teach Psychiatry About Psychosis* — Aeon ([aeon.co](https://aeon.co/essays/what-can-psychedelic-science-teach-psychiatry-about-psychosis))

### Programming, computing, AI

- *Spaced Repetition* — Gwern ([gwern.net](https://gwern.net/spaced-repetition))
- *Recording and Processing Spoken Word* — Laurence Tratt ([tratt.net](https://tratt.net/laurie/blog/2024/recording_and_processing_spoken_word.html))
- *Database Fundamentals* — Tom Tonti ([tontinton.com](https://tontinton.com/posts/database-fundementals/))
- *A Critical Look at MCP* — Raz ([raz.sh](https://raz.sh/blog/2025-05-02_a_critical_look_at_mcp))
- *OpenAI Codex Review* — Zack Proser ([zackproser.com](https://zackproser.com/blog/openai-codex-review))
- *Six Principles for Production AI Agents* — app.build ([app.build/blog](https://www.app.build/blog/six-principles-production-ai-agents))
- *An Interactive Guide to the Fourier Transform* — Better Explained ([betterexplained.com](https://betterexplained.com/articles/an-interactive-guide-to-the-fourier-transform/))

### Economics, finance

- *Bitcoin Network Health* — Lyn Alden ([lynalden.com](https://www.lynalden.com/bitcoin-network-health/))

### Workflows, productivity

- *How to Beat Procrastination* — Tim Urban, Wait But Why ([waitbutwhy.com](https://waitbutwhy.com/2013/11/how-to-beat-procrastination.html))
- *16 Life-Learnings from 16 Years* — The Marginalian ([themarginalian.org](https://www.themarginalian.org/2022/10/23/16-learnings/))
- *My Lifetime Reading Plan* — Ted Gioia, The Honest Broker ([honest-broker.com](https://www.honest-broker.com/p/my-lifetime-reading-plan))
- *The Notetaking Cold War* — Every / Superorganizers ([every.to](https://every.to/superorganizers/the-notetaking-cold-war-591898))

## Processed

```dataview
TABLE WITHOUT ID file.link AS "Note", authored_on AS "Read"
FROM "21.02_Zettel/refs"
WHERE medium = "reading"
SORT authored_on DESC
```
