# Programming languages

Papers 16, 21, 29, 31 and 39: Hopper's compiling routines, McCarthy's LISP, Dijkstra's case against go to, Hoare's axioms, and Liskov and Zilles's abstract data types.

## 16. Hopper, *The Education of a Computer* (1952)

**Set out to.** "Replace, as far as possible, the human brain by an electronic digital computer" in the work of programming itself. Hopper builds on Aiken's library of routines, Mauchly's "short-order code" and Wilkes's book on subroutines.

**Construct: levels of education.**
- **An operation (Fig 16.1)**: INPUT → OPERATION → OUTPUT, with CONTROL above and TOOLS below, like a production line. Solving a problem has the same shape (Fig 16.2): PROBLEM → BRAIN → RESULTS, with the MATHEMATICIAN as control and FORMULAS and TABLES as tools.
- **The UNIVAC system (Fig 16.3)**: UNITYPER (typewriter input) → UNIVAC → UNIPRINTER, with a PROGRAM and UNISERVO tape drives.
- **Two levels (Fig 16.4).** At the first, the mathematician turned programmer uses formulas, tables and the code to produce a PROGRAM. At the second, UNIVAC runs it with its "standard knowledge" of elementary arithmetic and logic, designed in by engineers. When the novelty wears off, writing and checking programs is dull labor, and "vice-presidents and project directors" notice the cost.
- **Third level (Fig 16.5).** The mathematician writes **computer information** from a **catalogue** of subroutines. UNIVAC, under a **compiling routine of type A**, turns it into a PROGRAM, which then runs on the data. The programmer "may return to being a mathematician" and need not know the instruction code. Programming takes hours instead of weeks, without transcription errors or untested routines.
- **Fourth level (Fig 16.6).** Because computer information treats variables and constants symbolically, a **compiling routine of type B**, such as a differentiator, can derive the formulas for successive derivatives before type A builds the program. In Fig 16.7 only two components remain: the mathematician and the computer.
- **Two ways to use a subroutine:**
  1. The program refers to an available subroutine and continues, as in the interpretive "short-order code".
  2. The compiler looks the subroutine up and translates it, properly adjusted, into the program. The result runs as a unit and can itself go into the library as a more advanced subroutine.

**The catalogue and computer information.** Take y = e^{−x²} sin cx. Break it into steps: u = x², U = e^{−u}, v = cx, V = sin v, y = UV.

**Fig 16.9**, the computer information:

| Op | Call-number | Arguments | Results |
|---|---|---|---|
| 0 TRANSFER | b0i | input 0, 0.01, 0.99, 2, 5 | x, Δx, L_x, n, c |
| 1 xⁿ | apn | x, n | u = x² |
| 2 e^{−u} | x-e | u | U |
| 3 c⊗ | amc | c, x | v = cx |
| 4 sin v | ts0 | v | V |
| 5 ⊗ | am0 | U, V | y = UV |
| 6 EDIT | yrs | x, y | output x̄, ȳ |
| 7 ⊕→L ("add to a limit") | aaL | x, Δx, L_x | x + Δx → x |
| 8 STOP | ust | | |

Operation 7 continues at operation 1 if x < L_x and goes to 8 if x ≥ L_x. Operations are numbered in normal sequence, with an alternate destination ("go to operation k"). The compiler remembers where it placed each subroutine, or that a transfer to k was asked for, whether forward or backward.

Arguments and results are numbered as one list x_i in any order, with forgotten quantities added at the end (Fig 16.10): x = x₁, Δx = x₂, L_x = x₃, u = x₄, U = x₅, c = x₆, v = x₇, V = x₈, y = x₉, n = x₁₀.

**Call-numbers** are alphabetic and partly phonetic, after Wilkes. a is arithmetic, t trigonometric and x exponential; amc is multiplication by a constant, x-e is e^{−U}, and ts0 is the sine. n, f and s mean normal, floating and stated (fixed) decimal point. The catalogue lists each call-number with the order of its arguments, controls and results.

