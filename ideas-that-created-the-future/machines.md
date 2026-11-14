# Machines

Papers 3, 7, 10, 15 and 25: the Analytical Engine as Lovelace programmed it, Aiken's tape-controlled calculator, the EDVAC stored-program design, microprogramming, and the integrated-circuit forecast.

## 3. Menabrea, *Sketch of the Analytical Engine Invented by Charles Babbage*, with Notes by Ada Augusta, Countess of Lovelace (1843)

**Set out to.** Menabrea wrote up the lectures Babbage gave in Italy in 1840; Lovelace translated them and added Notes A–G. The aim was to explain how a machine could carry out all of analysis "if their laws are known".

**Menabrea's construct.**
- **The problem.** Pascal's machine was a curiosity; it really did only + and −. Machines that need continual intervention by a human agent invite error. The "double problem" is to unite correct results with economy of time.
- **Two classes of operation in analysis:** the numerical calculation of coefficients, and their distribution to the quantities they belong to. For example, (a + bx)(m + nx) = am + (an + bm)x + bnx².
- **No trial and guess-work.** Once given the primitive data, the machine must do every step by itself, so it "must exclude all methods of trial and guess-work, and can only admit the direct processes of calculation". "The machine is not a thinking being, but simply an automaton which acts according to the laws imposed upon it." Doing division without guessing was an early research problem. The four arithmetic operations suffice for all numerical calculation.
- **Representation.** Numbers sit in columns of discs on a common axis, digits 0–9 with the units at the bottom, 40 discs per column. The columns are V₀, V₁, …. The **mill** is "that portion of the machine which works". To combine numbers, they are cleared from their columns (left as zeros), carried to the mill, and the result is sent to the indicated column.
- **Cards, after the Jacquard loom.** In the loom, a pasteboard card with holes lets some rods pass through and holds others back, and a series of cards hangs on a polygonal beam. The Engine has **Operation-cards** and **cards of the Variables**. The cards "possess all the generality of analysis, of which they are in fact merely a translation." The same cards serve every problem that differs only in its numbers, so the cards are "another form of analytical notation".
- **Contingencies.** If a quantity passes through zero or infinity, a bell rings and the machine stops for the attendant, or, if the case was foreseen, it brings up new cards. Computing abⁿ needs one multiplication card whatever n is.
- **Arranging the work.** A calculation must be arranged "conformably to the means which the machine possesses": what is easy for a human computer may be long for the engine, and the reverse. Interpreting formulas and results lies beyond the engine unless the interpretation can itself be put in its symbols. The engine is "not itself the being that reflects", but it executes "the conceptions of intelligence". Once it is built, making out the cards can go to a workman; the intellectual labor is preparing the formulas.
- **Advantages.**
  1. Rigid accuracy: no human intervention, and the engine prints its data so one can check that the question was posed correctly.
  2. Economy of time: two 20-figure numbers multiplied in at most three minutes, with several results at once for tables.
  3. Economy of intelligence: "a real manufactory of figures".

**Fig 3.1, the program for x in a two-equation linear system.** Columns V₀ = m, V₁ = n, V₂ = d, V₃ = m′, V₄ = n′, V₅ = d′ (V₆ and V₇ hold copies of n and n′).

| Op | Operation-card | Variable-cards | Result |
|---|---|---|---|
| 1 | × | V₂ × V₄ → V₈ | dn′ |
| 2 | × | V₅ × V₁ → V₉ | d′n |
| 3 | × | V₄ × V₀ → V₁₀ | n′m |
| 4 | × | V₁ × V₃ → V₁₁ | nm′ |
| 5 | − | V₈ − V₉ → V₁₂ | dn′ − d′n |
| 6 | − | V₁₀ − V₁₁ → V₁₃ | n′m − nm′ |
| 7 | ÷ | V₁₂ ÷ V₁₃ → V₁₄ | x = (dn′ − d′n)/(n′m − nm′) |

The columns of the table record the operation number, the Operation-cards (the nature of each operation), the Variable-cards (the columns operated on and the columns receiving results), and the progress of the work.

