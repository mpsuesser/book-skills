# Book Skills

Agent skills, one per book. Each skill is a compact distillation of a single book, written so an agent can apply that book's system to the situation in front of it, in the author's own terms.

## Install

With the [skills CLI](https://skills.sh):

```sh
npx skills add mpsuesser/book-skills                 # pick from all 47
npx skills add mpsuesser/book-skills --skill tempo   # install one
npx skills add mpsuesser/book-skills --list          # list without installing
```

Add `-g` to install at user level instead of into the current project. You can also copy any folder into your agent's skills directory (for Claude Code, `~/.claude/skills/`).

The skills are model-invoked: each description names the situations and terms that should bring the book to mind, so the agent loads the skill when a conversation calls for it.

## The skills

### Conversation and groups

**[`difficult-conversations`](difficult-conversations/)** · *Difficult Conversations* by Douglas Stone, Bruce Patton and Sheila Heen<br>
Prepares, conducts or debriefs any conversation someone finds hard, by separating it into the Three Conversations (What Happened?, Feelings, Identity) and moving from a battle of messages to a learning conversation. Carries the book's five-step checklist, the Third Story opening, and its scripts for hard cases.

**[`supercommunicators`](supercommunicators/)** · *Supercommunicators* by Charles Duhigg<br>
Works out which of three conversations is happening (What's This Really About?, How Do We Feel?, Who Are We?) and matches it, following the four rules of a learning conversation. Includes looping for understanding, deep questions, and a table for diagnosing a conversation that failed.

**[`magic-words`](magic-words/)** · *Magic Words* by Jonah Berger<br>
Chooses the exact words of a request, pitch, email or reply using Berger's six types of magic words, each with its mechanism, the numbers behind it, and the condition under which it flips. Also covers what a text's language reveals about its writer.

**[`games-people-play`](games-people-play/)** · *Games People Play* by Eric Berne<br>
Applies transactional analysis to a recurring exchange: ego states (Parent, Adult, Child), transactions, strokes and time structuring, then a six-step game analysis. Indexes every game in Berne's thesaurus with its payoff and antithesis.

**[`influencer`](influencer/)** · *Influencer: The New Science of Leading Change* by Joseph Grenny, Kerry Patterson, David Maxfield, Ron McMillan and Al Switzler<br>
Leads behavior change in an organization, a community or oneself: focus on a measurable result, find the two or three vital behaviors, and engage all six sources of influence (personal, social and structural; motivation and ability).

**[`chairs-are-where-the-people-go`](chairs-are-where-the-people-go/)** · *The Chairs Are Where the People Go* by Misha Glouberman with Sheila Heti<br>
Gets groups of people to do things together: hosting shows, classes, parties and conferences, running charades and improv games, and settling neighborhood disputes. Also holds Glouberman's answers to the personal questions the book takes up, from making friends in a new city to quitting smoking.

### Mind, motivation and play

**[`flow`](flow/)** · *Flow: The Psychology of Optimal Experience* by Mihaly Csikszentmihalyi<br>
Makes a task, a job, a relationship or free time absorbing by working with the eight elements of flow and the balance of challenges and skills. Extends to the autotelic personality, coping with adversity, and building a life theme.

**[`how-emotions-are-made`](how-emotions-are-made/)** · *How Emotions Are Made* by Lisa Feldman Barrett<br>
Reasons about emotion with the theory of constructed emotion: the brain predicts, and from interoception, the body budget, affect and emotion concepts it constructs instances of emotion. Applies it to handling one's own feelings, reading other people's, and weighing claims about emotion in faces, brains, law, illness and animals.

**[`unlocking-the-emotional-brain`](unlocking-the-emotional-brain/)** · *Unlocking the Emotional Brain* by Bruce Ecker, Robin Ticic and Laurel Hulley<br>
Ends a symptom rather than managing it by running the therapeutic reconsolidation process (A–B–C–1–2–3–V): find the emotional learning that makes the symptom necessary, find knowledge that contradicts it, and guide the juxtaposition experience that memory reconsolidation needs. Carries Coherence Therapy's techniques, the book's cases step by step, and its maps of AEDP, EFT, EMDR, IFS, IPNB, ISTDP, psychedelic-assisted therapy and Somatic Experiencing.

**[`modern-wisdom-ancient-roots`](modern-wisdom-ancient-roots/)** · *Modern Wisdom, Ancient Roots* by Srikumar Rao<br>
Works on a stuck job, a strained marriage, anger, worry or a setback by treating mental models and mental chatter as the cause of the problem. Carries Rao's practices: becoming the witness of your chatter, the if-then model, deliberate intent, "Who am I being?", and investing in the process, not the outcome.

**[`magic-of-thinking-big`](magic-of-thinking-big/)** · *The Magic of Thinking Big* by David J. Schwartz<br>
Raises the size of someone's thinking where excuses, fear, procrastination or a setback hold them back: cure excusitis, let action cure fear, use the big thinker's vocabulary, and build a ten-year plan. Also covers winning other people's support, leading, and salvaging something from every setback.

**[`actionable-gamification`](actionable-gamification/)** · *Actionable Gamification* by Yu-kai Chou<br>
Audits or designs motivation in a product, workplace or habit system with the Octalysis Framework: the 8 Core Drives, their Game Techniques, White Hat and Black Hat motivation, and the four Experience Phases. Includes the Octalysis Audit and the Strategy Dashboard for designing from scratch.

**[`games-agency-as-art`](games-agency-as-art/)** · *Games: Agency as Art* by C. Thi Nguyen<br>
Treats games as the art of agency, in which designers shape the goals, abilities and environments that players take on as temporary agencies. Use it to design or critique a game's goals and scoring, explain why people play, and diagnose value capture by metrics, rankings and gamification.

**[`kinky-nlp`](kinky-nlp/)** · *Kinky NLP* by sleepingirl<br>
Applies neuro-linguistic programming to erotic hypnosis between consenting partners: writing and critiquing patter, inductions, triggers and conditioning suggestions, and reading a partner's language. Covers the meta model, the Milton model language patterns, pacing and leading, submodalities, reframing, metaphor, and the book's consent models.

### Thinking and deciding

**[`beginning-of-infinity`](beginning-of-infinity/)** · *The Beginning of Infinity* by David Deutsch<br>
Judges explanations, forecasts, institutions and arguments by Deutsch's standard of the good explanation: hard to vary, with reach, improved by conjecture and criticism. Covers the principle of optimism, prediction versus prophecy, Popper's criterion, universality, memes, and the failure modes Deutsch names.

**[`great-mental-models`](great-mental-models/)** · *The Great Mental Models*, volumes 1 to 4, by Shane Parrish and Rhiannon Beaubien, with Rosie Leizrowice on volume 3<br>
Looks at a decision, problem or argument through a latticework of mental models drawn from general thinking, physics, chemistry, biology, systems, mathematics, economics and art. One skill covers all four volumes: a catalog of every model and Supporting Idea with the situations it fits, and for each model its definition, its moves and questions, the limits the authors name, and the cases that show it at work.

**[`computational-thinking`](computational-thinking/)** · *Computational Thinking* by Peter J. Denning and Matti Tedre<br>
Treats computational thinking as two skills: designing computations that get computers to do jobs, and interpreting the world as information processes. Use it to judge what can and cannot be computed, separate CT for beginners from CT for professionals, design large software systems and software that satisfies its users, model natural processes, and weigh claims about AI and the limits of computing.

**[`tempo`](tempo/)** · *Tempo* by Venkatesh Rao<br>
Decides when to act, and reads or shifts the pace of a conversation, team or project, using Rao's four timing behaviors (merging, going with the flow, pace-setting, disruption), momentum moves and deep stories. Also covers mental models, archetypes, and reading workspaces and organizations as externalized mental models.

**[`be-slightly-evil`](be-slightly-evil/)** · *Be Slightly Evil: A Playbook for Sociopaths* by Venkatesh Rao<br>
Handles office politics, rivals, negotiations and stalemates with partly adversarial tactics organized by Boyd's OODA loop. Covers felt and played status, cold-blooded listening, the hierarchy of deceptions, conflict without ego, damage control, and getting inside an opponent's tempo.

### Designing and making

**[`design-of-design`](design-of-design/)** · *The Design of Design* by Frederick P. Brooks, Jr.<br>
Guides the design of complex things (software, computer architectures, buildings, organizations) toward conceptual integrity: name the Design Concept, write down user and use models, budget the scarce resource, and keep one chief designer. Includes a symptom-to-remedy table and Brooks's case studies.

**[`dream-machine`](dream-machine/)** · *The Dream Machine* by M. Mitchell Waldrop, with three of J. C. R. Licklider's papers<br>
Carries Licklider's vision of man-computer symbiosis and the ARPA and PARC way of realizing it. Use it to divide work between people and machines, lead a research community, build open networks and standards, or move research into the market.

**[`ideas-that-created-the-future`](ideas-that-created-the-future/)** · *Ideas That Created the Future: Classic Papers of Computer Science*, edited by Harry R. Lewis<br>
Answers from 46 founding papers of computer science, Aristotle to Shamir, in each paper's own terms: its definitions and notation, its method and results, and the editor's account of what it led to. Use it to explain where a computing idea came from, trace how ideas connect paper by paper, or apply a classic construct such as Hamming codes, Hoare logic, the relational model or Shamir's threshold scheme.

**[`write-useful-books`](write-useful-books/)** · *Write Useful Books* by Rob Fitzpatrick<br>
Designs, tests and refines problem-solving nonfiction the way a product is built: scope a clear promise, test it in reader conversations, iterate with beta readers, and seed the first readers so that recommendations carry the book. Built around the book's DEEP criteria (Desirable, Effective, Engaging, Polished).

**[`comic-toolbox`](comic-toolbox/)** · *The Comic Toolbox* by John Vorhaus<br>
Writes and repairs comedy with Vorhaus's tools: comedy as truth and pain, the comic premise as a gap between two realities, the comic perspective that drives a character, and the nine-step Comic Throughline for story. Includes a diagnostic for why a joke or scene isn't funny.

**[`point-and-line-to-plane`](point-and-line-to-plane/)** · *Point and Line to Plane* by Wassily Kandinsky<br>
Analyzes or builds a composition from Kandinsky's basic elements (point, line, basic plane), their tensions and their inner sound. Covers placement on the picture plane, the character of lines and angles, their relation to colour, and translating music, dance and natural forms into point and line.

**[`creative-selection`](creative-selection/)** · *Creative Selection* by Ken Kocienda<br>
Builds products the way Apple made Safari and the iPhone keyboard: by creative selection, a loop of demo, feedback and next demo, fed by seven essential elements (inspiration, collaboration, craft, diligence, decisiveness, taste, empathy). Use it to plan a demo, run a review with a decider, judge taste in a design, and converge on a ship date.

**[`insanely-simple`](insanely-simple/)** · *Insanely Simple* by Ken Segall<br>
Applies Apple's obsession with Simplicity, enforced with the Simple Stick, through the book's ten elements (Think Brutal, Small, Minimal, Motion, Iconic, Phrasal, Casual, Human, Skeptic, War). Use it to shrink teams and approval chains, cut product lines and messages to one point, name products, present to executives, and fight Complexity when experts and process say no.

### Companies and teams

**[`zero-to-one`](zero-to-one/)** · *Zero to One* by Peter Thiel with Blake Masters<br>
Judges and builds companies that create new things: ask the contrarian question, escape competition through creative monopoly, plan as a definite optimist, and look for secrets. Covers the power law, founding teams and equity, culture, distribution, and the seven questions every business must answer.

**[`high-growth-handbook`](high-growth-handbook/)** · *High Growth Handbook* by Elad Gil<br>
Answers the problems of scaling a startup after product/market fit, from 10 to 10,000 people: the CEO's role, the board, hiring and firing executives, recruiting, re-orgs and culture, product management, late-stage financing, going public, and M&A. Includes the views of the operators and investors Gil interviews.

**[`how-to-make-a-few-billion-dollars`](how-to-make-a-few-billion-dollars/)** · *How to Make a Few Billion Dollars* by Brad Jacobs<br>
Builds a company at scale by Jacobs's playbook from United Waste, United Rentals and XPO: get the big trend right, buy and integrate companies, hire and pay for outstanding people, and run electric meetings. Also covers handling a crisis with radical acceptance and rearranging your brain to think huge.

**[`matchmakers`](matchmakers/)** · *Matchmakers: The New Economics of Multisided Platforms* by David S. Evans and Richard Schmalensee<br>
Analyzes, starts, prices or vets a business that connects two or more customer groups. Covers the chicken-and-egg problem and the strategies for reaching critical mass, price level and price structure (money side, subsidy side), design for thick markets, governance rules, ecosystems, and six questions that tell fizzle from sizzle.

**[`five-dysfunctions-of-a-team`](five-dysfunctions-of-a-team/)** · *The Five Dysfunctions of a Team* by Patrick Lencioni<br>
Diagnoses and rebuilds an underperforming team through Lencioni's pyramid: absence of trust, fear of conflict, lack of commitment, avoidance of accountability, inattention to results. Carries the team assessment, the exercises and the leader's role for each dysfunction, and Kathryn's methods from the DecisionTech fable.

### Marketing and selling

**[`22-immutable-laws-of-marketing`](22-immutable-laws-of-marketing/)** · *The 22 Immutable Laws of Marketing* by Al Ries and Jack Trout<br>
Plans, judges and repairs marketing strategy as a battle of perceptions, law by law, from leadership and category to hype and resources. Use it to pick the category to be first in, choose the word to own in the prospect's mind, compete from second or third place, and decide on a line extension.

**[`simple-marketing-for-smart-people`](simple-marketing-for-smart-people/)** · *Simple Marketing for Smart People* by Billy Broas and Tiago Forte<br>
Markets a product, service or course by answering one focusing question, "What does my customer need to believe in order to buy?", then building those beliefs with educational content. Carries Belief Building, the core messaging document, the chain of beliefs, the claim/proof model, and the Ladder of Importance for deciding what to work on.

**[`robert-collier-letter-book`](robert-collier-letter-book/)** · *The Robert Collier Letter Book* by Robert Collier<br>
Writes sales letters, mailings, collection letters and fund appeals that bring back orders, the way Collier did in mailings that sold over twenty million dollars of goods. Find the bait that ties the offer to the reader's mental conversation, aim at the emotions, and build on the Six Essentials, from the opening through the snapper to the close. Carries the six prime motives, word pictures, proof, supplying the impulse, premiums and hurry-ups, the damaged-set and favor letters, and his rules for lists and testing.

**[`dotcom-secrets`](dotcom-secrets/)** · *DotCom Secrets* by Russell Brunson<br>
Designs, builds and fixes sales funnels: find the dream customer with the Secret Formula, place each offer on the Value Ladder, and pick the funnel that fits its price. Carries the ten funnels page by page, the scripts for each page (headlines, sales letters, OTO videos, the Perfect Webinar, phone closes), the follow-up email sequences, and how to diagnose a funnel from its CPA and ACV.

**[`expert-secrets`](expert-secrets/)** · *Expert Secrets* by Russell Brunson<br>
Turns expertise into a movement (expert/guide, new opportunity, future-based cause) and sells it one-to-many with story. Carries the Epiphany Bridge script, the four core stories, the Stack Slide, and the Perfect Webinar slide by slide with all 16 mini closes, plus its Shortcut and 5-Minute versions and the weekly live webinar funnel.

### Crowds and public opinion

**[`the-crowd`](the-crowd/)** · *The Crowd: A Study of the Popular Mind* by Gustave Le Bon<br>
Explains why a crowd, an electorate, a jury or an assembly behaves as it does, by Le Bon's law of the mental unity of crowds: contagion, suggestibility and thinking in images. Covers the remote and immediate factors of opinion, the leader's means (affirmation, repetition, contagion, prestige), and fixed beliefs against changeable opinions.

**[`propaganda`](propaganda/)** · *Propaganda* by Edward Bernays<br>
Wins public acceptance for an enterprise, idea, product or cause the way Bernays's public relations counsel does: by creating circumstances and events that move group leaders and group custom, where a direct appeal argues at individuals. Covers the new propaganda, the invisible government, and its practice in business, politics, education, social service, art and science.

**[`edward-bernays-reader`](edward-bernays-reader/)** · *The Edward Bernays Reader: From Propaganda to the Engineering of Consent* by Edward Bernays<br>
Plans a public relations, political, fundraising or morale campaign from Bernays's writings of 1923 to 1979: the engineering of consent and its eight principles, publics and group leaders, the overt act, symbols, and themes and appeals. Also covers attitude polls, psychological warfare, and repairing an organization's standing with its publics.

### Presenting and teaching

**[`presentation-secrets-of-steve-jobs`](presentation-secrets-of-steve-jobs/)** · *The Presentation Secrets of Steve Jobs* by Carmine Gallo<br>
Builds, reviews and rehearses a presentation as a three-act production of eighteen scenes: create the story, deliver the experience, refine and rehearse. Carries each scene's technique and Director's Notes, from the Twitter-like headline, the rule of three and the antagonist to visually simple slides, dressed-up numbers, the holy shit moment and rehearsal, with patterns that pair what Jobs said with what each slide showed.

**[`bezos-blueprint`](bezos-blueprint/)** · *The Bezos Blueprint* by Carmine Gallo<br>
Writes and presents the way Jeff Bezos taught Amazon to: simple words, the logline, bottom line up front, the six-page narrative memo, and the PR/FAQ that works backwards from the customer. Carries the Gallo Method Message Map, the AMP model (Ability, Message, Practice), storytelling and metaphor, and the book's coaching drills.

**[`how-to-teach-anything`](how-to-teach-anything/)** · *How to Teach Anything* by Peter Hollins<br>
Plans and delivers teaching, tutoring, training or an explanation: see the landscape, draw the student a map, build from what they already know, and scaffold within cognitive load. Holds the five pedagogical approaches and a toolkit that runs from the Feynman technique and Bloom's taxonomy to Socratic questions, productive failure and feedback.

### Prose and copy

**[`elements-of-style`](elements-of-style/)** · *The Elements of Style* by William Strunk Jr.<br>
Writes, revises and marks prose by Strunk's eighteen numbered rules from the 1918 edition: eight Elementary Rules of Usage and ten Elementary Principles of Composition, among them "Omit needless words" and "Use the active voice". Also holds A Few Matters of Form, Words and Expressions Commonly Misused, and Words Commonly Misspelled.

**[`economical-writing`](economical-writing/)** · *Economical Writing* by Deirdre Nansen McCloskey, with an appendix by Stephen T. Ziliak<br>
Drafts and revises expository prose by McCloskey's thirty-five numbered rules, from the whole piece down to the paragraph, the sentence and the word. Includes her list of Bad Words and Ziliak's McZ# method, which marks each fault in a draft with the number of the rule it breaks.

**[`make-your-writing-flow`](make-your-writing-flow/)** · *Make Your Writing Flow* by Ryan Deane<br>
Connects sentences and paragraphs with the transition that signals the relation the writer means, chosen from the book's 34 categories of transitional words and phrases. Holds every transition by category with notes on how each is used, and a pass for revising a draft join by join.

**[`very-good-copy`](very-good-copy/)** · *Very Good Copy* by Eddie Shleyner<br>
Writes, edits and judges persuasive copy the way Shleyner's 207 micro-lessons teach it: diagnose with the 40/40/20 rule and the levels of awareness, then research, find the angle, structure, draft, edit and test. Reference files go deeper on headlines, storytelling, persuasion, editing, campaigns and positioning, the creative process, and a copywriter's practice and career.

## How each skill is built

- **`SKILL.md` holds what every use of the book needs:** the core concepts, the book's procedure where it has one, and pointers to the rest. It is the only file loaded when the skill fires.
- **Sibling files hold the depth:** the detail of individual chapters, case studies, scripts and catalogs. The agent opens one when the situation calls for it.
- **The author's terms and claims are kept.** Each skill uses the book's own vocabulary and states its claims at the author's confidence, at the generality of the book.
- **Each was distilled from the book's full text,** and its quotations were checked against that text.

A skill gives an agent a book's working system. It does not replace reading the book.
