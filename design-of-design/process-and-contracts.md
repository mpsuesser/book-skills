# Design process models, requirements and contracts

Brooks's argument: a formal process model is needed, and since designers think spatially it must be one they can picture. The linear Rational Model is natural, but it is misleading. A bad model matters, because too-early binding produces bloat and disaster. The model persists because of its seductive logical simplicity and because contracts demand it. The Spiral is the most promising replacement.

## The Rational Model

Herbert Simon gave the model its most influential statement: "the theory of design is that general theory of search … through large combinatorial spaces." Pahl and Beitz's German engineering method and the Waterfall reached the same model independently. Its parts are:

- **Goal**: the primary objective, e.g. a beach house.
- **Desiderata**: secondary objectives, e.g. withstand a hurricane, sleep and seat 14, give views.
- **Utility function**: weights the desiderata. Designers imagine it as a linear sum, but each goodness term actually saturates; more window area or more electrical outlets stop adding value.
- **Constraints**: either *binary* (a 10-ft setback) or *elastic*, with steeply rising penalties (a schedule). Some are simple, and some conceal terrifying complexity ("The house must satisfy all the building codes").
- **Budget**: a fixed resource allocated among the elements, "perhaps not $ cost". This is the budgeted resource of SKILL.md, step 4.
- **Design tree of decisions**: each decision narrows the space. Designers search the tree, test each branch for feasibility against the constraints, and *satisfice* (Simon), stopping when the design is good enough.

The search runs as a loop:

```
UNTIL ("good enough") or (time runs out)
  DO another design (to improve utility function)
    UNTIL design is complete
      WHILE design remains feasible, make another design decision
      Backtrack up design tree; explore a path not searched before
  Take best design
```

**Design tree branches** come in two kinds:
- An **attribute branch** subdivides the design: each branch is a different attribute to specify, such as an alarm clock's "Alarm".
- An **alternative branch** enumerates options, one of which must be chosen, such as the alarm's "Sound".

Blaauw and Brooks's portion of the tree for an alarm clock, with `+` marking the attribute branches and `|` separating alternatives:

```
CLOCK +
├─ VISIBILITY: LUMINOUS DIAL (ELECTRIC LIGHT | PHOSPHORESCENT LIGHT) | PLAIN DIAL
└─ ALARM +
   ├─ SOUND: BUZZER | CHIME | RADIO
   ├─ SETTING
   └─ CONTROL: SET (ONCE | DAILY) | STOP (OFF | SLUMBER)
```

Engineers search roughly depth-first from an initial proposal. Building architects search laterally among alternatives at every level.

**Royce's 1970 Waterfall paper** set up the sequential model as a straw man to argue against. Its seven steps are System requirements → Software requirements → System design → Program design → Coding, unit test → Integration, system test → Operations, maintenance. Each is planned and staffed differently, and iteration is limited to the neighboring steps: "an iteration with the [immediately] preceding and succeeding steps but rarely with the more remote steps in the sequence." Brooks once advocated the model and has repented.

**What is right with it.** Any systematization beats "Let's just start coding, or building." The model gives:
- clear steps for planning, milestones, organization and staffing;
- one vocabulary for talking with managers and stakeholders;
- something teachable, which tells a novice where to begin.

Early explicit goals, desiderata and constraints prevent wandering and unify the team. Systematic search broadens the horizon. But the model is much too simplistic.

## What is wrong with it

1. **We don't really know the goal when we start.** See SKILL.md, step 1. Knowing the complete requirements up front is the rare exception.
2. **We discover the design tree as we go.** Original design involves novelty in goals, desiderata, constraints or fabrication technology. Few designers work in depth on as many as 100 projects in a lifetime, and engineering designers rarely explore alternatives that are not clearly on the way to a solution.
3. **Nodes are tentative complete designs, not decisions.** Branches are linked by exclusion, affinity or trade-off. At each node the real choice is among several tentative complete designs. The order of decisions matters greatly. Following Parnas, put the decisions least apt to change nearest the root, because flexibility is itself a goal.
4. **The goodness function cannot be evaluated incrementally.** Performance and cost depend on detailing that comes later, so designers must estimate and prune as they go. Experience helps, both direct and surrogate: "The most potent reason to study design history is to learn what *doesn't work*, and *why*." Rough estimators such as square-foot cost or instruction mixes can lop off feasible branches. An example is pushing out a wall under a roof that is already specified, where the marginal cost is low.
5. **Desiderata and weightings keep changing.** Donald Schön's term is *reflection-in-action*: the situation "talks back," and the designer's conversation with it is reflexive. Use scenarios expose new desiderata; the coats question moved a master bedroom. Low-marginal-cost goodness, once it appears, must be preserved. Sitterson Hall gained a serendipitous 125-person conference facility this way.
6. **Constraints keep changing.** The environment changes: setback rules, electrical codes, a chip withdrawn from the market. Discoveries change them too: solid rock under the site, chip cooling limits. Constraints also go away. A skillful designer with a flexible design leaps to exploit that, but more commonly nobody notices, or remembers what the constraint had foreclosed. The cure is the design program's explicit constraint list. A breakthrough can come from stepping outside the design space to remove a constraint, such as buying land instead of seeking a variance.