**Lovelace's Notes.**
- **Note A.** The Difference Engine tabulates functions whose seventh difference is zero, Δ⁷u_z = 0, with integral u_z = a + bz + cz² + … + gz⁶. It uses seven columns, for nautical and astronomical tables, and it prints its own results, but it is strictly arithmetical.

  The Analytical Engine is "the material expression of any indefinite function of any degree of generality and complexity", such as F(x, y, z, log x, sin y, x^p, …). It rests in a neutral state, ready to take the impress of a particular function from its cards, and it could tabulate Δⁿu_z = 0 for any n. The cards fix the operations, not the numbers.

  It could act "upon other things besides number" whose relations can be expressed by "the abstract science of operations". With pitched sounds, it "might compose elaborate and scientific pieces of music of any degree of complexity or extent". "The Analytical Engine weaves algebraical patterns just as the Jacquard-loom weaves flowers and leaves." It is a uniting link between matter and abstract mental process, and a "new, a vast, and a powerful language" for analysis.
- **Note B.** The **store** holds an indefinite number of columns, "probably at least two hundred" against the Difference Engine's seven. Each column has a top circle for the sign and a square below for the general symbol.

  Lovelace distinguishes **Variables** (capital V, a column of the engine) from the variables of a formula. A column is named for the fact that its value varies, not for any analytic distinction between constants and variables. Computing axⁿ with a = 5, n = 7, x = 98 takes six multiplications for 98⁷ and one more, written 7(×).

  Operation-cards put the mill into one state at a time (adding, multiplying), and it works on one pair of numbers at a time. Variable-cards are **Supplying-cards**, which "furnish the mill with its proper food", and **Receiving-cards**, which place results; Lovelace thinks *Distributive-cards* a better name for both. Fig 3.5 counts the operations: x^{an} is 34(×), a·n·x is 2(×), (a/n)·x is (÷, ×), and a + n + x is 2(+).

  The engine "separates those things which are in reality distinct and independent, and unites those which are mutually dependent."
- **Note C.** **Backing the cards.** The prism holding the cards can turn backward, bringing any card or set of cards into use any number of times. She proposes the same for weaving, to make symmetric patterns from few cards.
- **Note E.** The engine handles algebra, not only arithmetic. Its results are of three kinds: symbolic, numerical, and algebraical in literal notation. A **cycle** is "any set of operations which is repeated more than once"; twice counts. There are also **cycles of cycles**.
- **Note F.** A woven portrait of Jacquard took 24,000 cards. Arrange processes symmetrically and in cycles, so that backing can be used, and adjust the mathematical and mechanical departments to each other: a difficulty in one can be overcome by a facility in the other.

  Example: eliminating 9 variables from 10 equations. Eliminating x₀ between one pair of equations costs 10(×, ×, −). The total is 9·10 + 8·9 + … + 1·2 = 330, so "three Operation-cards would perform the office of 330 such cards". For n equations in n − 1 variables, the same three cards replace millions. The general formula need never be worked out; knowing the series of operations is enough.

  On the three-body problem: of about 295 coefficients of lunar perturbation computed by several astronomers, 14 differ in sign, and only 101, about a third, agree in both sign and amount. The engine would remove such errors.
- **Note G.** Guard against exaggeration. There is a tendency first to overrate a new invention, then by reaction to undervalue it. "The Analytical Engine has no pretensions whatever to originate anything. It can do whatever we know how to order it to perform. It can follow analysis; but it has no power of anticipating any analytical relations or truths." Its indirect influence lies in recasting analysis for the engine, which throws subjects into new lights.

**Led to.** Lewis calls the Analytical Engine the first device reasonably called a computer rather than a calculator, and Lovelace one of the first programmers. It was also "the first computer system pitched as almost operational that never worked properly".

Babbage's Difference Engine computed polynomial values by accumulating differences. For example, Σ_{i=0}^{n}(2i + 1) = (n + 1)², so it could make squares by adding successive odd numbers. Precision machining was not good enough to build the Analytical Engine. A Difference Engine was later completed using techniques developed for the failed design.

Lewis lists the firsts in this paper:
- compilation (Fig 3.1 is in effect an assembly-language compilation of an algebraic expression);
- step counting;
- loops controlled by an integer index;
- conditional branches and nested loops;
- accounting for code size;
- exception handling;
- mechanical solution of linear systems;
- the data/code dichotomy;
- nonnumeric computing;
- underestimating how hard programming is;
- hints of an undiscovered ontology of computations.

Lovelace "trod the spectacular wilderness of the field" on a path that was then lost until others followed. Aiken (7) came to think of himself as Babbage's heir. Turing (14) answers Note G as "Lady Lovelace's objection".