**Subroutines.**
- Each is coded relative to an entrance line numbered 001, for maximum accuracy and minimum time. It may store its own constants. **Permanent constants** (1/2π, π/4, log₁₀ e, ±0, .2, .5) sit in reserved memory and are never modified when the subroutine is positioned.
- A subroutine is preceded by its call-number, its arguments, non-modification indicators for embedded constants, and its results.
- The standard pattern: entrance line (line 1), normal exit line (line 2), alternate exit lines in catalogued order, then arguments, results and constants. The first action line comes after these, and no instruction may precede it.
- "The day may come when the elementary subroutines are rarely used and the computer information will contain but seven or eight items calling into play powerful subroutines."

**The compiling routine.** For each operation, type A:
1. locates the subroutine by call-number;
2. fabricates instructions to transfer its arguments;
3. adjusts the entrance and normal exit lines;
4. adjusts the alternate exit lines;
5. adjusts auxiliary entrance lines;
6. modifies all addresses in the subroutine;
7. leaves embedded constants unaltered;
8. fabricates instructions to transfer the results;
9. keeps a record of the program.

It also allocates temporary storage, program space and input/output. "Stated bluntly the compiling routine is the programmer and performs all those services necessary to the production of a finished program." Variants handle floating decimal, complex numbers and double precision. Type B uses **task routines** that replace or supplement the computer information: given f(x) and n, it produces f(x) and its first n derivatives.

**Advantages:**
1. memory allocation, address modification and transcription are relegated to the machine;
2. programming and transcription errors are removed;
3. programming time is conserved;
4. the "ability to operate on operations";
5. duplication is avoided, since each program may become a subroutine.

**Disadvantages:** duplicate data transfers (UNIVAC could produce the program and then eliminate the duplication), and missing subroutines must still be written.

**The future.** Type A for commercial programs. A routine that estimates magnitudes and running times to select subroutines. Sin θ and cos θ computed together, found by "sweeping the computer information once to examine its structure". Formulas in algebraic form, and "type C and D routines will be found to exist".

**The close.** Treat the professional programmer as part of the computer, and everything the programmer knows becomes available to it once translated. "UNIVAC at present has a well grounded mathematical education fully equivalent to that of a college sophomore, and it does not forget and does not make mistakes."

**Led to.** Hopper programmed Aiken's Mark I (7) and Mark II; the Mark II logbook records a moth in a relay as the "First actual case of a bug being found", though the term already existed. She saw that computing's future lay as much in business data processing as in science, and joined Eckert and Mauchly's company, whose machine was the UNIVAC.

In the 1940s there were no higher-level languages, parsers, compilers or debugging tools, and translation was done by hand. This paper marks the start of computers assisting programmers. Lewis finds in it, at least by allusion:
- compilers, including what are now linking loaders and code relocation;
- symbolic programming;
- optimization trade-offs;
- global program analysis;
- macro-assembly;
- formal specifications of subroutines;
- hierarchical program structure;
- the turn to commercial applications;
- the coming dominance of software cost over hardware.

The paper is "elaborately anthropomorphic". Its line between human and machine shifts as the computer's "education" advances.

Within a couple of years she led "automatic programming" at Remington Rand, producing ARITH-MATIC and MATH-MATIC, roughly the type A and type B routines. She was then the determined force behind COBOL (COmmon Business Oriented Language), against skepticism about English-like vocabulary and its cost in efficiency. The Introduction gives her argument that hardware would become the cheapest part, which made higher-level languages a necessity.

## 21. McCarthy, *Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I* (1960)

**Set out to.** Describe LISP (LISt Processor), built for the IBM 704 by the MIT artificial intelligence group. It was meant for experiments with the **Advice Taker**, a program instructed by declarative as well as imperative sentences and meant to show "common sense". The requirement was to manipulate expressions representing such sentences so as to make deductions. The paper simplifies this into a formalism for recursive functions of symbolic expressions, independent of the 704.

