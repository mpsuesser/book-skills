---
name: design-of-design
description: "The Design of Design (Frederick P. Brooks, Jr.) on designing complex things (software, computer architectures, buildings, books, organizations) with conceptual integrity. Use when the user names the book or Brooks, or its terms: Design Concept, conceptual integrity, Rational Model, Waterfall, Spiral, Co-Evolution, design program, budgeted resource, user and use models, \"better wrong than vague\", system architect, chief designer, design by committee, exemplars, \"designing the wrong thing\", great designers vs great processes. Also use when deciding what to design or eliciting requirements, fighting requirements bloat or contracting for design work, choosing a design process model, organizing or reviewing a design team or a distributed one, naming the scarce resource or challenging constraints, judging elegance, style or consistency, studying precedents, recording design rationale, writing a design retrospective, or recruiting, growing and protecting designers."
---

# The Design of Design

Brooks holds that the design process has properties that stay the same across media, so lessons cross between them. He designed in five: computer architecture, software, houses, books and organizations. He takes the engineer's viewpoint: utility, effectiveness, efficiency, elegance. His central finding is that "the boldest design decisions, whoever made them, have accounted for a high fraction of the goodness of the outcome." Bold decisions come from vision or from desperation. They are always gambles: extra investment in hope of a much better result.

His question for every designer is how to weld intuition to system: "Systematic design excluding intuition yields pedestrian follow-ons and knock-offs; intuitive design without system yields flawed fancies." He calls "a science of design" an impossible and misleading goal, so apply him as judgment backed by reasons and precedents.

## Core vocabulary

**Design.** From the OED: "To form a plan or scheme of, to arrange or conceive in the mind … for later execution." A *design* (the noun) is a created object. It comes before the thing designed and is distinct from it.

**Idea, Implementation, Interaction.** Dorothy Sayers's three stages of making:
1. Formulate the conceptual construct.
2. Implement it in real media.
3. Interact with users in real uses.

The essence of a design is the conceptual construct; implementation is accident. Few makers are Mozart ("Everything has been composed, just not yet written down"). For most, incompleteness and inconsistency appear only during implementation, so writing, experimenting and "working out" are part of designing. Blaauw split Sayers's implementation stage in two, giving computer design three separate activities:
- **Architecture**: exactly the properties that govern which programs run and what results they give, not how fast.
- **Implementation**: the machine organization that carries the architecture out.
- **Realization**: the technology that physically builds that implementation.

**Design Concept.** The shared, invisible thing an architect and a client actually mean while they gesture vaguely at the drawings. For the System/360 architects, the real System/360 was the Design Concept, and each physical model was one of Plato's shadows.
- "Unity of concept is the goal; it is achieved only by much conversation."
- That conversation is most direct when it is about the concept itself, not about derived representations or partial details.
- Detailing surfaces the team's conflicting versions of the concept and forces them to be resolved. Should the S/360 decimal datatype be modeled on the 32-bit integer or on the character string? The answer depended on whether a person's implicit concept was scientific or business.
- A product with no felt Design Concept shows it: OS/360 was a fusion of separately evolved parts.

**Conceptual integrity.** Unity, economy and clarity of a design: "the most important consideration in system design." It is also called coherence, consistency, or uniformity of style.
- Its test is consistency: "given a partial knowledge of the system, one can predict the remainder."
- A coherent tool does what one expects. It is easy to learn and use, and it delights.
- A solo designer gets integrity by making each microdecision the same way every time. A team gets it only through deliberate management; see `teams-and-collaboration.md`.

Its three component principles:
- **Orthogonality**: "Do not link what is independent." Changing one function should have no observable effect on the others. An alarm clock whose alarm works only when the face is lit violates it.
- **Propriety**: "Do not introduce what is immaterial." Every function should meet an essential requirement. Its opposite is *extraneousness*, such as a car's gearshift, which exists because of the implementation.
- **Generality**: "Do not restrict what is inherent." Users invent uses beyond the designer's imagination: "When you don't know, grant freedom."

**Routine, adaptive, original design.**
- **Routine** design follows a codified decision tree and can be automated: a 50-ft concrete bridge, a compiler for an established language.
- **Adaptive** design modifies a preceding design for new purposes.
- **Original** design, a "wicked problem" in Rittel and Webber's term, is the book's subject.