## 7. Aiken, *Proposed Automatic Calculating Machine* (1937)

**Set out to.** Show that scientific computation needs a machine different from punched-card accounting equipment, and specify one.

**The need.**
- New functions defined by infinite series are poorly tabulated.
- More accurate measurement means that small differences between computed and experimental results may reveal a new physical effect.
- Nonlinear devices such as the vacuum tube produce differential equations of no studied form, which must be attacked with series and numerical integration.
- Problems in the ionosphere, astronomy, relativity and mathematical economics are out of reach "not because of theoretical difficulties, but because of insufficient means of mechanical computation"; some ionospheric expressions are too long for a printed line.

**History.** Aiken traces pebbles, counters, the abacus, Napier's bones (1617), Pascal (1642, adding and subtracting), Morland (1666, multiplying by repeated addition), and Leibniz's stepped reckoner and pin wheel. Then come the slide rule (3–4 significant figures) and Babbage: the idea in 1812, a model in 1822, a government grant in 1823, and aid withdrawn in 1833 after nearly £20,000. Hollerith's punched cards led to IBM tabulating machinery. Commercial accounting made mechanical computation an economic necessity, but accounting machines do only the four operations and no algebra.

**Four features beyond accounting machines.**
1. Handle positive and negative quantities.
2. Supply and use transcendental functions (trigonometric, elliptic, Bessel, probability), selected by switches.
3. Run fully automatically once a process is set up, repeating it over equal steps of the independent variable.
4. Compute **lines instead of columns**. Accounting does step 1 for every x, then step 2. A differential equation needs each next value from the one before.

These four would convert IBM machines, with more arithmetic elements added.

**Operations wanted.** Arithmetic with signs and parentheses; integral and fractional powers; logarithms and exponentials; trigonometric, hyperbolic and inverse functions; superior transcendentals; and the evaluation and tabulation of formulas, series, first- and second-order ODEs, and numerical integration and differentiation of empirical data.

**Means.** Everything reduces to arithmetic. Signs are treated as numbers. Parentheses mean computing piecewise, which needs temporary storage in counters. Fractional powers come by Newton's iteration. For 5^{1/3}, take f(x) = x³ − 5:

  x_n = x_{n−1} − f(x_{n−1})/f′(x_{n−1}) = (2/3)x_{n−1} + 5/(3x_{n−1}²)

With x₀ = 2: x₁ = 4/3 + 5/12 = 21/12, and x₂ = 42/36 + (5 × 144)/(3 × 441) = 1.166 + 0.544 = 1.710, the cube root of 5 to four significant figures.

In general the r-th root of θ is x_n = (1 − 1/r)x_{n−1} + θ/(r·x_{n−1}^{r−1}), and non-integer r goes through a mechanical log table. Numerical integration by Simpson, Weddle or Gauss rules needs a list of numbers fed in mechanically. For differentiation by difference formulas, fifth differences are negligible with close observations, so a fifth-difference engine like Babbage's can be built from standard adding machines.

**The design reduces to control.** IBM machines already compute A + B = F, A − B = F, AB + C = F, AB + C + D = F, A + B + C = F, A − B − C = F and A + B − C = F from punched cards, rewired at a plugboard in minutes. The whole design problem "reduced to a problem of suitable control design": machine switching, with continuous perforated tape replacing cards and formulas punched as perforations.

**Apparatus (switchboard panels).**
- Power: 120 V ac motors and 32 V dc relays.
- **Master control**: deliver the number in position x to y and start the operation in y, with interlocks so that a number is not removed before it is determined and no operation starts before the last one finishes. There are four master controls, to combine for big problems or run several at once.
- Four devices stepping the independent variable, x₀ plus successive Δx.
- Permanent constants e, π and log₁₀ e, plus 24 adjustable constant positions.
- Two perforated-tape feeders for series values and one card magazine for empirical data.
- Twelve temporary storage positions.
- Four units each of add/subtract, multiply and divide.
- Permanent log, antilog, sin, cos, arcsin and arctan, and two Maclaurin series units.
- Accumulators up to fifth differences.
- Output: final results printed, intermediate results punched.

**Fig 7.1, products per hour by size of operands:** 2×8 digits 1500, 3×8 1285, 4×8 1125, 5×8 1000, 6×8 900, 7×8 818, 8×8 750. Ten-place logarithms run at about 90 an hour, so the logarithms of all numbers from 1000 to 100,000 take about 1100 hours, or 50 days.