**Critiques Brooks endorses:**
- Nigel Cross: expert designers contradict conventional problem-solving theory, and design reasoning is *appositional*: "designing seems to proceed by oscillating between sub-solution and sub-problem areas, as well as by decomposing the problem and combining sub-solutions."
- Royce's counterflow arrows two boxes back are "A Band-Aid, not a cure."
- Schön: Technical Rationality fits only well-formed problems. Real practice involves uncertainty, instability, uniqueness and value conflict, and its problems must be *set*, constructed from problematic situations.
- The most devastating critique: "Designers just don't work that way."

**Why the model matters.** Designers are spatial thinkers ("Where is next November?" is a curb-stone test of design talent), and process models live in their heads as diagrams that shape thinking subconsciously. A deficient model hinders designers and mis-educates their successors. In software it makes us demand up-front requirements, believe they can be written, and contract "on the basis of this enshrined ignorance." The map is not the terrain. "The Waterfall Model is wrong and harmful; we must outgrow it." Disciples less gifted and more fervent than the founders harden any model into rigidity and oversimplification. Standards enshrined it: DoD-STD-2167A in 1985, VDI-2221 in 1986.

## Better models

Brooks's position: there *will* be a dominant model, so substitute a less misleading one rather than "let 100 models bloom." A replacement must emphasize the progressive discovery of requirements, be memorably *visualized*, and still allow contracting among fallen humans.

- **Co-Evolution** (Maher, Poon and Boulanger): the problem space and the solution space co-evolve, exchanging information, and understanding of both is generated and evaluated incrementally. Its two tracks, requirements definition and solution development, alternate: problem statement 1, prototype 1, problem statement 2, prototype 2, and so on. It captures progressive discovery and is memorable. But it is not comprehensive, gives no image of convergence, and has no milestones or contracting points.
- **Raymond's Bazaar** (open source): a user sees a need, builds a module and gifts it. Prestige is the incentive, market selection among modules is the quality control, and testers are many. The gift-prestige economy works for people otherwise fed, because their contributions are by-products. Conceptual integrity still came from one overarching force (Linus Torvalds) and from a pre-existing functional specification and system design (UNIX). Its success derives from *the builders being the users*, which lets requirements stay implicit. Brooks doubts it works when builders aren't users. Distinguish "anybody can change it" from "anybody can see it."
- **Boehm's Spiral** (1988) is the most promising. Each turn, growing in cumulative cost, passes through four quadrants:
  1. "Determine objectives, alternatives, constraints";
  2. "Evaluate alternatives, identify, resolve risks": risk analysis and a prototype, with successive prototypes leading to an operational one;
  3. "Develop, verify next-level product": turn by turn, concept of operation, software requirements, product design, then detailed design, code and tests;
  4. "Plan next phases."

  Each turn ends in a review, the commitment partition. The spiral suggests progress, ties repetitions of the same activity together, is memorable, and emphasizes prototyping, starting with user-interface prototypes and user testing long before an operational prototype is possible. Brooks wants the model designer-centered, with *frequent* but not *continuous* interaction with representative users and successive prototypes as the vehicles. His way forward: embrace and develop the Spiral, and punctuate it with **explicit contracting points**. At each point state what can be contracted, what certainties exist, and how risk is explicitly distributed.

## Requirements, sin and contracts

**The LHX helicopter.** It was meant to succeed four helicopters with different missions. An inter-group committee set the requirements, including "And it must ferry itself across the Atlantic." That capability had to be paid for in reduced capacity elsewhere, not just in dollars. Buying more C-5 transports to carry it was "not possible." The committee had neither an aircraft engineer nor a helicopter pilot. It became a reconnaissance helicopter, two were built, and the program was scrapped.