**Construct: preliminaries.**
- **Partial functions** are defined on only part of their domain, because a computation may not terminate.
- **Propositional expressions** take the values T and F, using ∧, ∨ and ∼ ((x < y) ∧ (b = c), "x is prime"). A **predicate** is a function with range {T, F}.
- **Conditional expressions**, "believed to be new": (p₁ → e₁, ⋯, p_n → e_n), read "if p₁ then e₁, otherwise if p₂ then e₂, …".

  The rule: examine the p's left to right. If a true p is met before any undefined p, the value is the corresponding e, if that is defined. If an undefined p comes first, or all the p's are false, or the chosen e is undefined, the expression is undefined.
  - (1 < 2 → 4, 1 ≥ 2 → 3) = 4.
  - (2 < 1 → 4, 2 > 1 → 3, 2 > 1 → 2) = 3.
  - (2 < 1 → 0/0, T → 3) = 3.
  - (2 < 1 → 3, T → 0/0) is undefined.
  - (2 < 1 → 3, 4 < 1 → 4) is undefined.
  - |x| = (x < 0 → −x, T → x); δ_ij = (i = j → 1, T → 0); sgn(x) = (x < 0 → −1, x = 0 → 0, T → 1).
- **Recursive definitions without circularity.**
  - n! = (n = 0 → 1, T → n·(n − 1)!). For 0! the meaningless 0·(0 − 1)! never arises.
  - gcd(m, n) = (m > n → gcd(n, m), rem(n, m) = 0 → m, T → gcd(rem(n, m), m)).
  - sqrt(a, x, ε) = (|x² − a| < ε → x, T → sqrt(a, ½(x + a/x), ε)), Newton's method.

  Termination is not guaranteed; a nonterminating computation is undefined.
- **Connectives as conditionals:** p ∧ q = (p → q, T → F); p ∨ q = (p → T, T → q); ∼p = (p → F, T → T); p ⊃ q = (p → q, T → T). With undefined values, ∧ and ∨ are not commutative: if p is false and q undefined, p ∧ q is false but q ∧ p is undefined. That is desirable, since q is never computed when p is false.
- **Functions and forms.** y² + x is a **form**, not a function: applied to (3, 4) it could be 13 or 19. Church's **λ-notation** λ((x₁, ⋯, x_n), ℰ) makes the function, so λ((x, y), y² + x)(3, 4) = 19. Bound variables are dummies, so λ((u, v), v² + u) is the same function. A notation that tells functions from forms allows functions of functions.

**S-expressions.**
- The characters are `.`, `(` and `)`, plus an infinite set of **atomic symbols**, such as A, ABA and APPLE PIE NUMBER 3.
- Definition: (1) atomic symbols are S-expressions; (2) if e₁ and e₂ are S-expressions, so is (e₁ · e₂). Examples: AB, (A · B), ((AB · C) · D).
- A **list** (m₁, m₂, ⋯, m_n) stands for (m₁ · (m₂ · (⋯(m_n · NIL)⋯))), where NIL is the atomic symbol that ends lists. (m) abbreviates (m · NIL), and (m₁, ⋯, m_n · x) abbreviates (m₁ · (⋯(m_n · x)⋯)).
- So ((AB, C), D) is ((AB · (C · NIL)) · (D · NIL)), and ((A, B), C, D · E) is ((A · (B · NIL)) · (C · (D · E))).

**M-expressions** (meta-expressions) use lower-case names, brackets and semicolons, as in car[cons[(A · B); x]]. S-expressions inside them stand for themselves.

**Elementary S-functions and predicates.**
1. atom[x] is T iff x is atomic: atom[X] = T; atom[(X · A)] = F.
2. eq[x; y] is defined only for atoms and is T if they are the same symbol: eq[X; X] = T; eq[X; A] = F; eq[X; (X · A)] is undefined.
3. car[(e₁ · e₂)] = e₁, defined only for non-atoms: car[(X · A)] = X; car[((X · A) · Y)] = (X · A).
4. cdr[(e₁ · e₂)] = e₂: cdr[(X · A)] = A; cdr[((X · A) · Y)] = Y.
5. cons[e₁; e₂] = (e₁ · e₂), defined for anything: cons[X; A] = (X · A).

They satisfy car[cons[x; y]] = x, cdr[cons[x; y]] = y, and cons[car[x]; cdr[x]] = x for non-atomic x. Compositions alone are "quite limited and not very interesting". With conditional expressions and recursion they give "a much larger class of functions (in fact, all computable functions)". For example, ff[x], the first atomic symbol ignoring parentheses, is ff[x] = [atom[x] → x; T → ff[car[x]]], and ff[((A · B) · C)] = A.