**Accuracy.** Ten significant figures need 23 number positions: 10 left of the point, 12 right (two guard places thrown away), and one for the sign. Results are printed in tabular form for photolithography, with no typesetting or proofreading and so no transcription errors.

**Led to.** With IBM, the proposal became the Automatic Sequence Controlled Calculator, the Mark I, in service in 1944. It was about 50 feet long, 8 high and 3 deep, nearly 5 tons, with 530 miles of wire and thousands of relays. Its speeds:
- add or subtract 23 decimal digits in 0.3 s;
- multiply in up to 6 s;
- divide in up to 15.6 s;
- log x, eˣ or sin x in a minute or more.

That was enough for a dozen simultaneous linear equations of the kind Leontief's input-output economics needed.

The program was punched into a loop of paper tape, so the machine did repetitive operations only: no recursion, no nested loop, and as built no conditional branch. There was no stored program even in the Mark IV. It was programmable but "enjoyed nothing of what we know as software". The "Harvard architecture", with data and program in separate kinds of storage, left Aiken on an intellectual sidetrack. Yet "Aiken got the last laugh": most computers today are embedded, with programs frozen in firmware like the Mark I's tape loop.

Aiken found Babbage only after he had begun the design, and he knew nothing of Lovelace's programming or of Turing. The Introduction notes his dispute with IBM over whose machine it really was.

## 10. von Neumann, *First Draft of a Report on the EDVAC* (1945)

**Set out to.** Describe the logical control of a "very high speed automatic digital computing system". Such a system carries out instructions for calculations of considerable complexity, such as a nonlinear partial differential equation in two or three variables.
- The instructions must be given "in absolutely exhaustive detail", including all numerical information: initial and boundary values, constants and tables. They are given in a sensed form such as punched cards, teletype tape, magnetic wire, film or plugboards, and in a code covering both the logical and the numerical material.
- The device must then "carry them out completely and without any need for further intelligent human intervention".
- It produces far more numerical material internally than it outputs.
- Malfunction has a finite probability and any error may vitiate the whole output. So the device should recognize the commonest malfunctions, show where they are and stop, or else correct them and go on.

**Construct: the five parts.**
1. **CA**, the central arithmetical part, with organs for +, −, × and ÷. The list is not beyond doubt: one could add sgn, | |, log or sin, or drop ÷ and even ×, using successive approximation or function tables.
2. **CC**, the central control. An "elastic", all-purpose device must separate the specific instructions that define a problem, which are stored, from the general control organs that see they are carried out "no matter what they are". CC is the latter. C = CA + CC.
3. **M**, the memory, needed for:
   - (a) intermediate results within × and ÷;
   - (b) instructions, since "the code is circumstantial";
   - (c) function tables of 100–200 entries with interpolation (even a reciprocal table, which reduces ÷ to ×);
   - (d) initial and boundary conditions;
   - (e) results of cycle t needed for t + dt;
   - (f) constants and parameters;
   - (g) successive approximations;
   - (h) sorting and statistical experiments.

   It is "tempting to treat the entire memory as one organ, and to have its parts even as interchangeable as possible."
4. **I**, input, transfers everything from the outside recording medium **R** into M, never directly into C.
5. **O**, output, transfers from M into R, never directly from C.

CA, CC and M correspond to the associative neurons; I and O correspond to the sensory (afferent) and motor (efferent) neurons.

**Why M if R is a memory?** Items (b), (c), (e) and (g) could be sensed from R, but "a really high speed device would be very limited in its usefulness unless it can rely on M, rather than on R". The procedure of the report is a "somewhat zigzagging discussion": take up one part incompletely, pass to the next, and return with the combined results.

**Elements.** An **element** is relay-like, with discrete equilibria it holds indefinitely. It emits stimuli of the same kind it receives, and takes its energy from another source. Realizations include ten-position wheels, telegraph relays, vacuum tubes and the cathode ray tube. Timing is either **asynchronous**, set by the elements' own reaction times, or **synchronous**, set by a fixed clock such as a crystal-controlled oscillator; a clock is preferable when the design relies on simultaneous sequences staying in step.

