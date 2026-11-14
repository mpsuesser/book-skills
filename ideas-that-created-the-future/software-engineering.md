# Software engineering

Papers 33, 40 and 44: Royce on managing large software development, Brooks's mythical man-month, and DeMillo, Lipton and Perlis against program verification.

## 33. Royce, *Managing the Development of Large Software Systems* (1970)

**Set out to.** Give personal views on managing large software developments, from nine years of software for spacecraft mission planning, commanding and post-flight analysis: "I have become prejudiced by my experiences."

**Construct: the steps.**
- **Fig 33.1.** Two steps are common to all programs: ANALYSIS → CODING. That suffices for a small program built and operated by the same people, and customers are happy to pay for both, since both are genuinely creative.
- For larger systems that approach is "doomed to failure". The added steps contribute less directly and drive up costs; customers would rather not pay for them and developers would rather not do them. "The prime function of management is to sell these concepts to both groups and then enforce compliance on the part of development personnel."
- **Fig 33.2,** a large program delivered to a customer: SYSTEM REQUIREMENTS → SOFTWARE REQUIREMENTS → ANALYSIS → PROGRAM DESIGN → CODING → TESTING → OPERATIONS.
- **Fig 33.3,** iteration: each step iterates with the one before and after it, rarely with remote ones. That scopes change to manageable limits and keeps "a firm and closeup moving baseline to which to return", a fallback that saves as much early work as possible.
- **Fig 33.4,** the risk: "I believe in this concept, but the implementation described above is risky and invites failure."
  - Testing, at the end, is the first event where timing, storage and input/output transfers are experienced rather than analyzed. If they fail, the fix is a major redesign, not "a simple octal patch or redo of some isolated code".
  - The feedback arrows run TESTING → PROGRAM DESIGN → SOFTWARE REQUIREMENTS. "The development process has returned to the origin and one can expect up to a 100-percent overrun in schedule and/or costs."
  - Analysis and coding, by contrast, are managed with relative ease: whole departments on orbit mechanics, spacecraft attitude determination or payload optimization yield a few lines of serial arithmetic code.

The approach is "fundamentally sound", and five added features remove most of the risk.

**The five steps.**
1. **Program design comes first** (Fig 33.5). Insert a preliminary program design between software requirements and analysis.
   - The objection is that this designs in a vacuum and may be substantially wrong: "This criticism is correct but it misses the point." The designer makes sure the software will not fail for reasons of storage, timing and data flux, and imposes those constraints on the analyst, so that insufficient resources or a wrong embryo design are recognized early.
   - Begin with program designers, not analysts or programmers. Design, define and allocate the data processing modes even at the risk of being wrong: processing and functions, the data base, execution time, operating system interfaces, input/output processing and preliminary operating procedures.
   - Write an overview document that is understandable, informative and current. Every worker should have an elemental understanding of the system, and at least one person a deep one, partly from having had to write the overview.
2. **Document the design.** How much documentation? "Quite a lot."
   - "The first rule of managing software development is ruthless enforcement of documentation requirements." Royce's remedy for a project in serious documentation default: replace project management, stop everything not related to documentation, and bring it up to standard.
   - A $5 million hardware device needs a 30-page specification; $5 million of software needs a 1500-page one.
   - Why so much:
     - A written description forces designers to take an unequivocal position, gives tangible evidence of completion, and prevents the "I am 90-percent finished" syndrome, month after month.
     - Early on, "the documentation is the specification and is the design". Bad documentation means bad design, and no documentation means no design, only people thinking and talking.
     - Documentation pays downstream: in testing, many people can work on mistakes, rather than the one man (who probably made the mistake) analyzing every one; in operations, where "the software is always blamed first" and documentation must fix or absolve the blame; and in redesign, updating and retrofitting in the field.
   - **Fig 33.6,** six documents:
     1. Software Requirements;
     2. Preliminary Design (spec);
     3. Interface Design (spec);
     4. Final Design (spec, then as built);
     5. Test Plan (spec, then test results);
     6. Operating Instructions.

     At delivery, documents 1 and 3–6 are updated and current.
3. **Do it twice** (Fig 33.7). If a product is being developed for the first time, the delivered version should be "actually the second version insofar as critical design/operations areas are concerned".
   - The pilot runs the entire process in miniature: preliminary design, analysis, program design, coding, testing and usage, feeding the main sequence. A 30-month effort gets about a 10-month pilot; a 12-month effort, three months.
   - It needs a "very special kind of broad competence": a feel for the trouble spots, modeling them and their alternatives, forgetting the straightforward parts.
   - Timing and storage are then studied with precision instead of judgment, because human judgment in program design, "as in the estimation of takeoff gross weight, costs to complete, or the daily double", is "invariably and seriously optimistic".