**The universal S-function apply.** If f is the S-expression for an S-function f′, then apply[f; args] and f′[arg₁; ⋯; arg_n] are defined for the same arguments and are equal. It "plays the theoretical role of a universal Turing machine and the practical role of an interpreter". Example:

  λ[[x; y]; cons[car[x]; y]][(A, B); (C, D)] = apply[(LAMBDA, (X, Y), (CONS, (CAR, X), Y)); ((A, B), (C, D))] = (A, C, D).

**Functions as arguments.** maplist[x; f] = [null[x] → NIL; T → cons[f[x]; maplist[cdr[x]; f]]].

Differentiation works on expressions built from atoms, (PLUS, e₁, ⋯, e_n) and (TIMES, e₁, ⋯, e_n). This is essentially Polish notation, with parentheses and commas allowing any number of arguments, so (TIMES, X, (PLUS, X, A), Y) is X(X + A)Y.

  diff[y; x] = [atom[y] → [eq[y; x] → ONE; T → ZERO];
   eq[car[y]; PLUS] → cons[PLUS; maplist[cdr[y]; λ[[z]; diff[car[z]; x]]]];
   eq[car[y]; TIMES] → cons[PLUS; maplist[cdr[y]; λ[[z]; cons[TIMES; maplist[cdr[y]; λ[[w]; [∼eq[z; w] → car[w]; T → diff[car[w]; x]]]]]]]]]

The last clause is the product rule. Applied to X(X + A)Y with respect to X it gives (PLUS, (TIMES, ONE, (PLUS, X, A), Y), (TIMES, X, (PLUS, ONE, ZERO), Y), (TIMES, X, (PLUS, X, A), ZERO)).

**The LISP system** is used for a LISP compiler, a proof checker, formal differentiation and integration, proof generation in the predicate calculus, engineering calculations whose results are formulas, and the Advice Taker.

**List structure.** A word is drawn as a rectangle divided into an address field and a decrement field, with arrows showing which locations it contains. Fig 21.1 shows (a) a tree, (b) shared substructure, which is permitted, and (c) a cycle, which is not. A non-atomic x is a word whose address and decrement parts hold the locations of car[x] and cdr[x]. An atomic symbol is a list of special form, its association list.

List structure has three advantages:
1. The size and number of expressions are unpredictable, which makes fixed blocks hard to allocate.
2. Freed registers return to a free-storage list, where even one is useful; with linear storage, odd-sized blocks are hard to reuse.
3. A shared subexpression is stored once.

**Free storage and reclamation.** Unused registers, about 15,000 at first, form one list whose head is in register FREE; taking a word advances FREE. The user never returns registers; reclamation is automatic.

A register is **accessible** if it can be reached from a fixed set of base registers by a chain of car and cdr. When a base register changes, a register may become unreachable, "abandoned by the program". Nothing happens until free storage runs out. Then a reclamation cycle runs:
1. Starting from each base register, make negative the sign of every register reachable by a car-cdr chain; a register already negative has already been reached.
2. Sweep the list area, return the registers whose signs are unchanged to the free list, and make the accessible ones positive again.

This is more convenient than having the programmer track and erase unwanted lists. Its efficiency depends on accessible lists not nearly exhausting memory: reclamation takes several seconds and must recover at least several thousand registers.

**Led to.** McCarthy named the field at the 1956 Dartmouth summer school on "Artificial Intelligence", proposed with Shannon, Minsky and Rochester. The proposal's seven topics are all still active research problems:
- automatic computers;
- how a computer can be programmed to use a language;
- neuron nets;
- the theory of the size of a calculation;
- self-improvement;
- abstractions;
- randomness and creativity.

His "audacious move" was to borrow directly from Church's lambda calculus, which had been built to resolve the Entscheidungsproblem (6). LISP was purely interpretive at first, with compilers years later. He invented **garbage collection** (Lewis's term for "reclamation") so that even small programs could run on memory-limited machines. He helped design ALGOL 60, the first widely used general-purpose language with recursion, and LISP influenced every later functional language. At MIT he was instrumental in the birth of time-sharing (23), and he founded the Stanford AI Laboratory in 1962. The Introduction credits him with taking symbol manipulation as primitive and putting recursion at the center of programming.

## 29. Dijkstra, *Go To Statement Considered Harmful* (1968)

