# Team design, collaboration and telecollaboration

Since 1900, design has moved to teams, and the teams increasingly telecollaborate. Collaboration is not good in itself. "Most great works of the human mind have been made by one mind, or two working closely." The danger of team design is the loss of conceptual integrity. The challenge is to keep integrity while getting the real benefits of collaboration.

## Why teams, and what they cost

Teams are forced by two things:
- **Technological sophistication**, which requires specialization; "no naive technologies left."
- **Hurry to market.** A rule of thumb gives the first to market about 40% long-run share.

Collaboration's costs, under the motto "Many hands make *light* work—Often. But many hands make *more* work—Always":
- **Partitioning.** No design task partitions perfectly. Crisp interface definition is a lot of work, slighted at one's peril. Interfaces are interpreted continually. Gaps, inconsistencies and conflicts must be reconciled. Common elements and a common design style must be standardized. Integration is the ultimate test of interface consistency ("Cut to plan; bang to fit," in the shipyards).
- **Learning and teaching.** Work = *l* + *d* (learning plus doing) becomes at least *n l* + *d*. Someone with the vision must teach, and so is not designing.
- **Communication**, which must be structured.
- **Change control.** Each designer makes only changes that affect only their own part, or that have been negotiated with the designers of the affected parts. This costs a lot. Not having formal change control costs much more.

The pattern behind truly innovative products is physical isolation, small teams, intense concentration, and leadership by one mind. Examples:
- the Spitfire at Hursley House;
- the Skunk Works under Kelly Johnson;
- the IBM PC at Boca Raton;
- the CDC 6600, built by Seymour Cray's secluded team of 35 "including the janitor." Cray personally mastered everything from architecture to cooling, so he could make trades across domains.

## Getting conceptual integrity in a team

The product must be conceptually coherent to the single mind of the user. Achieving that with a team is a management feat.

- **Interdisciplinary negotiation among peers is the classic recipe for bloated products.** It is design by committee, "where none dare say 'No' to another's suggestion."
- **Empower a single system architect.** This is the most important single way to get conceptual integrity. The architect must:
  - be competent in the relevant technologies;
  - be experienced in the sort of system being designed;
  - have a clear vision of and for the system;
  - really *care* about its conceptual integrity.

  The architect is the agent, approver and advocate for the user and the other stakeholders. The real user is often not the purchaser; in military procurement, for instance, the purchaser is represented by marketers, engineers and manufacturers. "Only the architect represents the users."
- **One user-interface designer.** When the architecture needs a team, the problem recurses. The user interface must be tightly controlled by one mind: "If one architect can't master it, one user can't either." Marissa Mayer controlled Google's home page. The UI designer needs experience of use, listening skills and, above all, *taste*. Iverson said of APL: "It does what you expect it to do."
- **The counter-example: IBM's Future Series.** Its brilliant architects each presented their own parts. A listener asked, "Can you please let me talk to the architect who understands it all, so I can get an overview?" The answer: "There isn't one. No one person understands it all." The project collapsed of its own weight, with an 800-page user manual. Mitchell, the Spitfire's designer, warned a test pilot: "If anybody ever tells you anything about an aeroplane which is so bloody complicated you can't understand it, take it from me: it's all balls."

## When collaboration helps

- **Determining needs.** A small team studies an unmet need or an existing system better than one person can.
- **Establishing objectives.** Extra minds flush out the *implicit* objectives and constraints that stakeholders don't recognize. They work from what is said, how it is said and what is left unsaid, and from that build a first estimate of the utility function. Observe how users do the job today; videotape it and watch repeatedly. Extra minds ask different questions, notice things nobody said, form independent opinions and stimulate discussion.
- **Exploring radical alternatives.** Explore early, while no one is wedded to a solution. Concreteness draws out unspoken desiderata and constraints.
- **Brainstorming.** Osborn's rules: "Focus on quantity," "No criticism," "Encourage wild ideas," "Combine and improve ideas," "Sketch all of them where all can see." Note that a 2007 Sandia study found individuals produced as many ideas as the group, and ideas of significantly better quality (originality, feasibility, effectiveness).
- **Design competitions.** They work best when the known constraints and objectives are stated concretely and shared, and unnecessary constraints are cut out.
  - When the System/360's stack architecture proved poor for the low-end models after six months, Amdahl suggested a competition. About 13 teamlets of one to three people sketched designs against fixed rules and a deadline. The two best were surprisingly alike, and the result was consensus, morale and a good design.
  - Brunelleschi won the Florence dome by competition.
  - Competitions for organization designs are inherently political.