4. **Plan, control and monitor testing** (Fig 33.8). Testing uses the most resources, carries the greatest risk, and comes last, when backup is least available.
   - Use test specialists who did not contribute to the design. The argument that only the designer can test is "a sure sign of a failure to document properly".
   - Have a second party visually inspect every bit of analysis and code, for dropped minus signs, missing factors of two and jumps to wrong addresses. "Do not use the computer to detect this kind of thing—it is too expensive."
   - "Test every logic path in the computer program at least once with some kind of numerical check."
   - Once the simple errors, which obscure the big ones, are removed, turn the software over to the test area. The key decisions are when, and by whom, final checkout is done.
5. **Involve the customer** (Fig 33.9). Even after agreement, what the software will do is open to wide interpretation, so commit the customer formally before delivery, at three points:
   - PSR (Preliminary Software Review), after preliminary program design;
   - CSR (Critical Software Review), several, after program design;
   - FSAR (Final Software Acceptance Review), after testing.

**Summary (Fig 33.10).** Each item costs money, but "the simpler method has never worked on large software development efforts", and the cost of recovery far exceeded that of the five-step process.

**Led to.** Royce, an aeronautical engineer by training, led aerospace software projects at TRW and then Lockheed from 1961 to 1994. Figs 33.1 and 33.2 gave rise to the term **waterfall model**: each stage complete before the next, no backing up, and later problems blamed on failed earlier stages. But "Royce himself never uses the term 'waterfall'", and the paper plainly includes elements of iterative or agile methods, with provisional early implementations used to refine the design.

The emphasis on design, analysis and documentation over coding resonates with Dijkstra (28), without his mathematical stiffness. Royce could not insist on simplicity and elegance as the highest values. His commitment to thorough testing would not impress Dijkstra, for whom testing can reveal errors but never establish correctness. Brooks (40) drew on experience in the same way. The paper "is so full of useful wisdom that it has passed the test of time".

## 40. Brooks, *The Mythical Man-Month* (1975)

**Set out to.** Explain why "more software projects have gone awry for lack of calendar time than for all other causes combined." The epigraph is the notice on the menu of Restaurant Antoine in New Orleans: "Good cuisine takes time. If we make you wait, it's to serve you better and please you."

Brooks gives five reasons:
1. Estimating techniques are poorly developed, and they carry the unvoiced, untrue assumption "that all will go well".
2. They "fallaciously confuse effort with progress, hiding the assumption that men and months are interchangeable".
3. Uncertain of their estimates, managers "lack the courteous stubbornness of Antoine's chef".
4. Schedule progress is poorly monitored.
5. When slippage is recognized, the natural response is to add manpower: "Like dousing a fire with gasoline, this makes matters worse, much worse."

**Optimism.** "All programmers are optimists." Dorothy Sayers, in *The Mind of the Maker*, divides creative activity into three stages: the idea, the implementation, and the interaction. Implementation exposes the incompleteness of ideas, and physical media are intractable: "Lumber splits; paints smear; electrical circuits ring." The programmer, though, "builds from pure thoughtstuff", an exceedingly tractable medium, so we expect few difficulties. "Because our ideas are faulty, we have bugs; hence our optimism is unjustified." Each task has a finite probability of no delay, and for many tasks chained end to end, the probability that all go well becomes vanishingly small.

**The man-month.** Cost varies as the product of men and months; progress does not. "Hence the man-month as a unit for measuring the size of a job is a dangerous and deceptive myth."

| Figure | Task | Months vs. men |
|---|---|---|
| 40.1 | Perfectly partitionable, no communication (reaping wheat, picking cotton) | fall inversely, a hyperbola |
| 40.2 | Unpartitionable, sequential constraints | a flat line: "The bearing of a child takes nine months, no matter how many women are assigned." |
| 40.3 | Partitionable but requiring communication | fall, then level off higher |
| 40.4 | Complex interrelationships | U-shaped: a minimum, then rising |

Communication adds training, which cannot be partitioned and so grows linearly in the number of workers, and intercommunication. If each part must be coordinated with each other part, the effort grows as n(n − 1)/2: three workers need three times as much pairwise intercommunication as two, and four need six times as much. Software is "inherently a systems effort—an exercise in complex interrelationships", so "adding more men then lengthens, not shortens, the schedule."

