# Logic and computability

Papers 1, 2, 4, 5, 6 and 8: from Aristotle's deduction by form, through Boole's algebra of logic and Hilbert's demand for decision procedures, to Turing's machine and Shannon's switching algebra.

## 1. Aristotle, *Prior Analytics* (∼350 BCE)

**Set out to.** Lay down the first system of logic: conclusions drawn from premises by their **form** alone, with no appeal to persuasiveness or to anything outside the premises. Lewis calls Aristotle "the great systematizer". The Greek συλλογισμός means "reckoning up" or "computation"; *syllogism* has since narrowed.

**Construct.**
- A **premise** is "a sentence affirming or denying something about something". It is **universal** ("to every", "to none"), **particular** ("to some", "not to some", "not to every") or **indeterminate**. A demonstrative premise takes one side of a contradiction as true; a dialectical premise asks which side holds.
- A **term** is what a premise breaks into: predicate and subject.
- A **deduction** is a discourse in which, certain things being supposed, something different from them "results of necessity because these things are so", needing no term from outside. It is **complete** when nothing beyond what was taken is needed for the necessity to be evident, and **incomplete** when further things are needed that follow from the terms but were not taken as premises. Demonstration is one kind of deduction; deduction is the more universal.
- For one thing "to be in another as a whole" is the same as for it to be "predicated of every" one of another.
- Premises can be about belonging, belonging of necessity, or possibly belonging.

**Conversion rules.**
- A universal privative converts: if no pleasure is good, no good is pleasure.
- A universal positive converts only partially: if every pleasure is good, some good is pleasure.
- A particular affirmative converts.
- A particular privative need not: man belongs not to some animal, yet animal belongs to every man.

**The first figure.** Of three terms, the **middle** is in another and has another in it. The **major extreme** is the one the middle is in; the **minor extreme** is under the middle.
- Every B is A and every C is B ⇒ every C is A.
- No B is A and every C is B ⇒ no C is A.
- A to every B and B to some C ⇒ A to some C.
- A to no B and B to some C ⇒ A not to some C.
- An indeterminate positive BC works the same as a particular one. The universal premise must go with the major extreme and the particular positive with the minor.

**Counterexample terms** show that a premise pattern yields nothing. Suppose the first term belongs to all of the middle and the middle to none of the last. With animal, man, horse the first term then belongs to every last; with animal, man, stone it belongs to none. Since both outcomes occur, no conclusion follows. Science, line, medicine against science, line, unit does the same job for another pattern.

**Led to.** In set terms, a predicate is membership and "belonging" is the subset relation: A ⊇ B and B ⊇ C ⇒ A ⊇ C is transitivity, and "A belongs to none of the Bs" says A and B are disjoint. Aristotle was the first to abstract the form of an argument from its content, so that reasoning becomes matching propositions to templates. Lewis calls the counterexample technique "the method used to this day to refute conjectures and to prove the independence of hypotheses". Two-valued logic underlies digital computing. Variables standing for any property make a computer general-purpose: the same bit can stand for a knight on f3 in one program and a book in stock in another.

## 2. Leibniz, *The True Method* (1677)

**Set out to.** Explain why demonstration has succeeded only in mathematics, and propose to carry its method into every field of reasoning.

**Construct.** Mathematics "carries its own test with it". A false theorem shows itself through a calculation that costs nothing but ink and paper. Such tests are made on the **characters** substituted for things, not on the things themselves:
- casting out nines (a check of divisibility by 9 using digit sums);
- Ludolph's computation of the circle (Lewis: Aristotle had a 96-gon for π, and Ludolph van Ceulen used a 2^62-gon to reach 35 places);
- tables of sines.

For example, 1677 × 365 = 612,105 is checked on paper rather than by piling up 365 heaps of 1677 stones. Other fields fail for two reasons: their steps are slippery, and they lack easy tests anyone can perform.

**The proposal.** Suppose we found characters that express all our thoughts as exactly as arithmetic expresses numbers. Then in every matter open to reasoning we could do what is done in arithmetic and geometry, by transposing characters and "a kind of calculation". Disputes would end by repeating the calculation: "Let us calculate, Sir."

**The limit** Leibniz always attaches: this holds only insofar as reasoning can go, from the given facts. Experiment supplies the facts. Reason draws out everything they imply and identifies which experiments remain. Where the facts cannot support an infallible judgment, reason determines "what is most probable from the given facts. And that is all reason can do."