- **Product fights**, a drama in five acts:
  1. Two teams meet, conclude there is no real overlap, and both proceed.
  2. Reality appears, as a market forecast or a skeptical boss.
  3. Each team changes its design to cover all of the other's market.
  4. Each woos supporters.
  5. There is a shootout before an executive.

  The outcome is A, B, both or neither. Early action by a skeptical boss should shorten the fight, though sometimes a fight is the best way to explore two approaches.
- **Design review**, where collaboration is most valuable, even necessary. "Demand multidisciplinary group review." The review team should be much larger than the design team. Bring other designers, users or their surrogates, implementers, purchasers, manufacturers, maintainers, reliability experts, and safety and environmental watchdogs.
  - Each specialist first reviews the documents alone, with time, reflection and references.
  - Then the joint group review is imperative, because one specialist's concern triggers another's.
  - On a submarine design, a supply officer's worry set off the damage-control specialist, and a tooling expert's fix alarmed the acoustic expert.
  - An Electric Boat shipyard foreman replaced the engineer's 20-piece semicylindrical tank with a one-piece rolled cylinder, cut in half and roofed with a flat plate: "We submarine builders are good at rolling cylinders."
  - On an oil platform, a maintenance foreman asked for heavy-gauge steel on one unit, "where it goes, we'll never be able to paint it again."
- **Representations for review.** Use a common model: drawings, full-scale mock-ups, virtual environments, prototypes, architectural diagrams. Reviewers often need a richer variety of representations than the designers used. Review *documents*, not slides: vague bullets let each listener interpret them as they please and suppress embarrassing crucial details. Gerstner switched off the projector.

## When collaboration hurts: design itself

The fantasy is a team looking at one shared model that anyone can change directly, so the design takes form bit by bit. That is not how collaborators design.

In reality:
- Each part has, at any time, one owner, who works alone preparing a proposal.
- The owner meets collaborators for a micro-session of design review, then retires to work out the detailed consequences.
- If a proposal is not accepted, the proposer withdraws and develops an alternative. The session reconvenes to choose, fuse, or strike off in a third direction.
- The fantasy has no function for *originating* designs, only for refining them.

Concurrency demands synchronization, design control, a resolution procedure and version control. Each designer designs against a *single time-stamped version*.
- If Jack routes air ducts while Jill routes steam pipes through the same tanker, they need that synchronization.
- If an admiral moves a submarine bulkhead in a playpen version, someone must check its effects on the other side and on structure, acoustics, piping and wiring before it reaches the standard version.

Tools that encourage committee design do more harm than good.

Once the exploratory stage is past and a basic theme is chosen, conceptual integrity rules and the design flows from a chief designer (SKILL.md, step 6). If the theme proves a blind alley, the team returns to collaborative exploration.

## Two-person teams are magical

Two is a magic number for collaborations, and pairs acting *uno animo* (with one mind) can do even conceptual design.
- **Pair programming**: initial productivity is less than two people working separately, but error rates drop radically, and rework is a large share of effort, so net productivity is higher.
- **The dynamics**: rapid informal interchange, no floor protocol, no domination. Short bursts of proposal, critique, counterproposal, synthesis and resolution form a single thread of idea development. "Two pencils may move over the same paper with neither collision nor contradiction."
- **Why it works**: articulating *why* as well as *what* exposes one's own fallacies; "as iron sharpens iron." Torrance found dyads produced twice as many original ideas, with twice the originality.
- **Pacing**: intersperse paired sessions with solo sessions to detail, document and prepare proposals.

A wise manager also launches a solo designer or a pair early to explore a technology that is foreseeable but not yet buildable.

Real design is always more complex than textbook examples. It always needs design-change control, "lest the left hand corrupt what the right hand has wrought."

## Telecollaboration

Teams distribute for specialization, home preferences, round-the-clock work, cost, and politics: the Airbus A380 was partitioned among four nations. "Distributed development of a unified product is *work!* Moreover, the distribution per se creates a lot of *extra* work!" Informal channels within collocated teams matter far more than anyone expects until they are gone. Space barriers are real; timezone barriers are real, sometimes more so; cultural barriers are very real.