Neurons are elements too, following McCulloch and Pitts (9): all-or-none, with excitatory and inhibitory synapses and a synaptic delay. Thresholds, temporal summation and the like are ignored, with occasional fixed thresholds of 2 or 3. "An element which stimulates itself will hold a stimulus indefinitely."

Reaction times:
- vacuum tube, about 1 microsecond (10⁻⁶ s);
- telegraph relay, about 10 ms (10⁻² s) or more;
- human neuron, about 1 ms (10⁻³ s).

The report assumes conventional commercial tubes.

**Binary.** A tube serves as an all-or-none gate, and a trigger circuit (flip-flop) has two equilibria. Elements with more equilibria are disproportionately complicated, so digits are two-valued and the system is binary. Binary also simplifies × and ÷, with no multiplication table: "Binary arithmetics has a simpler and more one-piece logical structure than any other, particularly than the decimal one." R stays decimal for human use; CA, CC and M are strictly binary, with conversion in I and O done by CA.

**Speed versus equipment.**
- Eight decimal digits means a relative rounding error under 10⁻⁸ ≈ 2⁻²⁷, so 27 binary digits. Multiplication takes about 27² = 729 steps, which collection of carries may double, so 1000–1500 steps.
- For relays (10 ms, the newest 5 ms) that is 10–15 s per multiplication, against 10 s for fast desk machines and 6 s for IBM multipliers.
- **Telescoping** helps relays: add all digit pairs at once, or form the partial products of a multiplication simultaneously and sum them pairwise in a tree, 5 addition times since 27 ≤ 2⁵ (a scheme due to Aiken). But such schemes "save time only at exactly the rate at which they multiply the necessary equipment"; an all-purpose relay system would need over 10,000 elements.
- For tubes the opposite holds. 1000–1500 reaction times is 1–1.5 ms, fast enough that the real problem is keeping the device in balance with human supervision at input and output. Addition takes about .03–.05 ms, division about as long as multiplication, and square root not much longer.
- **Principle:** "The device should be as simple as possible, that is, contain as few elements as possible. This can be achieved by never performing two operations simultaneously, if this would cause a significant increase in the number of elements required." Fewer elements mean more reliability and shorter reaction times. All earlier thinking went the other way, so it is instructive to think the opposite view through completely.

**E-elements.** For a first orientation, the report uses a hypothetical element that works like a vacuum tube. It is drawn as a circle receiving excitatory and inhibitory stimuli and emitting along a branching line after a synaptic delay t, the same for all elements; conduction delays are neglected. Unlike the nervous system, the delay is well defined and common to all, and serves as the absolute unit of time. A central clock emits a short standard pulse of length t′ every period t; stimuli are clock pulses gated by elements, so a stimulus is "completely renewed and synchronized after each step" (Fig 10.2).

**Memory and the word.** "The (capacity) unit of memory is the ability to retain the value of one binary digit." A standard number is 30 binary digits (rounding error under 2⁻³⁰ ≈ 10⁻⁹), plus a sign, plus one unit marking it a number rather than an order: 32 = 2⁵ units, a **minor cycle**. In delay-line memory, 32 minor cycles make a **major cycle**, held in one delay-line organ (DLA).

**Orders.** Orders come from M, the same place as numbers, so each minor cycle carries a mark saying which it is. Four classes:
- (a) CC instructs CA to carry out one of its operations.
- (b) Transfer a standard number. Transfers within M are routed through CA, so only M → CA and CA → M are needed.
- (c) Move CC's connection with M to a different point to get the next order.
- (d) Control input and output.

Normally CC obeys orders in the sequence they appear. A transfer is **transient** (return after one order) or **permanent** (continue from the new point). A transient transfer can be expressed by two permanent ones, so all transfers are permanent except number transfers.

**Code (Fig 10.3).** A minor cycle is I = (i₀, i₁, …, i₃₁). i₀ = 0 marks a standard number and i₀ = 1 an order. Digits are fed lowest place first, because carries propagate in time, with the sign last: i₃₁ = 0 is + and 1 is −, and the binary point follows the sign. The number is ξ = Σ_{ν=1}^{31} i_ν·2^{ν−31} (mod 2), with −1 ≤ ξ < 1. The orders are:
- **Nξ**: a standard number.
- **(α)**: carry out operation w in CA and dispose of the result.
  - Codes for w: + 0000, − 0001, × 0010, ÷ 0011, √ 0100, i 0101, j 0110, s 0111, db 1000, bd 1001 (db and bd convert decimal to binary and back).
  - Disposals: w → μρ sends the result to minor cycle ρ of major cycle μ; w → f to the minor cycle after the order; w → A into CA's input; h holds it in CA's output; no arrow means no disposal.