**Systems test.** Debugging is the part most affected by sequential constraints, so testing is usually the most mis-scheduled. Brooks's rule of thumb:
- 1/3 planning;
- 1/6 coding;
- 1/4 component test and early system test;
- 1/4 system test, with all components in hand.

Few conventional schedules allowed half for testing, yet most projects spent half. Many were on schedule "until and except in system testing". A late slip is peculiarly disastrous: it comes without warning, when the team is fully staffed, the cost per day is at its maximum, and secondary costs are very high.

**Gutless estimating.** The urgency of the patron may govern the scheduled completion, but not the actual completion. An omelette promised in two minutes either waits or is eaten raw; turning up the heat gives "an omelette nothing can save—burned in one part, raw in another". The estimates are hard to defend because they are "derived by no quantitative method, supported by little data, and certified chiefly by the hunches of the managers". There are two remedies: develop and publicize productivity figures, bug-incidence figures and estimating rules; meanwhile, managers must stiffen their backbones and defend their estimates.

**Regenerative schedule disaster.**
- **The case.** A task is estimated at 12 man-months: three men for four months, with milestones A, B, C and D at the end of each month (Fig 40.5). The first milestone is reached only after two months (Fig 40.6).
- **The options:**
  1. Only the first part was misestimated. Then 9 man-months remain in two months, which needs 4½ men: add 2 to the 3.
  2. The whole estimate was uniformly low (Fig 40.7). Then 18 man-months remain, which needs 9 men: add 6.
  3. Reschedule. P. Fagg's advice: "Take no small slips."
  4. Trim the task, formally and carefully, or watch it "get silently trimmed by hasty design and incomplete testing".
- **Why the first option fails** (Fig 40.8):
  1. The two new men need a month of training from an experienced man, so "3 man-months will have been devoted to work not in the original estimate."
  2. Repartitioning three ways into five loses work and lengthens system testing.
  3. At the end of month 3 more than 7 man-months remain, with 5 trained people and one month left. The product is just as late as if no one had been added.

  Finishing in four months would have meant adding 4 men, not 2. That makes a team of at least 7, whose organization and division of the task are "different in kind, not merely in degree". Repeating the cycle at the missed milestone is the temptation: "Therein lies madness." The regenerative disaster yields "a poorer product, later, than would rescheduling with the original three men, unaugmented".

**Brooks's Law.** "Oversimplifying outrageously": "Adding manpower to a late software project makes it later."
- Sequential constraints bound the number of months, and the number of independent subtasks bounds the number of men.
- From those two numbers one can derive schedules with fewer men and more months; the only risk is product obsolescence.
- One cannot get workable schedules with more men and fewer months.

**Led to.** Software was hard to write and harder to estimate, and engineering management practice did not apply. Tom Cheatham: "when someone tells you that a bridge is half built, you can walk out onto it and see." Compare Royce's 90-percent-finished syndrome (33).

Brooks wrote his Harvard thesis on business data processing under Aiken (7) and joined IBM in 1956, when each machine was incompatible with its predecessor. Seeing, as Hopper (16) predicted, that rewriting software to move up would cost unsustainably, he designed the System/360 line so that software ran on newer, more powerful models with different hardware implementations; Wilkes's microprogramming (15) helped. He coined **computer architecture**: the structure of a computer system as the software sees it. When he left IBM, Thomas Watson Jr. asked why software projects were so hard to manage, and this essay is part of the answer.

Brooks later founded the computer science department at the University of North Carolina. A decade on, "No Silver Bullet: Essence and Accident in Software Engineering" (1987) explained why none of the new technologies had made software production significantly simpler or faster. Modularization, reuse and open-source libraries have helped, but they have "by no means invalidated the humble wisdom of this essay". Proposals to add labor to a late project, ignoring ramp-up and coordination, are still not unusual.

## 44. DeMillo, Lipton & Perlis, *Social Processes and Proofs of Theorems and Programs* (1977)

**Set out to.** Answer the claim that programming should become more like mathematics: "Maybe so, but not in the way they seem to think." Program verification seeks confidence in software through "a long chain of formal, deductive logic". Mathematicians could in principle work that way, "but in fact they don't. What they use is a proof, a very different animal." The thesis: "in the end, it is a social process that determines whether mathematicians feel confident about a theorem", and since no comparable social process can take place among program verifiers, "program verification is bound to fail."