Making it work:
- **Face-to-face time is crucial.** Ask how far you would walk to avoid a videoconference, call, email or letter for a lunch date, a complex deal, or firing an assistant.
  - Successful telecollaborations rest on long histories of face time and still need some. Without those histories, travel is worth its cost.
  - Airbus kept Bristol wing engineers resident in Toulouse, with a daily company plane: "none of these collaboration aids could be omitted."
  - System/360 spanned seven computers in four locations in three countries. It ran the first full-time transatlantic leased line, kept residents each way, and held annual two-week whole-team meetings, one of which settled some 200 hanging conflicts.
- **Clean interfaces**, defined meticulously, interpreted continually, and changed under control with wide communication. System/360's standard logical, electrical and mechanical I/O interface was its key enabling innovation. Management must design in advance a mechanism for resolving differences of opinion or taste: "There is no substitute for authority." Vague interfaces surface their errors late, at integration. Clean interfaces also bring joy, because owners can sign their work.
- **Matching tools across sites.** Airbus's partners ran incompatible CATIA releases, and wiring harnesses met conduits wrongly, costing about 22 months.
- **The document is the most potent technology.** Formal prose and drawings carry a precision that demands study and enables critique.
  - Blaauw and Brooks wrote a 1,200-page book by mailed drafts, on top of nine years of daily face time: "when a text paragraph couldn't be made to work, it was always because we didn't know what we were talking about."
  - **Telephone plus a shared document** is vastly more powerful than either alone: "Having to agree word-by-word forces the collaborative facing of many issues that would otherwise be missed."
- **Video** falls short in field of view, document sharing, resolution and depth cues. It is most valuable when faces and body language matter: screening unknown job applicants, issues vital to the participants, an insecure participant, or different organizational or national cultures.
- **Tools.** "Effective toolsmithing always starts with the *user* and the *task*." It works best when the toolsmith has a *real* user with a *real* task. Most collaboration tools spring from a technical idea instead.

## The divorce of design

Since the 16th century, designing has separated from doing. In the 20th century designers became progressively divorced from implementers and from users. Edison, Ford and the Wrights built their own designs; today's engineers cannot make their own chips. Hospital, reactor and laboratory designers lack the users' experience. Two forces drive this: implementation technology demands specialization, and designs are so complex they demand all of a designer's energy. "*Miscommunication abounds*": elegant buildings that are hard to work in, confusing reactor control panels, over-specified implementations that cost far more. "Communication *between* people is always much poorer than communication *within* a person." The exceptions succeed because their designers are users: UNIX, Linux, the iPod.

Recognize the divorces and marshal deliberate, focused effort against them. Four remedies:

1. **Use-scenario experience.** Even a little real use, or a good simulation, beats none.
   - Use full-scale mock-ups for dry runs of a kitchen or cockpit, and virtual environments.
   - Brooks apprenticed two weeks as an operator in a computer center before designing Stretch's operator console.
   - Kruchten sent Canadian air-traffic-control software people to ATC classes and to sit beside live controllers. The controllers took object-oriented design and Ada courses, and the two groups built a common vocabulary.
2. **Close interaction with users through incremental development and iterative delivery** (Harlan Mills). Build a minimal-function version that works, and give it to users to use or test-drive; for mass markets, use a sample. Brooks almost invariably made wrong assumptions about how his tools would be used.
   - Users of a room-filling virtual protein asked by the third session, "May I have a chair?"
   - Radiation-therapy planners preferred to sit and rotate the virtual patient rather than walk around it.
3. **Concurrent engineering.** Dig personally into implementation; even isolated, unrepresentative experience informs design, though beware the undue influence of a small sample. The best balance is true implementers intimately involved in design (in software, sometimes called agile). Implementers brought forward need richer visuals than drawings.
4. **Education of designers.** Teach the techniques and practice of *understanding* users' needs. Gould and Lewis give three principles:
   - early and continual focus on users, in direct contact from the outset;
   - empirical measurement of usage;
   - iterative design.

   Many designers think they do this while only hearing or reading about users, or "reviewing" late. Implementation experience is equally crucial. Prefer project courses with real outside users, and allow the student team to fail: "advanced methods can be self-taught when needed. Gut instincts are harder to acquire."