- **A ← μρ**: transfer the number in μρ into CA.
- **C ← μρ**: connect CC to minor cycle ρ of major cycle μ, that is, a jump.

**Led to.** This is the "von Neumann architecture", described but not named, with one memory holding both data and program. It has the logical structure of Turing's universal machine (6), a similarity Lewis calls "something of a coincidence"; the report cites McCulloch and Pitts, not Turing. Turing's ACE plan cites this report rather than his own work.

The design came from the Moore School group: Eckert, Mauchly, Burks and Goldstine, whose ENIAC was already computing ballistics. Goldstine typed von Neumann's memo and released it in 1945 under von Neumann's name alone: "the document was von Neumann's, but the design was the group's". The release invalidated Eckert and Mauchly's 1947 patents.

The revised *Preliminary Discussion* (Burks et al., 1946–47) added memory addresses ("location-numbers"), registers, floating point and hex digits A–F. Because programs are loaded and processed like data, a software industry became possible. Program was held in fast memory "simply so that successive instructions could be accessed at electronic speeds". Later versions dropped the neuronal discussion.

The Introduction says von Neumann is credited "too generously" for the stored program, which had many parents.

## 15. Wilkes, *The Best Way to Design an Automatic Calculating Machine* (1951)

**Set out to.** Make the design of a machine's control systematic instead of ad hoc, starting from reliability.

**Construct.**
- **Reliability** depends on the amount of equipment, its complexity, and the degree of repetition of units. **Complexity** is "the extent to which cross-connections between the various units obscure their logical interrelation"; simple connections are easier to repair and let different people build different units.
- **Repetition.** Five identical units are better than five different ones, and even six identical units beat five different ones. Wilkes conjectures that n different units are as desirable as kn identical ones for some k > 2, in a machine of about 10 groups with n ≈ 10.
- A **parallel machine** has a larger arithmetic unit, but one made of identical repeated units, and simpler control. Its standard unit is four flip-flops (one for each of four registers) plus an adder, with gates for transfers through the adder. Transfers happen by pulsing wires.
- **Control registers**, with Manchester and EDSAC names: next-order address (control, or sequence control tank); current order (current instruction register, or order tank); and a step counter for multiplication and shifts (timing control tank). Manchester also has B registers (index registers). With one B register, the same unit serves control and arithmetic, which is extreme repetition.

**Microprogramming.** Every machine operation is a sequence of steps: transfers between store and registers, or between registers. Each step is done by pulsing certain wires, and is a **micro-operation**. A machine operation is a **micro-programme** of micro-operations.

**Fig 15.1.**
1. A timing pulse enters a decoding tree, routed by the number in register R.
2. It reaches rectifier **matrix A**, whose output wires operate gates in the arithmetical unit and elsewhere. Each row of A is one **micro-order**.
3. It also reaches **matrix B**, which feeds back through a short delay line to R, changing its number and so selecting the next micro-order.
4. **Conditional micro-orders** branch the tree's output before matrix B, steered by a potential such as the accumulator's sign flip-flop.
5. To start an operation, the function digits of the order are set on the first four or five flip-flops of R and zeros on the rest.

**Results.** Nothing in the parts is new (flip-flops, gates, mixing diodes), and Wilkes grants it. Nor is the scheme extravagant: starting from the logical layout gives an arrangement that is both logical and economical, with the trade-off between logic and economy visible at every stage.

A simple machine needs only **40 micro-orders**. Its operations are add, subtract, multiply (two orders), right and left shift by any number of places, accumulator to store, conditionals on the sign of the accumulator and of the B register, store to B register, input and output, plus order extraction. Drawing up a micro-programme resembles ordinary programming. "The order code need not be decided on finally until a late stage in the construction of the machine; it would even be possible to change it after the machine had been put into operation simply by rewiring the matrices."

