# Representing design trajectories and rationales, and tools for designers

## Why record trajectories and rationales

Designers need to document how a design evolved: the *whats* and the *whys*. A rationale document is priceless to maintainers and prevents ignorant mistakes. It is also harder to produce than it looks. Brooks and his wife Nancy kept a 235-page prose log while designing a 1,700-square-foot house addition. Madison's notes on the Federal Convention are a stunning example of rationale capture.

## The knowledge is a web; documents are lines

Knowledge forms a general, nonplanar graph. Every linear document linearizes it in two moves:
1. **Cut edges** until the graph is a tree, which imposes a hierarchical order.
2. **Map the tree onto a line**, usually depth-first.

Then add back the cut links as cross-references:
- **A book**: the table of contents is the tree, page numbers give the line, and the index restores the cut links as chains.
- **A library**: the classification tree gives shelf order; the author, title and subject indices restore the rest.

Design spaces have this same web structure. Decisions share reasoning with their siblings and cousins, and design *processes* are harder still to represent.

## The design tree, defined operationally

Brooks's attempt to reconstruct the house addition's design tree from the log was "an experiment that failed," and what was learned in *trying* was more revealing than the tree. One lesson: define the tree precisely enough to be operationally useful, and try a pen-and-paper sample before choosing a tool. The definition he converged on works like configuring a built-to-order laptop:
- **Question nodes** pose design questions.
  - Sibling questions are orthogonal: *attribute branches*.
  - A question's options are mutually exclusive: *alternative branches*.
  - Each choice raises further questions.
- **The finished product** is the set of chosen leaf nodes, one per independent question.
- **Rationale nodes.** Each option carries pro and con nodes. Each question carries a choice-made-and-why node.

**Insights from the attempt:**
- **Design work uncovers requirements as well as satisfying them.** Analyzing an architect's proposed pavilions revealed two requirements nobody had recognized: the family needed a central place to congregate naturally, and a precious large black oak had to stay. "Design work doesn't just satisfy requirements, it elicits them." A good process encourages this.
- **Design means realizing that alternatives exist, as well as selecting among them.** Some alternatives come from exemplars; others are breakthroughs. Two Music Room configurations were both unacceptable, until a third appeared ("Config C—A real way forward!"). "A major part of design is realizing that design options exist."
- **The tree changes as the design changes.** The question tree already embeds design decisions. Brooks's first log page divided the task into "Three separable problems," New wing, Old West and Old East, each with its rooms. Why is the Entrance in the New Wing? That assignment was itself a design decision. Each high-level design carries a different organizational tree. Brooks hung the nodes off the *as-built* structure. Early abandoned alternatives affect larger portions of the tree, such as "Flip house end for end," which was short-lived but intrusive. Far-reaching changes grow fewer as the design stabilizes. A capture tool must track growth and the cutting and grafting of subtrees.

**Tree of decisions versus tree of designs.** In a decision tree the product is a set of leaves, so the best complete design so far is hard to see. In a *tree of designs*, each node specifies the sub-tree of products that agree in all decisions down to that node, and each leaf is a complete design. With *n* independent binary questions there are 2^n leaves, which is too cumbersome to draw but instructive. An agile nightly build is a node in the tree of designs: the best complete design so far.

**Modular versus tightly integrated.** Alternatives are rarely independent. The Music Room's placement affected the studies, the living room and the kitchen, forcing *compound* alternatives. Following Alexander, tight dependency makes revision hard. A designer may therefore deliberately trade design quality for ease of later modification (Parnas), or for speed and ease of the design process itself. Modular designs are easier to represent as decision trees, which may be what *modular* means. Complete modularity has costs, because an optimized component can serve several goals at once. A unibody car is lighter and stronger than a ladder frame, but a ladder-framed pickup converts more easily to an SUV.

