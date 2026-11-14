# Book Skills

47 agent skills, one per book. Each skill is a compact distillation of a single book, written so an agent can apply that book's system to the situation in front of it, in the author's own terms.

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

Grouped by topic: Conversation (6), Mind and play (8), Thinking (5), Design and making (8), Companies (5), Marketing (5), Public opinion (3), Presenting and teaching (3), Writing (4). The name in the first column is the folder and the value for `--skill`.

| Skill | Book | Topic | What it does |
|---|---|---|---|
| [`difficult-conversations`](difficult-conversations/) | *Difficult Conversations*<br>Douglas Stone, Bruce Patton and Sheila Heen | Conversation | Prepares, conducts or debriefs a hard conversation by separating it into the Three Conversations (What Happened?, Feelings, Identity) and moving to a learning conversation. |
| [`supercommunicators`](supercommunicators/) | *Supercommunicators*<br>Charles Duhigg | Conversation | Works out which of three conversations is happening (What's This Really About?, How Do We Feel?, Who Are We?) and matches it, with looping for understanding and deep questions. |
| [`magic-words`](magic-words/) | *Magic Words*<br>Jonah Berger | Conversation | Chooses the exact words of a request, pitch, email or reply using Berger's six types of magic words, each with its mechanism and the condition under which it flips. |
| [`games-people-play`](games-people-play/) | *Games People Play*<br>Eric Berne | Conversation | Applies transactional analysis to a recurring exchange: ego states, transactions, strokes and a six-step game analysis, with every game in Berne's thesaurus and its antithesis. |
| [`influencer`](influencer/) | *Influencer: The New Science of Leading Change*<br>Joseph Grenny, Kerry Patterson, David Maxfield, Ron McMillan and Al Switzler | Conversation | Leads behavior change in an organization, a community or oneself: find the vital behaviors and engage all six sources of influence. |
| [`chairs-are-where-the-people-go`](chairs-are-where-the-people-go/) | *The Chairs Are Where the People Go*<br>Misha Glouberman with Sheila Heti | Conversation | Gets groups of people to do things together: hosting shows, classes, parties and conferences, running charades and improv games, and settling neighborhood disputes. |
| [`flow`](flow/) | *Flow: The Psychology of Optimal Experience*<br>Mihaly Csikszentmihalyi | Mind and play | Makes a task, a job, a relationship or free time absorbing by working with the eight elements of flow and the balance of challenges and skills. |
| [`how-emotions-are-made`](how-emotions-are-made/) | *How Emotions Are Made*<br>Lisa Feldman Barrett | Mind and play | Reasons about emotion with the theory of constructed emotion: prediction, interoception, the body budget, affect and emotion concepts. |
| [`unlocking-the-emotional-brain`](unlocking-the-emotional-brain/) | *Unlocking the Emotional Brain*<br>Bruce Ecker, Robin Ticic and Laurel Hulley | Mind and play | Ends a symptom instead of managing it with the therapeutic reconsolidation process: find the emotional learning behind it, find knowledge that contradicts it, and guide the juxtaposition experience. |
| [`modern-wisdom-ancient-roots`](modern-wisdom-ancient-roots/) | *Modern Wisdom, Ancient Roots*<br>Srikumar Rao | Mind and play | Works on a stuck job, anger, worry or a setback by treating mental models and mental chatter as the cause, with Rao's practices for becoming the witness and investing in the process. |
| [`magic-of-thinking-big`](magic-of-thinking-big/) | *The Magic of Thinking Big*<br>David J. Schwartz | Mind and play | Raises the size of someone's thinking where excuses, fear or procrastination hold them back: cure excusitis, let action cure fear, and build a ten-year plan. |
| [`actionable-gamification`](actionable-gamification/) | *Actionable Gamification*<br>Yu-kai Chou | Mind and play | Audits or designs motivation in a product, workplace or habit system with the Octalysis Framework and its 8 Core Drives. |
| [`games-agency-as-art`](games-agency-as-art/) | *Games: Agency as Art*<br>C. Thi Nguyen | Mind and play | Treats games as the art of agency: design or critique goals and scoring, explain why people play, and diagnose value capture by metrics and gamification. |
| [`kinky-nlp`](kinky-nlp/) | *Kinky NLP*<br>sleepingirl | Mind and play | Applies neuro-linguistic programming to erotic hypnosis between consenting partners: patter, inductions, triggers, the meta model and the Milton model, and the book's consent models. |
| [`beginning-of-infinity`](beginning-of-infinity/) | *The Beginning of Infinity*<br>David Deutsch | Thinking | Judges explanations, forecasts, institutions and arguments by Deutsch's standard of the good explanation: hard to vary, with reach, improved by conjecture and criticism. |
| [`great-mental-models`](great-mental-models/) | *The Great Mental Models, volumes 1 to 4*<br>Shane Parrish and Rhiannon Beaubien, with Rosie Leizrowice on volume 3 | Thinking | Looks at a decision, problem or argument through a latticework of mental models from eight disciplines, with each model's definition, moves, limits and cases across all four volumes. |
| [`computational-thinking`](computational-thinking/) | *Computational Thinking*<br>Peter J. Denning and Matti Tedre | Thinking | Judges what can and cannot be computed, designs large software systems, models natural processes, and weighs claims about AI and the limits of computing. |
| [`tempo`](tempo/) | *Tempo*<br>Venkatesh Rao | Thinking | Decides when to act, and reads or shifts the pace of a conversation, team or project, using Rao's four timing behaviors, momentum moves and deep stories. |
| [`be-slightly-evil`](be-slightly-evil/) | *Be Slightly Evil: A Playbook for Sociopaths*<br>Venkatesh Rao | Thinking | Handles office politics, rivals, negotiations and stalemates with partly adversarial tactics organized by Boyd's OODA loop. |
| [`design-of-design`](design-of-design/) | *The Design of Design*<br>Frederick P. Brooks, Jr. | Design and making | Guides the design of complex things toward conceptual integrity: name the Design Concept, write user and use models, budget the scarce resource, and keep one chief designer. |
| [`dream-machine`](dream-machine/) | *The Dream Machine*<br>M. Mitchell Waldrop, with three of J. C. R. Licklider's papers | Design and making | Carries Licklider's vision of man-computer symbiosis and the ARPA and PARC way of realizing it, from dividing work between people and machines to leading a research community. |
| [`ideas-that-created-the-future`](ideas-that-created-the-future/) | *Ideas That Created the Future: Classic Papers of Computer Science*<br>edited by Harry R. Lewis | Design and making | Answers from 46 founding papers of computer science, Aristotle to Shamir, in each paper's own terms, with the editor's account of what it led to. |
| [`write-useful-books`](write-useful-books/) | *Write Useful Books*<br>Rob Fitzpatrick | Design and making | Designs, tests and refines problem-solving nonfiction the way a product is built, around the DEEP criteria (Desirable, Effective, Engaging, Polished). |
| [`comic-toolbox`](comic-toolbox/) | *The Comic Toolbox*<br>John Vorhaus | Design and making | Writes and repairs comedy with Vorhaus's tools: the comic premise, the comic perspective, and the nine-step Comic Throughline. |
| [`point-and-line-to-plane`](point-and-line-to-plane/) | *Point and Line to Plane*<br>Wassily Kandinsky | Design and making | Analyzes or builds a composition from Kandinsky's basic elements (point, line, basic plane), their tensions and their inner sound. |
| [`creative-selection`](creative-selection/) | *Creative Selection*<br>Ken Kocienda | Design and making | Builds products the way Apple made Safari and the iPhone keyboard: a loop of demo, feedback and next demo, fed by seven essential elements. |
| [`insanely-simple`](insanely-simple/) | *Insanely Simple*<br>Ken Segall | Design and making | Applies Apple's obsession with Simplicity, enforced with the Simple Stick, through the book's ten elements, from Think Brutal to Think War. |
| [`zero-to-one`](zero-to-one/) | *Zero to One*<br>Peter Thiel with Blake Masters | Companies | Judges and builds companies that create new things: the contrarian question, creative monopoly, definite optimism, secrets, and the seven questions every business must answer. |
| [`high-growth-handbook`](high-growth-handbook/) | *High Growth Handbook*<br>Elad Gil | Companies | Answers the problems of scaling a startup from 10 to 10,000 people: the CEO's role, the board, executive hiring, re-orgs, late-stage financing and M&A. |
| [`how-to-make-a-few-billion-dollars`](how-to-make-a-few-billion-dollars/) | *How to Make a Few Billion Dollars*<br>Brad Jacobs | Companies | Builds a company at scale by Jacobs's playbook: get the big trend right, buy and integrate companies, hire outstanding people, and run electric meetings. |
| [`matchmakers`](matchmakers/) | *Matchmakers: The New Economics of Multisided Platforms*<br>David S. Evans and Richard Schmalensee | Companies | Analyzes, starts, prices or vets a multisided platform: the chicken-and-egg problem, critical mass, the money side and the subsidy side, and governance rules. |
| [`five-dysfunctions-of-a-team`](five-dysfunctions-of-a-team/) | *The Five Dysfunctions of a Team*<br>Patrick Lencioni | Companies | Diagnoses and rebuilds an underperforming team through Lencioni's pyramid, from absence of trust to inattention to results. |
| [`22-immutable-laws-of-marketing`](22-immutable-laws-of-marketing/) | *The 22 Immutable Laws of Marketing*<br>Al Ries and Jack Trout | Marketing | Plans, judges and repairs marketing strategy as a battle of perceptions, law by law, from leadership and category to hype and resources. |
| [`simple-marketing-for-smart-people`](simple-marketing-for-smart-people/) | *Simple Marketing for Smart People*<br>Billy Broas and Tiago Forte | Marketing | Markets a product, service or course by answering "What does my customer need to believe in order to buy?" and building those beliefs with educational content. |
| [`robert-collier-letter-book`](robert-collier-letter-book/) | *The Robert Collier Letter Book*<br>Robert Collier | Marketing | Writes sales letters, collection letters and fund appeals that bring back orders: find the bait, aim at the emotions, and build on the Six Essentials. |
| [`dotcom-secrets`](dotcom-secrets/) | *DotCom Secrets*<br>Russell Brunson | Marketing | Designs, builds and fixes sales funnels: the Secret Formula, the Value Ladder, the ten funnels page by page, and the script for each page. |
| [`expert-secrets`](expert-secrets/) | *Expert Secrets*<br>Russell Brunson | Marketing | Turns expertise into a movement and sells it one-to-many with story: the Epiphany Bridge script, the Stack Slide, and the Perfect Webinar slide by slide. |
| [`the-crowd`](the-crowd/) | *The Crowd: A Study of the Popular Mind*<br>Gustave Le Bon | Public opinion | Explains why a crowd, an electorate, a jury or an assembly behaves as it does, by Le Bon's law of the mental unity of crowds. |
| [`propaganda`](propaganda/) | *Propaganda*<br>Edward Bernays | Public opinion | Wins public acceptance for an enterprise, idea or cause the way a public relations counsel does: by creating circumstances that move group leaders and group custom. |
| [`edward-bernays-reader`](edward-bernays-reader/) | *The Edward Bernays Reader: From Propaganda to the Engineering of Consent*<br>Edward Bernays | Public opinion | Plans a public relations, political or morale campaign from Bernays's writings of 1923 to 1979: the engineering of consent and its eight principles. |
| [`presentation-secrets-of-steve-jobs`](presentation-secrets-of-steve-jobs/) | *The Presentation Secrets of Steve Jobs*<br>Carmine Gallo | Presenting and teaching | Builds, reviews and rehearses a presentation as a three-act production of eighteen scenes, each with its technique and Director's Notes. |
| [`bezos-blueprint`](bezos-blueprint/) | *The Bezos Blueprint*<br>Carmine Gallo | Presenting and teaching | Writes and presents the way Jeff Bezos taught Amazon to: simple words, the logline, the six-page narrative memo, and the PR/FAQ that works backwards from the customer. |
| [`how-to-teach-anything`](how-to-teach-anything/) | *How to Teach Anything*<br>Peter Hollins | Presenting and teaching | Plans and delivers teaching, tutoring or an explanation: draw the student a map, build from what they already know, and scaffold within cognitive load. |
| [`elements-of-style`](elements-of-style/) | *The Elements of Style*<br>William Strunk Jr. | Writing | Writes, revises and marks prose by Strunk's eighteen numbered rules from the 1918 edition, among them "Omit needless words" and "Use the active voice". |
| [`economical-writing`](economical-writing/) | *Economical Writing*<br>Deirdre Nansen McCloskey, with an appendix by Stephen T. Ziliak | Writing | Drafts and revises expository prose by McCloskey's thirty-five numbered rules, with her list of Bad Words and Ziliak's McZ# method for marking a draft. |
| [`make-your-writing-flow`](make-your-writing-flow/) | *Make Your Writing Flow*<br>Ryan Deane | Writing | Connects sentences and paragraphs with the transition that signals the relation the writer means, chosen from the book's 34 categories. |
| [`very-good-copy`](very-good-copy/) | *Very Good Copy*<br>Eddie Shleyner | Writing | Writes, edits and judges persuasive copy the way Shleyner's 207 micro-lessons teach it, from the 40/40/20 rule and the levels of awareness to editing and testing. |

## How each skill is built

| Part | What it holds |
|---|---|
| `SKILL.md` | What every use of the book needs: the core concepts, the book's procedure where it has one, and pointers to the rest. It is the only file loaded when the skill fires. |
| Sibling files | The depth: individual chapters, case studies, scripts and catalogs. The agent opens one when the situation calls for it. |

Each skill uses the book's own vocabulary and states its claims at the author's confidence, at the generality of the book. Each was distilled from the book's full text, and its quotations were checked against that text.

A skill gives an agent a book's working system. It does not replace reading the book.
