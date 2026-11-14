# Book Skills

Agent skills, one per book. Each skill is a compact distillation of a single book, written so an agent can apply that book's system to the situation in front of it, in the author's own terms.

## Install

With the [skills CLI](https://skills.sh):

```sh
npx skills add mpsuesser/book-skills                 # pick from all 17
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

**[`actionable-gamification`](actionable-gamification/)** · *Actionable Gamification* by Yu-kai Chou<br>
Audits or designs motivation in a product, workplace or habit system with the Octalysis Framework: the 8 Core Drives, their Game Techniques, White Hat and Black Hat motivation, and the four Experience Phases. Includes the Octalysis Audit and the Strategy Dashboard for designing from scratch.

**[`games-agency-as-art`](games-agency-as-art/)** · *Games: Agency as Art* by C. Thi Nguyen<br>
Treats games as the art of agency, in which designers shape the goals, abilities and environments that players take on as temporary agencies. Use it to design or critique a game's goals and scoring, explain why people play, and diagnose value capture by metrics, rankings and gamification.

### Thinking and deciding

**[`beginning-of-infinity`](beginning-of-infinity/)** · *The Beginning of Infinity* by David Deutsch<br>
Judges explanations, forecasts, institutions and arguments by Deutsch's standard of the good explanation: hard to vary, with reach, improved by conjecture and criticism. Covers the principle of optimism, prediction versus prophecy, Popper's criterion, universality, memes, and the failure modes Deutsch names.

**[`tempo`](tempo/)** · *Tempo* by Venkatesh Rao<br>
Decides when to act, and reads or shifts the pace of a conversation, team or project, using Rao's four timing behaviors (merging, going with the flow, pace-setting, disruption), momentum moves and deep stories. Also covers mental models, archetypes, and reading workspaces and organizations as externalized mental models.

### Designing and making

**[`design-of-design`](design-of-design/)** · *The Design of Design* by Frederick P. Brooks, Jr.<br>
Guides the design of complex things (software, computer architectures, buildings, organizations) toward conceptual integrity: name the Design Concept, write down user and use models, budget the scarce resource, and keep one chief designer. Includes a symptom-to-remedy table and Brooks's case studies.

**[`dream-machine`](dream-machine/)** · *The Dream Machine* by M. Mitchell Waldrop, with three of J. C. R. Licklider's papers<br>
Carries Licklider's vision of man-computer symbiosis and the ARPA and PARC way of realizing it. Use it to divide work between people and machines, lead a research community, build open networks and standards, or move research into the market.

**[`write-useful-books`](write-useful-books/)** · *Write Useful Books* by Rob Fitzpatrick<br>
Designs, tests and refines problem-solving nonfiction the way a product is built: scope a clear promise, test it in reader conversations, iterate with beta readers, and seed the first readers so that recommendations carry the book. Built around the book's DEEP criteria (Desirable, Effective, Engaging, Polished).

**[`comic-toolbox`](comic-toolbox/)** · *The Comic Toolbox* by John Vorhaus<br>
Writes and repairs comedy with Vorhaus's tools: comedy as truth and pain, the comic premise as a gap between two realities, the comic perspective that drives a character, and the nine-step Comic Throughline for story. Includes a diagnostic for why a joke or scene isn't funny.

**[`point-and-line-to-plane`](point-and-line-to-plane/)** · *Point and Line to Plane* by Wassily Kandinsky<br>
Analyzes or builds a composition from Kandinsky's basic elements (point, line, basic plane), their tensions and their inner sound. Covers placement on the picture plane, the character of lines and angles, their relation to colour, and translating music, dance and natural forms into point and line.

## How each skill is built

- **`SKILL.md` holds what every use of the book needs:** the core concepts, the book's procedure where it has one, and pointers to the rest. It is the only file loaded when the skill fires.
- **Sibling files hold the depth:** the detail of individual chapters, case studies, scripts and catalogs. The agent opens one when the situation calls for it.
- **The author's terms and claims are kept.** Each skill uses the book's own vocabulary and states its claims at the author's confidence, at the generality of the book.
- **Each was distilled from the book's full text,** and its quotations were checked against that text.

A skill gives an agent a book's working system. It does not replace reading the book.