**Capture tools:**
- Project-management and PERT tools support only the Waterfall. They have no conditional nodes and assume the major decisions are made.
- IBIS-style issue mapping (gIBIS, Compendium) structures argument. Razzaque's Compendium chart of the house wing distinguishes four node kinds (Design Alternative, Chosen Design Alternative, Requirements uncovered during design work, Question) and two links: design alternatives that are mutually exclusive, and design alternatives that are independent.
- Structured annotation *during* design restricts vague ideas and impedes conceptual design. CAD is too precise for quick exploration, while sketches allow vagueness. For capture, a generic diagramming tool with automatic tree layout serves better.

**When rationale capture gets adopted.** DRed, Rolls-Royce's design-rationale editor, succeeded where similar tools failed, for these reasons:
- **An existing rationale-capture culture.** Management allowed a DRed chart *instead of* the required prose report. A company without the culture did not adopt it.
- **A dedicated two-person link** between the users and the tool's builders.
- **Flexible use.** Teams sketched on a whiteboard in the meeting, then one person formalized the chart. It was also used solo, for both conceptual and detailed design, and without a facilitator.
- **Training through real problems.** About 600 engineers were trained, some through a six-week project course in which teams of four worked on real but non-essential problems and were allowed to fail.
- **No formal revision control**, because "if DRed were under it, DRed wouldn't be used."

DRed also found an unplanned use: diagnosing faults from field reports.

## The dream system for designers

Brooks's dream system was framed for house design and generalizes to software. Its focus is communication between the designer's mind and the system, with the designer's mind paramount. "New tools can lead us to better ways of thinking."

**Progressive truthfulness** (Turner Whitted's term): start from a model that is fully detailed but only resembles what is wanted, then adjust attributes one after another toward the vision. "Give me the Three-Bedroom Georgian House." "Face it north." "Mirror-flip it left to right." "Make the living room 14 feet wide." This beats the usual progressive refinement in three ways:
- At every step there is a prototype to study.
- The model starts valid, with no structural inconsistencies.
- It is always fully detailed, so perceptions don't mislead.

**A model library** of fine, fully detailed designs. With such a library, consistency of style is "the designer's to lose." Innovators such as Brunelleschi, Le Corbusier and Gaudí "innovated from mastery, not ignorance," so a library does not limit creativity. The true hazards lie in the library itself: bad models, too few models, too narrow a variety. They are worst at the beginning.

**Mind to machine:**
- **Hands and voice.** Use both hands, the dominant hand for precision and the other for framing. Point at nouns with the hands; speak verbs by voice, with a limited vocabulary and a user synonym dictionary. Keep menus for the novice, with keyboard equivalents under the left hand for the expert. The novice then acquires expertise one verb at a time, by their own frequency of use.
- **Strong locality.** Most choices come from a small subset, so customizable menus are essential.
- **Sketching.** It is primary, and it is 2-D, because the retina is.
- **3-D pointing** fatigues the arm, so let the elbows rest.
- **Viewpoint control.** Position (x, y) and heading change continually; eye height and roll rarely.
- **Follow-up questions.** A system that asks them must let experts turn them off.

**Machine to mind:**
- **Context and detail views at once.** Designers follow a universal sequence:
  1. study a big spatial chunk for context;
  2. zoom in;
  3. create or manipulate a local portion;
  4. zoom out;
  5. repeat.

  A single window enforces this hand-driven toggling. "Have two big screens showing these two views all the time!" The context can also be the library.
- **The 3-D view** is always in full detail. Kinetic depth (rocking the model) is the strongest depth cue.
- **The workbook view.** Bring in designs and action plans in progress. Take away the updated designs, a log of every action (for automatic backtracking), and dictated notes of what was tried, rejected and kept, each with *why*. "The *why*s, which cannot be captured from the action log, are crucially important for any complex design." They refresh the designer after an interruption, recall skipped trails of thought, and are priceless to new team members and project heirs. Page-corner inserts show the running cost estimate and the state of the budgeted commodity.
- **The specification view.** Specifications grow alongside the drawings. Library models carry their specifications.
- **For software**, the equivalent views are a rich starting library, a design display, a context display, a workbook display and a test-cases display, all cross-linked.

**Building it.** Build incrementally, with continual trials by real designers; an all-at-once project would almost surely fail. The hardest part is the initial library.