The characters would form a language "very difficult to construct but very easy to learn". Only calculation or grammar errors would be possible in it, and equivocations would vanish. It would silence the ignorant, because no one could speak beyond what they understood without the vanity being obvious. Leibniz calls it an instrument to exalt reason as the telescope perfects vision. He first had the thought at eighteen.

**Figure 2.1** (from *De progressione dyadica*, 1679): binary arithmetic. 1011000 = 2^6 + 2^4 + 2^3 = 64 + 16 + 8 = 88, and the binary sum 001011 + 110101 = 1000000.

**Led to.** Lewis puts Leibniz "in the running for the title of first computer scientist". He built a calculator that multiplied and divided by nested loops, invented binary arithmetic, and designed a binary calculator that was never built. His *dx* notation survives because it makes rules like the chain rule easy to apply mechanically, unlike Newton's dots; he "recognized how good notation can contribute to clear thought." His thesis (1666) systematized logic for legal reasoning. Voltaire's Pangloss mocked the grand plan. The logical reductionism returns in McCulloch and Pitts (9), Bush (11), and "every automated decision support system".

## 4. Boole, *The Laws of Thought* (1854)

**Set out to.** "Investigate the fundamental laws of those operations of the mind by which reasoning is performed", express them in the symbolic language of a calculus, found logic and its method on that calculus, and make it the basis of probability.

**Construct.**
- "Language is an instrument of human reason, and not merely a medium for the expression of thought."
- A **sign** is "an arbitrary mark, having a fixed interpretation, and susceptible of combination with other signs in subjection to fixed laws dependent upon their mutual interpretation." What a sign means does not depend on its form.
- Every operation of language as an instrument of reasoning uses three things: **literal symbols** x, y for things as subjects of conception; **signs of operation** +, −, × for the mental operations that combine or separate conceptions; and the **sign of identity** =.

**Class I signs (appellative).** A letter x stands for a class, such as "men". A class may also be a single individual, **Nothing**, or the **Universe**. xy is the class to which both x and y apply (white sheep), and zxy adds a third quality (horned white sheep).
- (4.1) xy = yx. This is "a law of thought, and not, properly speaking, a law of things"; the freedom of word order in language shows it.
- (4.2) xx = x, that is, x² = x, the **index law**. "Good, good men" means good men; repetition for emphasis has no logical force.

**Class II signs** collect parts into a whole or separate them: "and" and "or" become +, and "except" becomes −. In strict use the parts joined must be distinct classes.
- x + y = y + x.
- (4.3) z(x + y) = zx + zy.
- "All men except Asiatics" is x − y; "all states except monarchies" is x − xy.
- (4.4) z(x − y) = zx − zy. Literal symbols are therefore distributive: a quality ascribed to a whole group is ascribed to each part.

**Class III signs** form propositions. The only copula needed is *is* or *are*, since "Cæsar conquered the Gauls" becomes "Cæsar is he who conquered the Gauls". "The stars are the suns and the planets" is (4.5) x = y + z, and transposing gives x − z = y. Equals added to or taken from equals stay equal, and x = y ⇒ zx = zy.

**Where the analogy with algebra stops.** zx = zy does not give x = y, because logic has no division. Removing z from zx is abstraction. Even in algebra, division needs z ≠ 0; admit z = 0 and the analogy is unbroken. The only numbers satisfying x² = x are 0 and 1. Conceive "an Algebra in which the symbols x, y, z, etc. admit indifferently of the values 0 and 1, and of these values alone." Its laws, axioms and processes coincide with those of an algebra of logic, and "difference of interpretation will alone divide them." That is Boole's method. Two systems such as logic and arithmetic can share symbols through a community of formal laws, not of meaning.

**Results.**
- (4.6) 0y = 0, so 0 is Nothing; 1y = y, so 1 is the Universe: "the two limits of class extension". 1 − x is the contrary class (not-men).
- The **principle of contradiction** follows from the index law: x − x² = 0, so (4.7) x(1 − x) = 0. Nothing is at once men and not-men. What Aristotle called the most certain of principles turns out to be a consequence of a law of thought that is mathematical in form, an equation of the second degree. Boole calls (4.7) the **law of duality**.
- **Primary (concrete) propositions** relate things ("snow is white"). **Secondary (abstract) propositions** relate propositions ("If the sun shines the earth is warmed"). The same symbols and laws serve both; only the interpretation differs.