**Set out to.** Argue that "the quality of programmers is a decreasing function of the density of go to statements in the programs they produce", and that go to should be abolished from all "higher level" programming languages, that is, everything except perhaps plain machine code.

**Construct.**
- **First remark.** The programmer's activity ends with a correct program, but "the process taking place under control of his program is the true subject matter of his activity." It is the process that is delegated to the machine.
- **Second remark.** "Our intellectual powers are rather geared to master static relations and … our powers to visualize processes evolving in time are relatively poorly developed." So we should shorten the conceptual gap between the static program, spread out in text space, and the dynamic process, spread out in time, making the correspondence as trivial as possible.
- **Characterizing the progress of a process.** If a process stops after some arbitrary action, what data must we fix to redo it to the very same point?
  - With a pure concatenation of assignments, a point in the program text suffices: the **textual index**.
  - Conditionals (if B then A), alternatives (if B then A1 else A2), Hoare's case[i] of (A1, A2, …, An), and McCarthy's conditional expressions (B1 → E1, …, Bn → En) all keep a single textual index.
  - With procedures, progress is a sequence of textual indices whose length is the dynamic depth of procedure calls.
  - Repetition clauses (while B repeat A; repeat A until B) are logically superfluous, given recursion, but realistic. Each entry adds a **dynamic index** counting the ordinal number of the current repetition. With nesting, progress is a mixed sequence of textual and dynamic indices.
  - These values are outside the programmer's control: they are **independent coordinates** of the process's progress.
- **Why we need them.** "We can interpret the value of a variable only with respect to the progress of the process." If n counts the people entering an initially empty room, then between seeing someone enter and incrementing n, n equals the number of people in the room minus one.

**Result.** With unbridled use of go to, it becomes terribly hard to find a meaningful set of coordinates. The values of variables cannot serve, since their meaning depends on progress. A counter of actions since the start, a normalized clock, is unique but "utterly unhelpful": at what count is n the number in the room minus one? "The go to statement as it stands is just too primitive; it is too much an invitation to make a mess of one's program." The clauses bridle its use. Any new clause, an abortion clause for example, must preserve "a programmer independent coordinate system".

**Credits.** Dijkstra cites Peter Landin and Christopher Strachey, and Heinz Zemanek, who doubted at a pre-ALGOL meeting in Copenhagen in early 1959 whether go to deserved equal syntactic footing with assignment. Restricting go to to alarm exits was presumably Hoare's suggestion. Wirth and Hoare (1966) said the case construction "mirrors the dynamic structure of a program more clearly than go to statements and switches". Böhm and Jacopini (1966) proved go to logically superfluous, but mechanically translating a flow diagram into jumpless form is not recommended, since the result is no more transparent.

**Led to.** Structured programming grew from several pressures. Better compilers made tricky code less necessary, bigger systems needed comprehensible modular code, and by 1968 machines supported recursion and while loops were common, with Wirth designing PASCAL. The letter was less a scientific contribution than a summary of a movement plus a call to action. Its effect was profound: "structured programming" appeared in hundreds of titles over the next decade.

Knuth (1974) showed that some things are easier with go to, and that structured programming could coexist with it. Still, Dijkstra's argument won. It shifted teaching and set minimum conditions on linguistic structures. The title "considered harmful" was not Dijkstra's: Wirth, as editor, supplied it for a note originally called "A Case Against the GOTO Statement", using what was already a journalistic convention. Liskov and Zilles (39) carried the program from control to data.

## 31. Hoare, *An Axiomatic Basis for Computer Programming* (1969)

**Set out to.** Lay logical foundations for programming by the method first applied in geometry: axioms, and rules of inference for proving properties of programs. "Computer programming is an exact science in that all the properties of a program and all the consequences of executing it in any given environment can, in principle, be found out from the text of the program itself by means of purely deductive reasoning."

**Computer arithmetic (Fig 31.1):**
- A1 x + y = y + x
- A2 x × y = y × x
- A3 (x + y) + z = x + (y + z)
- A4 (x × y) × z = x × (y × z)
- A5 x × (y + z) = x × y + x × z
- A6 y ≤ x ⊃ (x − y) + y = x
- A7 x + 0 = x
- A8 x × 0 = 0
- A9 x × 1 = x