**Firmness, usefulness, delight.** Vitruvius's *firmitas, utilitas, venustas*. Brooks gives delight equal weight and assesses every design on all three. Firmness includes durability; usefulness includes uses nobody planned.

## Working a design

These are Brooks's prescriptions in the order a design project first meets them. Each step recurs as the design talks back: "the design-goal-setting process is itself iterative."

1. **Decide what to design.** "The hardest part of design is deciding what to design." Clients almost never know their complete requirements at the start, and "A chief service of a designer is helping clients discover what they want designed."
   - In Brooks's example, a client asked every day for revisions to a drawing-tracking database: "That's fine—it is what I asked for—but could you change it so that...?" Brooks realized that his most useful service was helping the client *decide* what was really wanted.
   - Put something concrete in front of the client early: a rapid prototype, a simulator, a full-scale mock-up, a virtual walk-through.
   - Treat goal changes as discovery: "Goal iteration must be considered an inherent part of the design process."

   The step is done when the client has reacted to something concrete and the stated goal has survived that reaction.

2. **Write the design program.** This is the architects' term for a document, prepared with the client, that sets out:
   - the **goal** (primary objective);
   - the **desiderata** (secondary objectives);
   - the **constraints**;
   - the **opportunities**.

   A design program is not a formal requirements specification, which is a contractual document. List every known constraint explicitly, including declared non-constraints. The House Wing program listed: budget not absolute, resale value irrelevant, land plentiful, design time plentiful. Explicit listing smokes constraints out early and keeps them in the designer's mind, so the designer notices when one goes away. Expect the program to grow: the House Wing's discovered objectives included a 40-person student group and its 40 coats.

3. **Make user and use models explicit.** Write down what you know about the users, the purposes of use and the modes of use. Also write down what you don't know but *assume*.
   - A **use model** is a weighted collection of use cases. When there are several user sets, describe each and give explicit weightings.
   - Where facts run out, **guess**. Postulate a complete set of attributes and values, with guessed frequency distributions. "An articulated guess beats an unspoken assumption."
   - **Better wrong than vague**: "Wrong ones will perhaps be questioned; vague ones won't." A vague model lets designers substitute themselves for the user, and they are not the user.
   - Then ask "Which assumptions matter? How much?" Where an important decision hinges on a guess, pay for a better estimate.
   - The chief architect owns the set the team works with and makes it known.
   - The reason for all this: a team that believes it shares assumptions doesn't. "Microdecisions too minor ever to be discussed will be made differently, and conceptual integrity will be lost." OS/360 grew two inconsistent debugging philosophies, one for batch and one for terminals, because subgroups held different use models.