**Rule of expression.**
- Write simple names as x, y, z and contraries as 1 − x.
- Write a class defined by common qualities as a product, and a collection of distinct portions as a sum.
- With x opaque, y polished, z stones: xyz is opaque polished stones, xy(1 − z) opaque polished things that are not stones, and x(1 − y)(1 − z) opaque things neither polished nor stones. Each term squares to itself.
- "Either x's or y's" is x(1 − y) + y(1 − x) when exclusive and x + y(1 − x) when inclusive. Strict usage makes "or" exclusive, but common usage favors inclusive.
- For three: exclusive is x(1 − y)(1 − z) + y(1 − x)(1 − z) + z(1 − x)(1 − y); inclusive is x + y(1 − x) + z(1 − x)(1 − y).

**Interpretation runs the rule in reverse.** With x hard, y elastic, z metals:
- non-elastic metals: z(1 − y);
- elastic substances together with non-elastic metals: y + z(1 − y);
- hard substances except metals: x − z;
- metals except those neither hard nor elastic: z − z(1 − x)(1 − y) = z{1 − (1 − x)(1 − y)};
- hard substances, except those metallic and non-elastic and those elastic and non-metallic: x − xz(1 − y) − xy(1 − z).

**Development.** A function f(x) is **developed** when it is reduced to the form ax + b(1 − x). Setting x = 1 gives a = f(1), and x = 0 gives b = f(0), so

  f(x) = f(1)·x + f(0)·(1 − x).

Boole likened this to a Taylor expansion.

**Led to.** Logic had barely advanced since Aristotle; Boole made it a branch of mathematics. Peacock (1830) had already called algebra "the science of general reasoning by symbolical language". Boole influenced De Morgan's laws and Venn's diagrams. Jevons's "logic piano", built for four propositions, was the first mechanization of boolean logic. In Boole, + is union, − is difference and juxtaposition is intersection, which carries over to naive set theory and to probability. Shannon (8) took the algebra over wholesale for circuits.

## 5. Hilbert, *Mathematical Problems* (1900)

**Set out to.** At the 1900 International Congress, set the agenda for the coming century with a list of 23 problems, prefaced by an account of what makes a problem good.

**What makes a good problem.**
- "As long as a branch of science offers an abundance of problems, so long is it alive; a lack of problems foreshadows extinction."
- It is **clear**: clear enough to explain to the first person you meet on the street, for "what is clear and easily comprehended attracts, the complicated repels us".
- It is **difficult** enough to entice, "yet not completely inaccessible, lest it mock at our efforts".
- It is "a guide post on the mazy paths to hidden truths".
- Examples:
  - Bernoulli's brachistochrone (line of quickest descent) gave the calculus of variations.
  - Fermat's xⁿ + yⁿ = zⁿ gave Kummer's ideal numbers and unique factorization into ideal primes.
  - The three-body problem gave Poincaré's methods.
  - Fermat's problem and the three-body problem are opposite poles: one comes from pure reason, the other is forced on us by nature.

**What a solution requires: rigor.** Correctness is established "by means of a finite number of steps based upon a finite number of hypotheses which are implied in the statement of the problem and which must always be exactly formulated."

**Heuristics.**
1. **Generalization.** A problem often fails because we miss the more general standpoint from which it is one link in a chain of related problems. "He who seeks for methods without having a definite problem in mind seeks for the most part in vain."
2. **Specialization** plays "a still more important part". Failure often comes from simpler related problems left unsolved.
3. **Impossibility proofs.** When a solution is sought under insufficient hypotheses or in the wrong sense, show that it is impossible. Examples are the irrationality of √2, the parallel axiom, squaring the circle, and the quintic by radicals; each was settled "in another sense than that originally intended". Perpetual motion, inverted, gave conservation of energy.

Hilbert held, without proof, that every definite problem admits settlement: either an answer or a proof of impossibility. "There is the problem. Seek its solution. You can find it by pure reason, for in mathematics there is no *ignorabimus*."

**Problem 2, compatibility of the arithmetical axioms.** Axioms give an exact and complete description of the relations among elementary ideas, and a statement is correct only if it is derivable in finitely many steps. The most important task is to prove the axioms "are not contradictory, that is, that a finite number of logical steps based upon them can never lead to contradictory results."

**Problem 10.** "Given a diophantine equation with any number of unknown quantities and with rational integral numerical coefficients: To devise a process according to which it can be determined by a finite number of operations whether the equation is solvable in rational integers." That is, an equation p(x₁, …, x_k) = 0 with integer coefficients and integer solutions sought. Requiring integers turns an algebraic problem into a combinatorial one.

