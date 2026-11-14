# Esthetics, style, exemplars, and how experts go wrong

## Esthetics in technical design

Vitruvius named three virtues: *firmitas, utilitas, venustas*, or firmness, usefulness and delight. Delight ranks equal with the other two. In technical design, delight is often logical beauty: the "elegant" language and the "clean" computer both refer to logical structure. Chesterfield: "Style is the dress of thought."

**Parsimony.** Elegance in mathematics means "accomplishing a great deal with few elements." Lisp's tiny core, with its extensibility and composability, is the model; Visual Basic is more complex and harder to extend. Parsimony is not the whole story:
- Index registers are logically unnecessary, yet they radically improve performance per cost.
- Van der Poel's one-op-code computer was sufficient but hard to program. It needed a library of nonobvious idioms, and its delight was a crossword puzzle's: "a construct of intentional complexity and no intended utility."
- APL one-liners are "crossword puzzle sport, not elegant design."
- "Programming languages exist to facilitate the writing—and the much more frequent reading—of programs, not to serve as puzzles."
- Explaining a parsimonious design still needs expansion and examples.

**Structural clarity.** Clarity is straightforwardness: a "direct route from what one wants to say to how one says it." The basic structural concept should be "plainly evident and, if not logically straightforward, easily explained." Familiar, simple metaphors give user interfaces their structure: the Macintosh desktop, the VisiCalc spreadsheet.

**Consistency.** Blaauw and Brooks's criteria for good architecture: a design that lacks needed functions is *erroneous*; one that is awkward or too complex to learn falls short; a straightforward one is *clean*. "Consistency underlies all principles of quality." In a consistent square-root operation, for example:
- the formats match the other floating-point operations;
- precision, range, rounding and significance follow the same rules;
- a negative argument raises an exception just as divide-by-zero does.

The touchstones of consistency are brevity of description, simplicity of code generation, and suitability for many implementations. Orthogonality, propriety and generality (defined in SKILL.md) derive from it.
- **Propriety's two refinements.** *Parsimony* is one subset of propriety. *Transparency* is another: the implementation produces no visible side effects, as a pipelined datapath stays invisible to the program.
- **Extraneousness**, propriety's opposite, breeds rules. Twos-complement arithmetic has a unique zero and is proper. Signed-magnitude and ones-complement have a signed zero, which is extraneous and brings extra rules and unexpected effects.
- **Generality** comes through open-endedness, complete function sets, decomposition into orthogonal components, and composability. Users invent uses beyond the designer's notions: the Intel 8080A's Restart instruction was used mostly for subroutine return.
- **Self-teaching.** A consistent design teaches itself, and so it resolves the conflict between ease of use and ease of learning. If fixed-point is a subset of floating-point, comprehension grows naturally from one to the other.

## Style

**Working definition:** "Style is a set of different repeated microdecisions, each made the same way whenever it arises, even though the context may be different." Related microdecisions are resolved in related ways: Wright's rectilinearity, Cray's preference for maximum performance over compatibility.

Style is a habit that economizes mental effort, and the bundle of consistent microdecisions makes it recognizable. People can tell a century or a composer, or that something "looks as if" Cray designed it. During the war, operators could identify individual Morse senders by their "fists." The authorship of *The Federalist Papers* was settled from prose style, and programmers recognize each other's code.

Two things about a style affect delight: how consistently it is carried out, and its intrinsic qualities. "A mishmash of styles delights no one." Integrity matters most in the overall structure (the bones), but uniform style in the details (the skin) matters too.
- **Clarity.** Consistency across macro- and microdecisions gives a *clear* style, one that can be described economically. A baroque style can be clear; a spare one need not be. Little consistency gives an *opaque* or *muddled* style. "Consistency brings clarity, and clarity brings delight."
- **Comprehensibility.** A consistently applied style aids learning, use, recollection after disuse, maintenance and extension.

**Properties of style:**
- **Costly to specify.** The *Chicago Manual of Style* runs 984 pages, and Fowler spends about 2,800 words on *the*.
- **Hierarchical.** English prose style runs from dialect and diction, through person, tense, formality, vividness and warmth, to prosody, usage, punctuation and layout.
- **Evolving.** Gothic went Early, then Decorated, then Perpendicular. Fashions move faster.

**To get a consistent style, document it.** "A clear style may not be a good style; a muddled one never is."
- A sole author of a ten-page paper has a clear style without trying.
- A book needs its stylistic microdecisions documented.
- A multi-author work needs a style sheet or a careful final editor.
- Some decisions come given: a journal's style manual, an engineering standard, a subroutine library. Unprescribed microdecisions always remain. *Computer Architecture* grew a 19-page Writing Style Sheet to settle questions like how to refer to a computer: by manufacturer and model at every mention, at the first mention, or once per chapter?
- Document the design and *why*, and record internally the microdecisions that preserve conceptual integrity, so maintenance keeps them.

**To get a good style:** "The prescription is simple; the methods, straightforward; the work, arduous."
1. **Study other designers' styles** intentionally, and practice working in another's style, as Respighi did in *Ancient Airs and Dances* and Kreisler in the style of Pugnani.
2. **Make conscious judgments.** Write down which styles you like, and why.
3. **Practice. Practice. Practice.**
4. **Revise**, hunting for stylistic inconsistencies.
5. **Choose designers carefully**, by the clear styles and good taste shown in their previous work.

## Exemplars

"Rarely does one get to do a design that is entirely new." Even novel designs derive from earlier artifacts. Following Hillier and Penn, the vast field of possibility can only be searched with prestructures, and these justify bringing in past solutions and style. Exemplars serve as "safe models for new designs, implicit checklists of design tasks, warnings of potential mistakes, and launching pads for radical new designs."
- Palladio measured Roman monuments.
- Jefferson studied Palladio and the buildings of Paris.
- Bach walked 250 miles to hear Buxtehude, and he copied Palestrina by hand.