**Led to.** Wilkes attended the 1946 Moore School summer school and designed EDSAC (Electronic Delay Storage Automatic Calculator) on the voyage home; it was running in 1949. While designing its successor he hit on a primitive micro-instruction set, implementing machine instructions as micro-programs. In Wilkes's later words, this gave "the control unit the full flexibility of a programmed computer in miniature", and he imagined programmers choosing their own instruction sets. IBM's System/360 adopted microcode, which eased debugging and field modification of complex operations like multiplication. The flexible, hierarchical, updatable design became **firmware**. Wilkes also wrote an early programming textbook and won the Turing Award in 1967.

## 25. Moore, *Cramming More Components onto Integrated Circuits* (1965)

**Set out to.** Answer *Electronics* magazine's request for a ten-year prediction. "The future of integrated electronics is the future of electronics itself."

**Construct.** **Integrated electronics** covers all the microelectronic technologies plus any that supply "electronics functions supplied to the user as irreducible units". The approaches (microassembly, thin-film structures, semiconductor integrated circuits) were converging. ICs were nearly mandatory in new military systems; Apollo showed complete circuit functions as free of failure as the best single transistors.

Silicon is the basic material: its technology is built around it and its oxide, and it is abundant and cheap. Gallium arsenide is for integrated microwave work.

**Prophecies.**
- Home computers, "or at least terminals connected to a central computer".
- Automatic controls for automobiles.
- Personal portable communications equipment.
- The electronic wristwatch, which needs only a display.
- In large systems: telephone filters, switching and data processing. Computers would be organized completely differently, with memories distributed through the machine.

**Costs and curves.** For simple circuits, cost per component falls nearly in inverse proportion to the number of components. More components lower the yield and raise the cost, so there is a **minimum cost** at any given time.
- 1962: minimum near 10 components.
- 1965: minimum near 50 components.
- 1970 (projected): minimum near 1000 components, at a tenth of today's cost per component.

"The complexity for minimum component costs has increased at a rate of roughly a factor of two per year." The rate should hold, if not increase, and there is no reason it should not stay nearly constant for at least ten years. So by 1975 the number of components per IC at minimum cost will be **65,000**; "I believe that such a large circuit can be built on a single wafer."

The second graph plots log₂ of components per integrated function against year: 0 in 1959, about 3 in 1962, 4 in 1963, 5 in 1964 and 6 in 1965, with a dashed extrapolation to 16 in 1975.

**Two-mil squares.** Transistors can sit on centers two-thousandths of an inch apart. A two-mil square also holds several kilohms of resistance or a few diodes. That gives at least 500 components per linear inch, a quarter million per square inch, so 65,000 components fit in about a quarter of a square inch. Present optical techniques suffice.

**Yield.** "There is no fundamental obstacle to achieving device yields of 100%." Packaging costs far exceed those of the semiconductor structure, and there is no barrier like thermodynamic equilibrium in a chemical reaction. "Only the engineering effort is needed." The cartoon shows a store counter between NOTIONS and COSMETICS selling HANDY HOME COMPUTERS.

**Heat.** A shrunken standard computer would glow. But ICs are two-dimensional, so every heat source is near a cooling surface. Power goes mainly into driving lines and capacitances, and confining a function to a small area limits capacitance. Smaller dimensions give higher speed at the same power per unit area.

**Day of reckoning.** The question is when to build a large function. The aim is to minimize the total cost of a system function: either amortize engineering over many identical items, or develop flexible techniques for engineering large functions. "Design automation procedures could translate from logic diagram to technological realization without any special engineering." It may be cheaper to build large systems from smaller, separately packaged functions.

**Linear circuits** change less radically. Their greatest limitation is the lack of large capacitors and inductors, because stored energy needs volume. Moore expects crystal-stable oscillators from thermal feedback, lumped-parameter microwave design, and phased-array radar built from many integrated microwave sources.

**Led to.** The transistor, small, cool, reliable and frugal with power, replaced tubes in the mid-1950s and made switching computers like TX-2 possible. The real revolution, which no one saw coming, was miniaturization: whole circuits mass-produced by photolithography from the early 1960s. Moore was R&D director at Fairchild Semiconductor; he and Robert Noyce co-founded Intel in 1968.

The doubling time was later ramped to every two years. The prediction became a challenge, but it "certainly is not, and never has been, the 'law' that it was dubbed". It held for thirty or forty generations, until feature sizes approached molecules, and the "law" was then generalized to speed or computing capacity gained by other means. Moore was prescient about yield and about a consumer computer. On heat Lewis comments: "Heat became a problem because this premise ceased to be true."