A theorem: y ≤ r ⊃ r + y × q = (r − y) + y × (1 + q). Proof: (r − y) + y × (1 + q) = (r − y) + (y × 1 + y × q) by A5, = (r − y) + (y + y × q) by A9, = ((r − y) + y) + y × q by A3, = r + y × q by A6, provided y ≤ r.

A1–A9 hold for the infinite integers and for nonnegative finite computer "integers", whatever the overflow technique. There are three such techniques:
1. **Strict interpretation**: an overflowing result does not exist and the program never completes.
2. **Firm boundary**: the result is the maximum value.
3. **Modulo arithmetic**: the result is taken modulo the size of the set.

Fig 31.2 tabulates the three for a machine with only 0, 1, 2 and 3. In modulo arithmetic, for instance, 2 + 2 = 0, 3 + 3 = 2, 2 × 2 = 0 and 3 × 3 = 1.

Supplementary axioms tell the models apart:
- infinite: ¬∃x ∀y (y ≤ x) (A10_I);
- finite: ∀x (x ≤ max) (A10_F);
- strict: ¬∃x (x = max + 1) (A11_S);
- firm boundary: max + 1 = max (A11_B);
- modulo: max + 1 = 0 (A11_M).

A property proved with a chosen axiom holds only on an implementation that satisfies it.

**Construct: P {Q} R.** "If the assertion P is true before initiation of a program Q, then the assertion R will be true on its completion." With no precondition, write true {Q} R. The notation is essentially Floyd's (1967), applied to program texts rather than flowcharts.

- **D0 Axiom of Assignment.** Assignment is "the most characteristic feature of programming a digital computer", yet its axiom is as simple as any in elementary logic. For x := f, where x is a simple variable and f an expression without side effects:

  ⊢ P₀ {x := f} P,

  where P₀ is P with f substituted for every occurrence of x. Whatever is true of x afterward must have been true of f before. It is an axiom schema, purely syntactic and easy to check.
- **D1 Rules of Consequence.** If ⊢ P{Q}R and ⊢ R ⊃ S, then ⊢ P{Q}S. If ⊢ P{Q}R and ⊢ S ⊃ P, then ⊢ S{Q}R.
- **D2 Rule of Composition.** If ⊢ P{Q₁}R₁ and ⊢ R₁{Q₂}R, then ⊢ P{(Q₁; Q₂)}R. Longer sequences nest, and the brackets drop by associativity.
- **D3 Rule of Iteration.** If ⊢ P ∧ B {S} P, then ⊢ P {while B do S} ¬B ∧ P. If S preserves P, then P holds after any number of iterations, even none; B is false on termination; and B may be assumed true at the start of S.

**Example.** Find the quotient q and remainder r of x by y by successive subtraction:

  ((r := x; q := 0); while y ≤ r do (r := r − y; q := 1 + q))

The property to prove is true {Q} ¬y ≤ r ∧ x = r + y × q. That is "a necessary (but not sufficient) condition for the 'correctness' of the program". The invariant is x = r + y × q, and the theorem above carries it through the loop body. "Like all formal proofs, it is excessively tedious." Notational conventions and derived rules shorten it, until "a 'formal proof' reduces to little more than an informal indication of how a formal proof could be constructed."

**Reservations.**
- Expressions are assumed to have no side effects.
- There is no basis for proving termination, so P{Q}R means "provided that the program successfully terminates, the properties of its results are described by R". Better to prove this conditional correctness and rely on the implementation to warn when it abandons execution.
- Not yet covered: real arithmetic, bits and characters, arrays, records, files, input/output, declarations, subroutines, parameters, recursion and parallel execution. The real difficulty lies in labels and jumps, pointers and name parameters.

**Why it matters.**
- **Correctness.** A program's most important property is that it accomplishes the user's intentions, and those can be stated as assertions. If the compiler and hardware are proved too, confidence is "limited only by the reliability of the electronics".

  Present practice is to test cases, modify, and believe. Testing often takes more than half a project's time, and with machine time costed realistically, removing errors is two-thirds or more of the cost. The cost of an error in use can be "almost incalculable—a lost spacecraft, a collapsed building, a crashed aeroplane, or a world war".