**Committee requirements:**
- Each member carries a wish list from constituents, plus ego and reputation.
- Logrolling is endemic.
- "Who advocates in the requirements process for the product itself—its conceptual integrity, its efficiency, its economy, its robustness? Often, no one."
- The result is grossly obese requirements, assembled without constraints, neither prioritized nor weighted, because social forces forbid it. Designers then weight them implicitly by their own user models, cut off from the setters' deep knowledge.
- Designers cause bloat too. In a Boehm classroom experiment, the team working from lovingly crafted specifications added features to "complete" the design or make it consistent.
- OS/360 rejected a marketing committee's requirements as impractical. A small team of architects, marketers and implementers extracted the essence instead.

**Fighting bloat and creep**, "by both birth control and infanticide." The Air Force Studies Board found the successful programs of the past had "*one or a few* clear overriding objectives and *schedule urgency*." They began with a few top-level requirements, broken down later by hard-driving managers who balanced function against schedule and cost.
- Schedule urgency is the best defense against creep. It was Brooks's own too. Lost urgency gets replaced by layers of "oversight."
- Define clear key performance parameters by Milestone A. Define detailed requirements *during* system development, by Milestone B.
- The top recommendation: appoint early-on strong, seasoned, domain-knowledgeable managers who stay through initial delivery. Empower them to "tailor standardized processes and procedures as they feel is necessary."
- Use a **Requirements Traceability Matrix**: every detailed requirement must derive from one or more of the initial overall requirements. None should sneak in from a user representative's request or "a designer's desire to do something clever, novel, and putatively useful."

**Sin.** Imagine a client who is never greedy, an architect who is the client's agent, an honest, high-quality builder and excellent communication. Then cost-plus would give the most value per dollar, design-build would be fastest, and an explicit Spiral would give the best product. The Waterfall persists because of sin (pride, greed and sloth) and because humans can neither trust each other's motives nor communicate perfectly. Organizations often behave worse than any of their members would.

**Contracts** best explain the Waterfall's persistence. "Get it in writing" forces too-early binding of goals, requirements and constraints. The adversarial counter-move: "Low-ball on the contract; make it up on the change orders."

**A model for contracting**, from building practice:
1. The client develops a *program*, not a specification.
2. The client contracts with an architect, hourly or by percentage, for *services*, not for a *specified product*.
3. The architect *elicits* a more complete program from the client, the users and other stakeholders. It does not pretend to be a rigid, contractable specification.
4. The architect makes a *conceptual design* that reconciles the program with budget, schedule and code. This is the first *prototype*, *conceptually tested* by the stakeholders.
5. After iteration comes *design development*: detailed drawings, a 3-D scale model, mock-ups. After further iteration come construction drawings and specifications.
6. The client uses those drawings and specifications for a *fixed-price contract* for the product.

The model separates the contract for design from the contract for construction. That clarifies much even when one organization does both. It is not fully sequential, since change orders still occur, and its schedule is long.

**Design-build** (concurrent and pipelined) fits projects that have close client-architect-contractor trust, well-understood design challenges, or a pressing hurry that justifies higher risk. Construction drawings are then produced first for what the builder needs first: long-lead-time steel, site work, foundations. A system project meeting these conditions must identify its build order and its long-lead-time components.

## Rationalism versus empiricism

The question: "Can I, by sufficient thought alone, design a complex object correctly?" Underneath, it is a view of man as creator.
- **Rationalists** say yes. Man is perfectible by education, so the right training and enough careful thought yield a flawless design. Their method is to reason the design into flawlessness (Dijkstra: design it correct, prove it correct).
- **Empiricists** say no. Man is flawed, so whatever he makes is flawed. Their method is to find the flaws by experiment and iterate.

Brooks is an empiricist. Only twice did a program of his run right the first time.

- **Formal proof** is proper for small, critical cores such as secure OS kernels. Proofs too can be fallacious. Their value is that proof reasoning differs in form from design reasoning, so the same mistake is unlikely to slip past both. Proof work rivals building work, so contain the proven core. "No proof can show that the original objectives for the program were right." At Warsaw, Lufthansa 2904's braking logic followed its specification, and the specification was wrong for the circumstances.
- **Mills's cleanroom review** is the wise balance where formal proof is infeasible but abandoning systematic verification is dangerous. It is systematic, non-formal group scrutiny of the designer's argument that the design is correct.
- **In other media**, design is verified by analysis and simulation: stress, vibration and acoustic analysis, walk-throughs, hurricane and earthquake loading, circuit and logic simulation, running an OS on a simulator. *The Federalist Papers* argued the U.S. Constitution's feasibility, and the Civil War, a system crash, exposed its incompleteness. None of these checks addresses whether the goals were right, so testing and iteration remain necessary. Careful thought helps.