The epigraph is J. Barkley Rosser: "intuition is the final authority."

**Construct: proof as social process.** Outsiders see mathematics as cold, formal, logical, mechanical and monolithic. Insofar as it is successful, it is "a social, informal, intuitive, organic, human process, a community project".
- The formalist view, elaborated by Russell and Hilbert, runs from axioms to theorems by a few fixed rules of transformation. *Principia Mathematica* was its crowning achievement and "also the deathblow": three enormous volumes barely got past elementary arithmetic. "If the mathematical process were really one of strict, logical progression, we would still be counting on our fingers."

**Believing theorems and proofs.** Ulam estimates 200,000 theorems are published every year. Some are contradicted, others doubted, and most ignored; only a tiny fraction are understood and believed by a sizable group. The authors' examples:
- Kempe's 1879 four-color proof stood eleven years before Heawood found the flaw.
- The first Hardy–Littlewood paper (1911) was never published because the proof was wrong.
- Cauchy, Lamé and Kummer each thought they had proved Fermat's Last Theorem.
- In 1945 Rademacher announced, in *Time*, a solution of the Riemann Hypothesis.
- Jech's footnotes on independence results record withdrawn claims by Levy, Marek, Truss and Felgner.
- American and Japanese topologists exchanged contradictory homotopy group results, and neither side was discredited.

"The point is not that mathematicians make mistakes"; it is that their errors are corrected "not by formal symbolic logic, but by other mathematicians." Simplicity is no guarantee either: from Ptolemy to Legendre, attempts on the Parallel Postulate produced "lovely, trim proofs that turned out to be false."

What, then, do we believe when we believe a theorem?
- **The classical view** is that a correct formal deduction exists in principle, in Zermelo–Fraenkel set theory or Peano arithmetic, without anyone writing it. A formal demonstration of one of Ramanujan's conjectures would run about two thousand pages.
- **Probabilists** hold that long proofs are only probably correct. Rabin's probable-primality algorithm (1976) gives answers with vanishingly small error probability for numbers where classical techniques are unworkable, beyond about 10^(10^4).

**A proof is a message.** "A proof is not a beautiful abstract object with an independent existence."
- Its life: a mathematician runs into the hall, commandeers a colleague's blackboard, and phones Texas and Toronto. Then come the write-up, drafts, referees and publication.
- A believed proof is **internalized**, paraphrased into the reader's own terms, so multiple versions reinforce belief. Gauss gave at least half a dozen proofs of quadratic reciprocity, and over fifty are now known. Lakatos traced Euler's V − E + F = 2 being reformulated for almost two hundred years.
- It is **transformed** and **generalized**, and a believed generalization raises the original's plausibility.
- It is **used**, as a lemma, or by engineers in bridges that stand and airplanes that fly.
- It is **connected** to other areas. Cohen's forcing (1964) was hardly understood until it was interpreted algebraically and generalized; now graduate students routinely study it.
- Eventually the community grants the central concepts "ultimate stability" and calls the theorem true in the classical sense, "although for almost all theorems no such deduction ever took place or ever will."

**Simplicity.** Important theorems tend to take the form "Every —— is a ——", not a clause-laden form with exceptions. That is no accident: simple theorems are the ones heard, internalized and used. "Mathematicians are not altruistic masochists." A proposition whose proof needs "five blackboards or a roll of paper towels" is unlikely to be assimilated. "The proof by itself is nothing; only when it has been subjected to the social processes of the mathematical community does it become believable." Manin: "A good proof is one that makes us wiser."

**Disbelieving verifications.** A long formal verification corresponds "not to the working mathematical proof, but to the imaginary logical structure that the mathematician conjures up to describe his feeling of belief." "Verifications are not messages." They cannot be read, internalized, transformed, generalized, used or connected, so "one either believes them blindly, as a pure act of faith, or not at all."

| | Theorem | Proof | Imaginary formal demonstration |
|---|---|---|---|
| Fig 44.1, the verifiers' analogy | program | verification | |
| Fig 44.2, the authors' analogy | specification | program | verification |

On the authors' analogy, verifiers should stop calling verifications "proofs".