- **Documentation.** Assertions before and after a subroutine are the most rigorous statement of its purpose, and its proof serves as a lemma for its callers. "The structure of the whole can be clearly mirrored in the structure of its proof." A proof explains not only what a program does but why.
- **Portability.** Machine-dependent features show up as failures to prove from machine-independent axioms. A deliberately machine-dependent program quotes the axiom it relies on, such as a version of A11, as a precondition.
- "Reliability can be purchased only at the price of simplicity."
- **Formal language definition.** Implementations should "satisfy" the axioms and rules, "accepting the axioms and rules of inference as the ultimately definitive specification of the meaning of the language". The axioms deliberately leave some things undefined, such as the range of integers and the overflow technique; a standard is the universal axioms plus a choice of supplementary ones. A language described by a few "self-evident" axioms is preferable to one needing many obscure ones.

**Led to.** Hoare formalized Dijkstra's insistence that programming is mathematical reasoning. He fulfilled McCarthy's call (1963): "Instead of debugging a program, one should prove that it meets its specifications, and this proof should be checked by a computer program." He had read Floyd's *Assigning Meanings to Programs*, which put invariant predicates on the edges of flowcharts; Hoare dropped the flowchart and attached invariants to statements. Quicksort (1962) was a byproduct of ALGOL 60, whose easy recursion made the algorithm's structure apparent.

Formal verification has had ups and downs. It is now standard for low-level code, but its more ambitious forms excited antipathy, as in DeMillo, Lipton and Perlis (44). Hoare later conceded that formal-methods researchers, "and I was the most mistaken among them", expected the programming world to embrace formalization gratefully. Failures came instead from inadequate requirements analysis or management control, and "the world just does not suffer significantly from the kind of problem that our research was originally intended to solve." He won the Turing Award in 1980.

## 39. Liskov and Zilles, *Programming with Abstract Data Types* (1974)

**Set out to.** Very-high-level languages ease programming by supplying abstractions suited to a problem area, but no designer can select all the abstractions in advance. The authors propose letting the built-in abstractions be augmented whenever a new data abstraction is discovered.

Structured programming already works this way. The programmer first writes the program for an abstract machine with exactly the data objects and operations the problem needs, and proves it correct using those abstractions. Then each abstraction becomes a new problem to realize, possibly introducing further abstractions, until all are realized. A language that supports this is "a general-purpose, indefinitely-high-level language."

**Construct.**
- An **abstraction** is "a mechanism which permits the expression of relevant details and the suppression of irrelevant details". Procedures abstract function well, but they are not a rich enough vocabulary: the data objects of an abstract machine are not accurately represented by independent procedures.
- **Definition:** "An abstract data type defines a class of abstract objects which is completely characterized by the operations available on those objects."
  - Users care only about behavior; the storage representation matters only to whoever implements the operations.
  - As with built-in types like integer, users create objects and apply operations to them. The operations are indivisible and atomic, objects cannot be decomposed, and misuse is caught by strong typing.
  - An abstract type is realized by an **operation cluster** that defines it in terms of its operations.
- A **functional abstraction** is an abstract operation outside any characterizing set, implemented by composing the characterizing operations of one or more types, as a sine routine composes real arithmetic.

**The language**, a simplified form of CLU, derived mainly from PASCAL.
- Two kinds of module, **procedures** and **clusters**, each compiled separately.
- The only free names are module names, bound at translation through a directory the programmer creates.
- Control is structured only: concatenation, if, case and while, with no go to or labels. Error handling is still being designed and is represented by `error`.

**Example: Polish_gen** converts infix to Polish postfix under an operator-precedence grammar; a + b * (c + d) becomes a b c d + * +.

```
Polish_gen: procedure(input: infile, output: outfile, g: grammar);
  t: token; mustscan: boolean; s: stack(token);
  mustscan := true;
  stack$push(s, token(g, grammar$eof(g)));
  while ¬stack$empty(s) do
    if mustscan then t := scan(input, g) else mustscan := true;
    if token$is_op(t) then
      case token$prec_rel(stack$top(s), t) of
        "<":: stack$push(s, t);
        "=":: stack$erasetop(s);
        ">":: begin outfile$out_str(output, token$symbol(stack$pop(s)));
                    mustscan := false end
      otherwise error;
    else outfile$out_str(output, token$symbol(t));
  end
  outfile$close(output);
  return;
end Polish_gen
```