4. **Name the budgeted resource.** "Name the scarce resource explicitly, track it publicly, control it firmly." There is usually one dominant scarce resource, and it is often not dollars. Examples from the book:
   - inches of oceanfront for a beach house;
   - ounces of payload for a spacecraft;
   - memory bandwidth, format bits or resident kernel memory for a computer;
   - pages for a grant proposal;
   - heat for a high-performance chip;
   - student learning hours for a curriculum;
   - political power for an organization's constitution;
   - calendar days for an asteroid interception.

   **Surrogates** stand in for the real resource: square feet for building cost, bits of register for chip area. A surrogate is simpler, usable before its cost ratio is known, stable, and it carries experience. Its danger is outliving its fit, as when area kept being budgeted after wiring length or pin count had become critical.

   The resource can also shift mid-design. OS/360 budgeted memory bytes until Ruthrauff's performance simulator showed a Model 65 compiling five Fortran statements a minute. From then on, disk accesses were the budgeted resource.

   Running the budget:
   - **Track publicly**: every sub-team knows its allocation and current state.
   - **Control firmly**: only one person controls budgeting and rebudgeting, holding a small personal kitty for late allocation (a general's reserves). Blaauw did this superbly with the bits of System/360's Program Status Word. Iverson made the number of distinct language concepts APL's budgeted resource and guarded it with "cautious stinginess."
   - The resource is usually a property of the design, not of the process. Schedule becomes it only when time is the product's own scarcity, as in a first-to-market race.

5. **Audit the constraints.** "Constraints are friends." They shrink the search space, focus the work and call forth invention. Michelangelo's David was cut from a cracked block another sculptor had abandoned. Sort every constraint into one of four kinds:
   - real;
   - obsolete once-real;
   - misperceived as real;
   - intentional artificial, like Bach's self-imposed forms; Brooks doesn't recommend these for engineering or software.

   Misperceived constraints often arrive as dictated implementations. "When you specify something to be designed, tell what properties you need, not how they are to be achieved." For the FAA's 9020 air-traffic system, MITRE's architects specified a triple modular redundant configuration: three peripheral adapters, three I/O channels, three processors. IBM proposed three System/360 Model 50s, each serving as both I/O channels and processor, which more than met every performance and reliability requirement. It was rejected for lacking the specified topology, though "what they were actually shopping for was function and reliability, not topology." IBM delivered six Model 50s instead: three with processors disabled serving as I/O channels, three with I/O channels disabled serving as processors. That was twice the components and considerably *less* reliable, at the same price. Faced with false constraints, the designer "should fight back!"

   Scan the list periodically: "Can this constraint now be removed because the world has changed? Can it be entirely circumvented by working outside the design space?" A setback rule blocked the Music Room, and Brooks bought a 5-ft strip of land from the neighbor.

   When a constraint vanishes, its discipline goes with it. Disk residence removed the size limit that had disciplined earlier operating-system designers, and OS/360 grew "too rich."

   An unconstrained-seeming task is the hard case: "A general-purpose product is harder to design well than a special-purpose one." Brooks's advice is to "first think harder about what is really desired, about the user and use models, and you will probably find some narrowing constraints."

6. **Explore radically, then commit through one mind.** Explore radical alternatives early, before anyone is wedded to one. Concrete alternatives draw out desiderata and constraints nobody had spoken. Small-team study, brainstorming and design competitions all serve this stage; see `teams-and-collaboration.md`. Then look for the bold decision. Once a basic theme is chosen, "Conceptual design, especially, must not be collaborative": "A design flows from a chief designer, *supported by* a design team, not *partitioned among* one." If the theme proves a blind alley, return to collaborative exploration.

7. **Iterate empirically.** Brooks is "a dyed-in-the-wool empiricist." Humans err in defining objectives, architecture, implementation and realization, and that fallibility prescribes the method:
   - early prototypes and early user testing;
   - iterative, incremental implementation;
   - a rich bank of test cases;
   - regression testing after every change;
   - frequent but not continuous interaction with representative users, with successive prototypes as the vehicle (Boehm's Spiral);
   - many detailed use scenarios. Asking "Where will guests at meetings put their coats?" moved a master bedroom to the other end of a house.
   - multidisciplinary design review, including Mills's cleanroom practice, in which the designer explains to a group why the design is correct and the group challenges the arguments and the implicit assumptions.

   Mind the limit: "none of these analyses and simulations addresses the rightness of the goals or the validity of the assumptions about the environment."

8. **Document the whats and the whys.** Record:
   - the design proper;
   - the designers' intent, "so that the later maintainer will not in ignorance loose a vital stone from the edifice's arch";
   - a style sheet for the repeated microdecisions;
   - a log of what was tried, what was rejected and what was kept, each with *why*.

   The action log captures what was done; only the designer can capture why. See `rationale-and-tools.md`.

9. **Ask the top-level question again.** "The besetting mistake of expert designers is not designing the thing wrong, but designing the wrong thing." Ask: "Is a paradigm shift under way? Will your assumptions still be valid a decade hence? Are you designing the right thing?" Ask it hardest after a success. "Success is dangerous for the professional designer."

**Give design its time.** Brooks's case studies repeat one lesson. Plenty of design time paid off for the houses, the kitchen and System/360, and OS/360 suffered from too little. More design time gives a better, longer-lived product, and it can deliver sooner by cutting rework, which is often as much as a third of design cost. Unbounded time is the opposite failure: the *Computer Architecture* book had unlimited time and arrived too late to have its full influence. "I am convinced that most projects need to devote a larger share of the total schedule to design."

## Diagnostics

Read a troubled design or project against these named failures.

| Symptom | Brooks's diagnosis | Remedy |
|---|---|---|
| Requirements are a union of wish lists, neither prioritized nor weighted | Committee requirements and **logrolling**: "I won't naysay your wish, if you won't naysay mine." Nobody advocates for the product itself. Speed, smallness, robustness and ease of use have no ardent champions. | A few overriding objectives, schedule urgency, one strong manager who stays, a traceability matrix (`process-and-contracts.md`) |
| Peers negotiate the design among themselves | **Design by committee**, "where none dare say 'No' to another's suggestion" | A system architect with authority (`teams-and-collaboration.md`) |
| Complete specifications demanded and contracted up front | The **Rational Model / Waterfall** followed slavishly: too-early binding yields "fat, cumbersome, over-featured products" and disasters of schedule, budget and performance | Spiral with explicit contracting points; contract design and construction separately (`process-and-contracts.md`) |
| Each team member pictures a different user | Implicit or vague user models | Step 3 |
| A skilled team builds the wrong thing well | **Designing the wrong thing**: too much experience brought to the task, a "pedestrian vision," Petroski's cycle of growing boldness | Step 9; study failures even more carefully than successes (`style-and-exemplars.md`, on JCL) |
| A deliberately tiny core sprouts jury-rigged extensions | "elegant" simplicity not up to the actual complexity inherent in the task (JCL's six verbs) | Match expressive power to the task's real complexity |
| Novelty pursued for its own sake | **Gratuitous innovation**: "a foolish idea and a selfish indulgence of pride." "Originality is no excuse for ignorance." | Master the exemplars first (`style-and-exemplars.md`) |
| A rough cost estimator rules out an option | A square-foot or instruction-mix estimate has lopped a feasible branch whose marginal cost is low: "One can often get something for nothing, if one has previously bought nothing for something." | Estimate the marginal cost of the specific change |
| Functional goodies pile up | A disciplining constraint went away unnoticed (OS/360 on disk) | Step 5: notice the vanished constraint and replace its discipline |
| The spec bends whenever the build is hard | A single implementation, for which changing the manual is always easier than changing the machine | Multiple concurrent implementations of one architecture |
| Elegant artifacts that are hard to use or to build | **The divorce of design** from use and from implementation: "Miscommunication abounds" | The four remedies (`teams-and-collaboration.md`) |
| Innovative proposals die in review | The product process is conservative, aims at predictability, "fights the last war," and is veto-oriented | Step outside the process; protect only the crown jewels; easy exceptions (`great-designers.md`) |
| A manager second-guesses the designer | The design was never entrusted | A chief designer with complete authority over the design (`great-designers.md`) |

## Going deeper

Each file builds on the vocabulary above. Read the one the situation calls for.

- `process-and-contracts.md`: the Rational Model in full and the six ways it fails; Co-Evolution, Bazaar and Spiral; requirements bloat and its cure; sin and contracts; the building-practice model for contracting; rationalism versus empiricism and formal proof. Read it when choosing or defending a process model, writing or contracting requirements, or arguing about verification.
- `teams-and-collaboration.md`: the costs of collaboration; the system architect and the single user-interface designer; when collaboration helps (needs, objectives, radical exploration, brainstorming, competitions, product fights, design review) and when it hurts; two-person teams; telecollaboration; the divorce of design and its four remedies. Read it when organizing, staffing, distributing or reviewing team design work.
- `great-designers.md`: why great designs come from great designers rather than great processes; what processes are properly for; making processes that permit greatness; entrusting a chief designer; finding, teaching, growing, managing and protecting designers; growing yourself as a designer, with Brooks's recommended reading. Read it when setting up a design organization or process, or planning a designer's development.
- `style-and-exemplars.md`: esthetics (parsimony and its limits, structural clarity, consistency); style as repeated microdecisions and how to get a good one; exemplars, their roles and how to study them; originality and pride; how expert designers go wrong, with JCL in detail. Read it when judging elegance or style, writing a style sheet, studying precedents, or auditing an expert team's assumptions.
- `rationale-and-tools.md`: representing design trajectories and rationales (design trees, the tree of designs, modularity trade-offs, rationale-capture tools and the conditions for their adoption), and Brooks's dream design system (progressive truthfulness, model libraries, context and detail views, the workbook of whys). Read it when recording design history or designing tools for designers.
- `case-studies.md`: seven designs analyzed in one format, with their bold decisions, budgeted resources, mistakes and lessons: a beach house, a house wing, a kitchen, System/360, OS/360, a book, and a three-university computation center's governance. Read it for worked examples in any medium, or when writing a design case study or retrospective in Brooks's format.