- **Informal to formal.** Requirements are informal and programs formal, so the transition between them is necessarily informal.
- **Independence.** Showing consistency with a specification has value only if specification and program were derived independently. In real life each is changed using knowledge of the other, and forbidding that is "a position of incredible poverty".
- **Real specifications.** They are long, complex and peculiar: the payroll for the French National Railroad has more than 3,000 pay rates, one for going uphill and one for downhill. Some numerical algorithms work for no known reason; Reverse Cuthill–McKee was known empirically to beat plain Cuthill–McKee long before George (1971) showed why.
- **Shallowness.** The reply that specifications are only long, not deep: "Precisely. Verifications are long and involved but shallow; that's what's wrong with them." Even a puny verification runs dozens of pages without "a light moment or a spark of wit". "Nobody is ever going to read it."
- **Automatic verifiers.** Lower bounds on the length of formal demonstrations are immense (Stockmeyer 1974). Picture a 300-line input/output package that, after several hours, yields a 20,000-line verification and the message "VERIFIED."
- **The Titanic effect.** Removing redundancy because a structure feels provably right makes failure massive and uncontrolled: "the severity with which a system fails is directly proportional to the intensity of the designer's belief that it cannot fail." The notes on the Euclid language omit exception handling, because "runtime software errors should not occur in verified programs": "Shades of the ship that shouldn't be sunk."
- **What VERIFIED would mean.** Even then it says formally correct, not reliable, trustworthy or safe. "Any human artifact of sufficient size and complexity is imperfect. The message will never read 'VERIFIED.'"

**Continuity.** The fetching defense is scaling up: verification will grow from FIND and GCD, and a production system is just a sum of small algorithms. The authors accept the first half; algorithms were proved and discussed informally long before computers. They reject the second.
- There is no continuity between FIND and a billing system that writes real bills.
- Production jargon tells the story: patches, bandaids and tourniquets, bells and whistles, glue, kitchen sink. More than half the code of a real production system is user interfaces and error messages.
- Hoare: "In many applications, algorithm plays almost no role, and certainly presents almost no problem."
- Algorithm specifications are concise, tidy and stable for decades. A real system's specification is as big as the system and changes daily. "Babysitting for a sleeping child for one hour does not scale up to raising a family of ten."
- "Programs are jagged and full of holes and caverns"; one changed bit can destroy one. Think of systems as composed "of butterflies' wings".
- A verification transfers to no other program, "not even to a program only one single line different from the original", so no community of verifiers forms.

**Believing software.** Epigraph, P. J. Davis: "The program itself is the only complete description of what the program will do."
- Resources are finite. Albert Meyer showed that a computer deciding the truth of simple formulas of at most a thousand bits, even with proton-size components, "must densely fill the entire observable universe." "Not even the computer can change the finite nature of the universe."
- No working system has been verified; there has never been a verification of a COBOL system that prints real checks.
- Engineering faces two problems: "people must plunge into activities that they do not understand. Second, people cannot create perfect mechanisms." Engineers answer with social processes of successive approximation and with the mature view that "reliable" never means "perfect".
- It is "nothing but symbol chauvinism" to think computer structures should be perfect and that energy should go into making them so. The SYNCHEM synthesizer's criterion: if it synthesizes the chemical, it works.
- "Make a sharp distinction between program reliability and program perfection—and concentrate our efforts on reliability." The model is general structures whose instances grow more reliable as the structure does: Knuth's generally useful algorithms (43), Baker's team programming, and reuse as a design criterion.
- "Verification is nothing but a model of believability."
- The authors ask colleagues not to narrow their vision, closing with Bronowski: "A science which orders its thought too early is stifled."

**Led to.** A valued colleague told Lewis the paper's "polemical overreach" meant it should not appear in the book. The controversy significantly slowed funding for program verification. It hit a nerve because it forced introspection about how computer science resembles mathematics, setting the formalist program against how mathematics works in practice. That some still bristle is a "testament to its dialectical force". James Fetzer (1988) later offended both sides: the authors had offered "some bad arguments for some positions that need further elaboration and deserve better support."

Today, even if Hoare's goals (31) were excessively ambitious, formal verification of hardware design and low-level code is "not only useful but essential". The 2007 Turing Award went to Clarke, Emerson and Sifakis for model checking of hardware and software. Formal verification of large software remains rare, for reasons Hoare himself seems to have acknowledged.

Perlis chaired the 1957 joint U.S.–European committee that produced ALGOL 60, precursor of all block-structured imperative languages. He won the first Turing Award (1966) and founded computer science at what is now Carnegie Mellon, then chaired it at Yale. DeMillo and Lipton were longtime collaborators, and both are now at Georgia Tech.