How it works:
- An identifier goes straight to output.
- An operator is compared with the top of the stack. "<" pushes it (as "+" < "*"). "=" discards both (as "(" = ")"). ">" outputs the top operator and sets mustscan false, so that the same t is compared with the new top.
- A grammar-dependent eof token is pushed first, so the stack empties only when input is exhausted.

The procedure relies on five data abstractions (infile, outfile, grammar, token, stack) and one functional abstraction (scan). Its knowledge of files "consists of the names of the operations which provide these services."

**Declarations and calls.**
- `t: token` names a variable without creating an object. Parentheses after a type name create one: `s: stack(token)` makes a stack whose element type is token.
- An object may be used in only three ways: operated on by its type's operations, passed as a parameter of identical type, or assigned to a variable of its type.
- Operations are called by compound names, type then operation, as in `stack$push(s, t)`. This resolves ambiguity among parameters of different types, lets different types reuse operation names, and makes calls distinguishable from procedure calls.

**scan (Fig 39.2)** reads a character, skips blanks, and returns the eof token at end of file. Otherwise it builds the symbol, a single non-alphanumeric character or a run of alphanumerics, and returns token(g, newsymb). Token is "a type introduced to provide efficient execution without revealing information about how the grammar represents symbols."

**Defining a type: the stack cluster (Fig 39.3).**

```
stack: cluster(element_type: type) is push, pop, top, erasetop, empty;
  rep(type_param: type) = (tp: integer; e_type: type; stk: array[1..10] of type_param);
  create
    s: rep(element_type);
    s.tp := 0; s.e_type := element_type;
    return s;
  end
  push: operation(s: rep, v: s.e_type); s.tp := s.tp + 1; s.stk[s.tp] := v; return; end
  pop: operation(s: rep) returns s.e_type;
    if s.tp = 0 then error; s.tp := s.tp − 1; return s.stk[s.tp + 1]; end
  top: operation(s: rep) returns s.e_type; if s.tp = 0 then error; return s.stk[s.tp]; end
  erasetop: operation(s: rep); if s.tp = 0 then error; s.tp := s.tp − 1; return; end
  empty: operation(s: rep) returns boolean; return s.tp = 0; end
end stack
```

The reserved word *is* "underlines the idea of a data type being characterized by a group of operations." A cluster has three parts:
- **The rep.** The figure prints the array as [1..10]; the text describes stk as an unbounded array. The rep defines a type accessible only inside the cluster, a template for building and decomposing objects. Users see objects as indivisible; inside the cluster they can be taken apart.
- **The create code.** Declaring `s: stack(token)` runs it at execution time. Because there are no free variables, cluster parameters must be stored in each rep instance, which is why e_type is kept. On return the type changes from rep to the abstract type.
- **The operations.** Each takes at least one rep parameter. They can be called only through the cluster, and a passed object's type changes from abstract to rep. Strong typing checks a pushed object against the stack's e_type at run time.

**Controlling information.** Since users cannot reach implementation details, programs are "more modular, and easier to understand, modify, maintain and prove correct."

The token type shows why. Comparing strings through grammar$prec_rel is slow; looking an operator up once and using its index into the precedence matrix is fast, but exposes the grammar's representation, inviting the maintenance errors Parnas warned of. The token cluster confines that knowledge. A change to the grammar affects only token, and an index-out-of-bounds error can come only from token or grammar.

The representation of tokens is a decision delayed until the cluster is written, after Dijkstra's principle "build the program one decision at a time". Proof divides in two: show that the cluster implements the type, and show that the program is correct using only the type's abstract properties.

**Led to.** In the "software crisis" of the late 1960s and 1970s, ambitions grew extravagant, bugs subtler, and multimillion-dollar systems were discarded. The response was to manage complexity by constraining programmers' freedom of expression, along two paths:
- the control of program flow: go to (29) and structured programming;
- the manipulation of data, through conventions that let a program express "only of the minimum necessary functional operations on data, not the internal structure of the data".

This paper is an early exemplar of the second. Very high-level languages are now standard, and object-oriented programming traces its roots here. Liskov earned one of the first computer science PhDs awarded to a woman, under McCarthy (21), and won the Turing Award in 2008, partly for data abstraction.