**Led to.** "Nothing is more important to the progress of science than knowing what question to ask." Problem 10 took seventy years: Davis, Putnam and Julia Robinson, with Matiyasevich's coup de grâce in 1970, showed it recursively unsolvable. The eighth problem (the Riemann hypothesis) remains open. The Clay Millennium Prizes of 2000 offer $1M for each of seven problems, including Riemann and P = NP; only Poincaré's has been solved.

In 1900 there was no precise notion of algorithm, only hints such as "a finite number of operations". The metamathematical tradition ran from Frege's *Begriffsschrift* (1879, the first rigorous axiomatization of logic) through *Principia Mathematica* (1910). The paradoxes prompted Hilbert's program of 1928, to "dispose of the foundational questions in mathematics as such once and for all".

His gravestone reads "We must know. We shall know." He said it in 1930, the day before Gödel announced incompleteness: any consistent, recursively axiomatizable system strong enough for basic arithmetic has true propositions it cannot prove. In closing one door, Gödel and Turing (6) "opened countless others". To prove what algorithms cannot do, Turing had to define what an algorithm is, and that opened algorithms to scientific study.

## 6. Turing, *On Computable Numbers, with an Application to the Entscheidungsproblem* (1936)

**Set out to.** Settle the **Entscheidungsproblem**: is there a procedure to decide whether an arbitrary formula of the predicate calculus (Hilbert and Ackermann's "functional calculus K", 1928) is provable? Proving that no procedure exists requires first circumscribing the class of all procedures. Turing defines the **computable numbers** as the "real numbers whose expressions as a decimal are calculable by finite means", that is, those whose decimal "can be written down by a machine".

**Construct.** The justification starts from the human computer, whose "memory is necessarily limited".
- A machine has finitely many **m-configurations** q₁, …, q_R. It works on a **tape** divided into **squares**, each bearing one symbol. It scans one square r with symbol 𝔖(r), the only one it is "directly aware" of, and remembers by its m-configuration.
- The **configuration** (q_n, 𝔖(r)) determines the next move: write on a blank square, erase, shift one square left or right, and change the m-configuration.
- It prints **figures** (0 and 1), which are the number, and **symbols of the second kind**, which are rough notes "to assist the memory". Only the notes may be erased.
- The **complete configuration** is the number of the scanned square, the whole tape and the m-configuration. Moves are changes between successive complete configurations.
- An **automatic machine (a-machine)** has its motion completely determined by its configuration. A **choice machine (c-machine)** waits at some points for an external operator to choose, as in axiomatic systems.
- A **computing machine** starts on a blank tape and prints figures. With a binary point in front, the figures it prints are the number computed.
- A machine is **circular** if it never writes more than finitely many figures, either because it reaches a configuration with no possible move or because it keeps moving while printing only second-kind symbols. Otherwise it is **circle-free**.
- A **computable sequence** is one computed by a circle-free machine. A **computable number** differs by an integer from a number computed by a circle-free machine.
- Tables use R and L to move, E to erase and P to print.

**Enumeration.**
- Write the machine's table as expressions separated by semicolons.
- Encode state q_i as D followed by i A's and symbol S_j as D followed by j C's. The result, using only A, C, D, L, R, N and ;, is the **standard description (S.D)**.
- Replace A→1, C→2, D→3, L→4, R→5, N→6, ;→7 to get the **description number (D.N)**. The machine with D.N n is ℳ(n).
- Example D.N: 31332531173113353111731113322531111731111335317.
- Every computable sequence has at least one D.N, and no D.N gives more than one sequence. So the computable numbers are **enumerable**: countably many, while the reals are uncountable.
- A **satisfactory** number is the D.N of a circle-free machine.

**Universal machine.** There is a single machine 𝒰 that, given a tape beginning with the S.D of any machine ℳ, computes the same sequence as ℳ.

**The diagonal argument.** The naive version goes as follows. Let β have n-th figure 1 − φ_n(n); if β were computable, say β = φ_K, then n = K gives 1 = 2φ_K(K), "1 is even". Turing calls this fallacious, because it assumes the computable sequences can be enumerated by finite means. Doing that is the same as deciding whether a number is satisfactory.

So he proves directly that no machine 𝒟 can decide satisfactoriness, marking each S.D "u" (circular) or "s" (circle-free). To avoid the feeling that "there must be something wrong", he uses β′, whose n-th figure is φ_n(n). Combine 𝒟 and 𝒰 into a machine ℋ:
- In section N, ℋ runs 𝒟 on N.
- If N is satisfactory, set R(N) = 1 + R(N − 1), compute the first R(N) figures of ℳ(N), and write the R(N)-th figure as the next figure of β′. Otherwise R(N) = R(N − 1).
- Every section is finite, so ℋ is circle-free.
- Let K be ℋ's own D.N. In section K the verdict cannot be "u", since ℋ is circle-free. If it is "s", ℋ must compute its own R(K)-th figure. To do that it must "calculate the first R(K) figures computed by ℋ and write down the R(K)th", which it never finishes. Then ℋ is circular, a contradiction.

It follows that no machine ℰ can decide whether an arbitrary ℳ ever prints a given symbol such as 0.

**Extent of the computable numbers.** Turing asks, "What are the possible processes which can be carried out in computing a number?" Any argument must ultimately appeal to intuition. He gives three kinds: (a) a direct appeal to intuition, (b) a proof that two definitions are equivalent, and (c) examples of large classes of computable numbers.

The argument of type (a):
- Paper ruled in squares can be one-dimensional.
- Finitely many symbols suffice. With infinitely many, some would differ arbitrarily little, and compound symbols like 17 or 999999999999999 can stand in for the rest. One cannot tell at a glance whether 9999999999999999 and 999999999999999 are the same.
- The computer's behavior depends on the symbols observed and the computer's "state of mind". At most B symbols are observed at once, and there are finitely many states of mind; more complicated states can be avoided by writing more symbols down.
- A **simple operation** changes at most one observed symbol, or moves to a new observed square within L squares of an old one, perhaps with a change of state of mind. Comparing a long theorem number such as 157767733443477 figure by figure is not one simple operation.
- A machine with one m-configuration per state of mind, scanning B squares, can do all this, and such a machine is equivalent to a computing machine.

**Application.** There is no general process, and so no machine, for deciding whether a formula 𝔄 of the functional calculus K is provable.
- Gödel had shown that some 𝔄 has neither 𝔄 nor −𝔄 provable, so consistency cannot be proved within the formalism. Turing shows that no method tells whether 𝔄 is provable, or equivalently whether K + (−𝔄) is consistent.
- If the negation of Gödel's result held, a machine 𝒦 enumerating all provable formulas would eventually reach 𝔄 or −𝔄 and so decide.
- Turing builds a formula Un(ℳ) for each machine, using these predicates:
  - R_S(x, y): in complete configuration x, the symbol on square y is S;
  - I(x, y): in x, square y is scanned;
  - K_{q_m}(x): in x, the m-configuration is q_m;
  - F(x, y): y is the immediate successor of x.

  Deciding whether Un(ℳ) is provable would decide whether ℳ ever prints 0.

**Led to.** Gödel's incompleteness (1930–31) had used Cantor's diagonalization and **Gödel numbering**, which codes a string of length k as the product of the first k primes, with the exponent of the k-th prime encoding the k-th symbol. Gödel did not settle the Entscheidungsproblem. Church's lambda calculus (1936) and Turing's machines are different but equivalent, and both men are credited. An impossibility proof has two tasks: prove the theorem, and convince people that the class of procedures is large enough. Church's abstruse calculus fell short on the second. Turing's machines were "simple enough to admit a proof of what they could not do, and yet demonstrably powerful enough". Emil Post anticipated the reduction but did not take the further steps.

Turing's construction of Un(ℳ) was flawed, and he corrected it in 1938. The S.D is "the first clear instantiation of a stored program", with no essential difference between program and data. The stored program returns with the EDVAC report (10).

## 8. Shannon, *A Symbolic Analysis of Relay and Switching Circuits* (1938)

**Set out to.** Give a method for the control and protective circuits of relays and switches, as used in telephone exchanges and motor control. The focus is **network synthesis**: given the required characteristics, find a circuit with the fewest relay contacts and switch blades. Along the way the method finds equivalent circuits and analogues of impedance-network theorems. The circuit becomes a set of equations in a calculus analogous to the calculus of propositions. To synthesize, write the desired characteristics as equations, manipulate them into simplest form and draw the circuit. The method always finds the simplest series-parallel circuit, and sometimes the simplest of any type.

**Construct.** The **hindrance** X_ab of a two-terminal circuit a–b is 0 when the circuit is closed (zero impedance) and 1 when it is open. Two hindrances are equal when they open and close together. **+ is series connection; · (product) is parallel connection** (Figs 8.1–8.3).

**Postulates**, paired by duality (swap 0 with 1 and + with ·):
- 1a: 0·0 = 0
- 1b: 1 + 1 = 1
- 2a: 1 + 0 = 0 + 1 = 1
- 2b: 0·1 = 1·0 = 0
- 3a: 0 + 0 = 0
- 3b: 1·1 = 1
- 4: at any time X = 0 or X = 1

Every theorem therefore has a dual. Only 1 + 1 = 1 departs from ordinary algebra.

**Theorems**, proved by **perfect induction** (checking every case):
- 8.1 commutative: X + Y = Y + X, XY = YX.
- 8.2 associative.
- 8.3a X(Y + Z) = XY + XZ.
- 8.3b X + YZ = (X + Y)(X + Z). This is false in numerical algebra.
- 8.4 1·X = X, 0 + X = X.
- 8.5 1 + X = 1, 0·X = 0.
- **Negation**: X′ = 1 when X = 0. A relay's make contacts give X and its break contacts give X′.
- 8.6 X + X′ = 1, XX′ = 0.
- 8.7 0′ = 1, 1′ = 0.
- 8.8 (X′)′ = X.

**Analogue with the calculus of propositions.** Huntington's postulates are satisfied. **Fig 8.4** is the dictionary:

| Symbol | Circuit | Proposition |
|---|---|---|
| X | the circuit X | the proposition X |
| 0 | closed | false |
| 1 | open | true |
| X + Y | series | true if either is true |
| XY | parallel | true if both are true |
| X′ | open when X is closed | contradictory of X |
| = | open and close together | each implies the other |

Any theorem of the calculus of propositions is a theorem about relay circuits.

**Further theorems.**
- **De Morgan:** 8.9a (X + Y + Z + …)′ = X′Y′Z′…; 8.9b (XYZ…)′ = X′ + Y′ + Z′ + ….
- **Expansion**, as in Boole (4):
  - 8.10a f(X₁, …, X_n) = X₁·f(1, X₂, …, X_n) + X₁′·f(0, X₂, …, X_n).
  - 8.10b f = [f(0, X₂, …) + X₁]·[f(1, X₂, …) + X₁′].
  - Iterating (8.11) gives the **complete expansion** 8.12a: a sum over all 2ⁿ products of primed and unprimed variables, each with coefficient equal to f's value where that product is 1. 8.12b is the dual product form.
  - Consequence: any function can be realized with a chosen variable appearing at most twice, once as a make contact and once as a break (Fig 8.5); applying 8.11 again lets another variable appear at most four times.
- **Generalized De Morgan** 8.13: f(X₁, …, X_n, +, ·)′ = f(X₁′, …, X_n′, ·, +). Negate each variable and swap + with ·, keeping the parentheses. For example, (X + Y(Z + WX′))′ = X′[Y′ + Z′(W′ + X)].
- **Simplification:**
  - 8.14 X = X + X = XX.
  - 8.15 X + XY = X; X(X + Y) = X.
  - 8.16a XY + X′Z = XY + X′Z + YZ, and its dual.
  - 8.17a Xf(X, Y, Z, …) = Xf(1, Y, Z, …); 8.17b X + f(X, Y, Z, …) = X + f(0, Y, Z, …).
  - 8.18a X′f(X, …) = X′f(0, …); 8.18b X′ + f(X, …) = X′ + f(1, …).

**Method of simplification.** Any expression in +, · and ′ is a series-parallel circuit, with each letter a contact. The circuit with the fewest contacts is the expression with the fewest letters. The most useful theorems are 8.3, 8.6, 8.9, 8.14, 8.15, 8.16a, 8.17 and 8.18. Ties are broken arbitrarily or on other grounds.

**Worked example (Figs 8.6–8.7).**

  X_ab = W + W′(X + Y) + (X + Z)(S + W′ + Z)(Z′ + Y + S′V)
    = W + X + Y + (X + Z)(S + 1 + Z)(Z′ + Y + S′V)  (8.17b on W, then X and Y)
    = W + X + Y + Z(Z′ + S′V)
    = W + X + Y + ZZ′ + ZS′V
    = W + X + Y + ZS′V

The result puts W, X and Y in series with a parallel branch of Z, S′ and V: a large reduction.

**Led to.** Peirce had noticed in 1886 that logical connectives correspond to series and parallel circuits. Shannon, an electrical engineer who had met Boole in a philosophy class, exploited the correspondence in his MIT master's thesis. He was the first to describe intended behavior mathematically, manipulate the formulas, and "compile" them into hardware. An omitted passage proves upper and lower bounds on circuit size for certain boolean functions, which foreshadows circuit complexity. Ten years later Shannon founded information theory (12).