**Computer and software design lag the older disciplines.**
- An amateur uses whatever exemplars they happened to meet. A trained architect is exposed to whole libraries across eras, styles and schools, with expert-guided tours.
- Computer architects are shaped by the first machine they substantially programmed: DEC's minicomputers by Whirlwind, System/360 by the 704 and 1401, early microprocessors by the PDP-11.
- Software patterns help, but whole-system descriptions are scarce.

**Study rationales, not only designs.**
- Read the manual for the architecture, the maintenance documents for the implementation, and the technical papers for the rationale.
- Papers emphasize the whats and are skimpy on the whys, and they are rationalized *post hoc*, "far more rational in retrospect."
- The exceptions cluster at early days and at revolutions, so learn from those. In computer architecture the line runs from Burks, Goldstine and von Neumann's 1946 "Preliminary discussion" through Stretch, the CDC 6600, System/360, Atlas's virtual memory, the minicomputer revolution, the microprocessor and RISC.
- Each revolution's incumbents missed it: the mainframe makers were "fat, dumb, and happy."

**How a design discipline matures:**
1. collection of designs;
2. careful, evenhanded criticism;
3. comparative analysis, which assesses each design's differences against that design's own objectives (criticizing its choice of goals instead does not help);
4. rules of good practice for synthesis;
5. handbooks;
6. standards.

Software is far behind on this path. Its systems are orders of magnitude more complex to describe, and academia doesn't reward the systematizers.

**Laziness, originality, pride.** Brooks does not advocate slavish copying.
- "The designer should know well the exemplars of his craft, their strengths, their weaknesses. Originality is no excuse for ignorance."
- In engineering, gratuitous innovation, meaning innovation not expected to be better in some useful sense, is "a foolish idea and a selfish indulgence of pride," because unintended downside consequences are unavoidable.
- "Designers who master the styles of their predecessors have more treasures upon which their originality can draw." Lazy copiers draw only on current and fashionable exemplars.
- Delight lies in the superior elegance of a new solution to an old problem, like the Leatherman, the Slinky or the cable-stayed bridge, not in novelty itself. Mere novelty is a seven-day wonder.
- "He who seeks originality is apt to find novelty, but not permanence of delight." Whoever seeks designs that really work is most apt to produce new designs of enduring value, almost as a by-product.
- "The desire to be original has degraded many a work." Sitterson Hall's "originality" gave it an ugly steel roof and dormers set too high. Wren built St Paul's to its glory within the tradition.

## How expert designers go wrong

"The besetting mistake of expert designers is not designing the thing wrong, but designing the wrong thing." Amateurs make many little mistakes; professionals goof big. Bridges collapse during construction, houses are drawn without stairs, computers waste memory bandwidth, languages grow too rich to learn.

**Petroski's cycle**, after each revolution in materials or technique:
1. Designers tread cautiously.
2. They master the new approach.
3. They extend it boldly, forgetting its underlying assumptions.
4. They overreach.

Major bridge failures come at roughly 30-year intervals. A new generation is trained in a technique without having suffered its birth pangs, the controversy that probed its assumptions, so it knows the trees and misses the woods. Being preoccupied with *doing the thing right*, it fails to ask "Am I doing the right thing?" "Success is dangerous for the professional designer. Failure stimulates analysis, scrutiny, rethinking. Success stimulates confidence both in design technique and in oneself. Both trusts may be misplaced." The System/360 architects rejected automatic memory management, and it had to be remedied "almost before the paint was dry."

**JCL**, OS/360's Job Control Language, is in Brooks's words "the worst computer programming language ever devised by anybody, anywhere," and it was built under his own supervision. Its biggest flaw: JCL is a programming language, and its designers did not perceive it as one. The other flaws follow:
- **One scheduling language for all programming languages**, so every user needed two languages. Schedule-time capability belonged inside each language, as compile-time facilities do in PL/I and macro assemblers.
- **Assembler-like syntax**, though by 1966 assembler ran only about 1% of jobs, and not exactly like assembler either.
- **Card-column dependence** (72 columns), just as the very system was pushing users onto terminals.
- **Too few verbs.** The designers' proud boast was that JCL had only six verbs, but its functions far exceeded six. "With an imposed 'elegant' simplicity not up to the actual complexity inherent in the task at hand, the complexity inevitably breaks out in jury-rigged solutions."
- **Declarations doing verbish things**, such as the DD statement's DISP parameter.
- **Almost no branching, no iteration, and no clean subroutine call**, even though scripts were full of open subroutines.

**How JCL got that way:** "The professionals who designed JCL brought too much experience to the task. Their familiarity with what they thought to be the problem blocked their thinking about it afresh, in its wider setting. In this case, following an exemplar brought disaster." They saw the job as a replay of the 1410/7010 OS, which was about two orders of magnitude simpler, and stated it as "a few control cards for the scheduler." Each word of that goal misled:
- *Few* equated fewness with simplicity, which gave too few verbs; real scripts ran to dozens of statements.
- *Cards* built the language around the punched card just as it galloped into obsolescence.
- *Control cards* implied separately interpreted, independent commands, hence the stunted branching, iteration and subroutines.

"Our basic problem was a *pedestrian vision*." JCL "was never really designed—it just grew." Every new schedule-time function was loaded on as a new keyword parameter, so adjectives in declarations became imperative verbs.

**Lessons:**
1. Study failure examples even more carefully than successes.
2. Watch yourself after success.
3. Think at the top level about the object and its assumptions about the environment it will be used in (the questions in SKILL.md, step 9).
