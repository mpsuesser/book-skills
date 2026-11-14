---
name: ideas-that-created-the-future
description: "Harry R. Lewis's Ideas That Created the Future: Classic Papers of Computer Science: 46 founding papers, Aristotle to Shamir, each with the editor's account of what it led to. Use when the user names the book or any of its papers or authors (Leibniz, Lovelace, Boole, Hilbert, Turing, Shannon, von Neumann, Bush, Hopper, Licklider, McCarthy, Engelbart, Dijkstra, Hoare, Codd, Cook, Karp, Knuth, Brooks, Cerf, Kahn, Diffie, Hellman, RSA); when explaining where a computing idea came from or how two ideas connect; or applying a classic construct in original terms: syllogism, boolean algebra, Turing machines, undecidability, switching circuits, entropy and channel capacity, Hamming codes, imitation game, stored program, microprogramming, perceptron, time-sharing, mutual exclusion, semaphores, go to, Hoare logic, abstract data types, relational model, IDF, NP-completeness, big O, waterfall, Brooks's Law, program verification, TCP, Ethernet, public-key cryptography, digital signatures, threshold schemes."
---

# Ideas That Created the Future

Harry Lewis collects 46 papers, from the earliest times to 1979, that made the field "in the words that created the field". He prefaces each with an essay setting its context, and most papers are abridged to their key contributions. He has two aims. The first is to correct the impression that the field's established conventions "were handed down to contemporary culture in finished form". The second is to show how new ideas come to be: "tentative, clumsy baby steps become graceful, progressive strides—or sometimes go nowhere for years and then are taken up again after a long delay." Use the book as the record of each idea as first stated, together with Lewis's account of where it went.

## Using it

1. Find the paper or papers in the index below by author, title or idea, and open each file named. A question that crosses threads opens several files.
2. Answer in the paper's own terms: its definitions and notation, its method and the result, and its numbers. Add Lewis's account of what it led to and which later paper took it up.
3. When the user wants a construct applied, run the method as the file gives it on the user's case and show the steps. Examples are sharing a key with Shamir's scheme, checking a staffing plan against Brooks's Law, or weighting search terms by collection frequency.

Done when the answer names the paper and year, uses the paper's terms, and traces any lineage paper by paper as Lewis draws it.

## How the ideas connect

Lewis calls computer science "the child of logic, the mathematical sciences, and the human imagination." The first computing was numerical calculation: *calculi* were the pebbles of early accountants. His Introduction traces the strands:

- **Logic to computability.** Aristotle (1) gave propositions with variables for properties. A form can be true for every instantiation of its variables, for some, or for none. This is what makes a computer general-purpose: the same binary elements signify different things at different times, as a register can hold the time of day in one program and a street address in the next. Leibniz (2) wanted a calculus of thought. Boole (4) made logic algebra. Hilbert (5) asked whether mathematics could be mechanically decided. Turing (6) answered by defining the machine. That definition made algorithms an object of scientific study and showed that computing has limits.
- **Logic into hardware.** Shannon (8) saw that Boole's laws are the laws of relay circuits. Binary won on two counts: it can be manipulated as boolean algebra, and a degraded two-valued signal is easier to restore. The EDVAC report (10) chose binary. Shannon (12) defined the bit, and Hamming (13) spent extra bits to detect and correct errors.
- **Machines.** Babbage's never-built Analytical Engine let Lovelace (3) reason about programming. Aiken's Mark I (7) ran a fixed tape loop. The stored program "had many parents": Eckert and Mauchly, von Neumann's EDVAC report (10), the Manchester Baby and Turing's ACE. In the 1950s, the "Cambrian era in computer design", Wilkes (15) answered an immediate need with microprogramming. Moore (25) charted the exponential growth of integrated circuits.
- **Brains and minds.** McCulloch and Pitts (9) did something "altogether different": they explained neurons as logic, and theirs is the only work the EDVAC report cites. Rosenblatt's perceptron (18) rebooted a more realistic neural model. Turing (14) replaced "can machines think?" with the imitation game. Weizenbaum's ELIZA (27) showed how readily people engage with a simple program. Wiener (19) warned against handing machines decisions that people should keep.
- **Helping people think.** Bush (11) imagined the memex without seeing that computers would serve it. Licklider (20) imagined symbiosis, Engelbart (22) built augmentation, and Sutherland (24) launched interactive graphics.
- **Programming.** Hopper (16) argued that hardware would become the cheapest part and that higher-level languages are a necessity. McCarthy (21) took symbol manipulation as primitive and put recursion at the center of programming. Dijkstra (29) struck the go to. Hoare (31) treated programs like logic formulas. Liskov and Zilles (39) held data to the same abstraction standards as control, which leads to object-oriented programming. DeMillo, Lipton and Perlis (44) pushed back against formal verification.
- **Operating systems.** The line runs CTSS (23) → THE (28) → UNIX (37). Dijkstra's mutual exclusion (26) is a positive result about concurrency.
- **Algorithms and complexity.** Graph algorithms came out of wartime operations research: Kruskal (17) found minimum spanning trees. Strassen (30) beat Gaussian elimination. Cook (34) made P = NP the central question. Karp (36) showed that many combinatorial explosions "were essentially variations on the same problem". Knuth (43) fixed the notation.
- **Building large software.** Royce (33) and Brooks (40) dissected why big projects fail; "Every programmer should read both."
- **Data and retrieval.** Codd's relational model (32) became the core of the data management industry. Spärck Jones (35) weighed how often a term occurs in a document against how many documents in the collection contain it.
- **Networks.** Cerf and Kahn (38) and Metcalfe and Boggs (41) wrote nonproprietary standards, and those made universal communication possible.
- **Cryptography.** Diffie and Hellman (42) solved key distribution over an insecure channel. RSA (45) supplied the trap-door permutation, whose security "rests on unproven foundations". Shamir (46) is "a gem": high-school mathematics that makes sense only in the computer age.

## The 46 papers

| # | Paper | Leading idea | File |
|---|---|---|---|
| 1 | Aristotle, *Prior Analytics* (∼350 BCE) | syllogism, deduction by form, counterexample terms | [logic-and-computability.md](logic-and-computability.md) |
| 2 | Leibniz, *The True Method* (1677) | characters for thought, "Let us calculate", binary | [logic-and-computability.md](logic-and-computability.md) |
| 3 | Menabrea and Lovelace, *Sketch of the Analytical Engine* (1843) | mill and store, Operation- and Variable-cards, cycles, "no pretensions to originate" | [machines.md](machines.md) |
| 4 | Boole, *The Laws of Thought* (1854) | algebra of 0 and 1, x² = x, law of duality, development | [logic-and-computability.md](logic-and-computability.md) |
| 5 | Hilbert, *Mathematical Problems* (1900) | good problems, no *ignorabimus*, problems 2 and 10 | [logic-and-computability.md](logic-and-computability.md) |
| 6 | Turing, *On Computable Numbers* (1936) | a-machine, universal machine, diagonal argument, Entscheidungsproblem | [logic-and-computability.md](logic-and-computability.md) |
| 7 | Aiken, *A Proposed Automatic Calculating Machine* (1937) | four features beyond accounting machines, control design | [machines.md](machines.md) |
| 8 | Shannon, *A Symbolic Analysis of Relay and Switching Circuits* (1938) | hindrance algebra, series = +, parallel = ·, circuit simplification | [logic-and-computability.md](logic-and-computability.md) |
| 9 | McCulloch and Pitts, *A Logical Calculus of the Ideas Immanent in Nervous Activity* (1943) | all-or-none neurons as propositions, nets with circles | [minds-and-machines.md](minds-and-machines.md) |
| 10 | von Neumann, *First Draft of a Report on the EDVAC* (1945) | CA, CC, M, I, O; binary; one memory for orders and numbers | [machines.md](machines.md) |
| 11 | Bush, *As We May Think* (1945) | memex, associative trails | [augmenting-humans.md](augmenting-humans.md) |
| 12 | Shannon, *A Mathematical Theory of Communication* (1948) | bit, entropy H, capacity of the noiseless channel, approximations to English | [information-and-coding.md](information-and-coding.md) |
| 13 | Hamming, *Error Detecting and Error Correcting Codes* (1950) | parity checks, Hamming distance, single-error-correcting code | [information-and-coding.md](information-and-coding.md) |
| 14 | Turing, *Computing Machinery and Intelligence* (1950) | imitation game, the nine objections, learning machines | [minds-and-machines.md](minds-and-machines.md) |
| 15 | Wilkes, *The Best Way to Design an Automatic Calculating Machine* (1951) | microprogramming, control matrices | [machines.md](machines.md) |
| 16 | Hopper, *The Education of a Computer* (1952) | subroutine library, compiling routines | [programming-languages.md](programming-languages.md) |
| 17 | Kruskal, *On the Shortest Spanning Subtree of a Graph* (1956) | shortest-edge-first spanning tree | [algorithms-and-complexity.md](algorithms-and-complexity.md) |
| 18 | Rosenblatt, *The Perceptron* (1958) | S-, A-, R-units, reinforcement, learning by connection | [minds-and-machines.md](minds-and-machines.md) |
| 19 | Wiener, *Some Moral and Technical Consequences of Automation* (1960) | machines that escape control, monkey's paw | [minds-and-machines.md](minds-and-machines.md) |
| 20 | Licklider, *Man–Computer Symbiosis* (1960) | symbiosis, formulative thinking, 85 per cent | [augmenting-humans.md](augmenting-humans.md) |
| 21 | McCarthy, *Recursive Functions of Symbolic Expressions* (1960) | S-expressions, car/cdr/cons, conditional expressions, eval | [programming-languages.md](programming-languages.md) |
| 22 | Engelbart, *Augmenting Human Intellect* (1962) | H-LAM/T, augmentation means, bootstrapping | [augmenting-humans.md](augmenting-humans.md) |
| 23 | Corbató, Daggett and Daley, *An Experimental Time-Sharing System* (1962) | CTSS, scheduling queues, response time | [operating-systems.md](operating-systems.md) |
| 24 | Sutherland, *Sketchpad* (1963) | light pen, constraints, ring structure, instances | [augmenting-humans.md](augmenting-humans.md) |
| 25 | Moore, *Cramming More Components onto Integrated Circuits* (1965) | components per chip doubling yearly, minimum cost | [machines.md](machines.md) |
| 26 | Dijkstra, *Solution of a Problem in Concurrent Program Control* (1965) | mutual exclusion among N computers | [operating-systems.md](operating-systems.md) |
| 27 | Weizenbaum, *ELIZA* (1966) | keywords, decomposition and reassembly rules, DOCTOR script | [minds-and-machines.md](minds-and-machines.md) |
| 28 | Dijkstra, *The Structure of the "THE"-Multiprogramming System* (1968) | layered levels, semaphores, harmonious cooperation | [operating-systems.md](operating-systems.md) |
| 29 | Dijkstra, *Go To Statement Considered Harmful* (1968) | textual index, dynamic progress of the process | [programming-languages.md](programming-languages.md) |
| 30 | Strassen, *Gaussian Elimination is Not Optimal* (1969) | seven multiplications, O(n^log₂7) | [algorithms-and-complexity.md](algorithms-and-complexity.md) |
| 31 | Hoare, *An Axiomatic Basis for Computer Programming* (1969) | P {Q} R, assignment axiom, rules of consequence, composition, iteration | [programming-languages.md](programming-languages.md) |
| 32 | Codd, *A Relational Model of Large Shared Data Banks* (1970) | data independence, relations, normal form, projection and join | [data-and-retrieval.md](data-and-retrieval.md) |
| 33 | Royce, *Managing the Development of Large Software Systems* (1970) | the stepwise model and its five fixes | [software-engineering.md](software-engineering.md) |
| 34 | Cook, *The Complexity of Theorem-Proving Procedures* (1971) | P-reducibility, tautologies, ℒ*, subgraph problem | [algorithms-and-complexity.md](algorithms-and-complexity.md) |
| 35 | Spärck Jones, *A Statistical Interpretation of Term Specificity* (1972) | specificity as frequency, collection-frequency weighting (IDF) | [data-and-retrieval.md](data-and-retrieval.md) |
| 36 | Karp, *Reducibility among Combinatorial Problems* (1972) | 𝒫, 𝒩𝒫, ≼, 21 complete problems | [algorithms-and-complexity.md](algorithms-and-complexity.md) |
| 37 | Ritchie and Thompson, *The UNIX Time-Sharing System* (1974) | i-node, special files, fork/exec, pipes, the Shell | [operating-systems.md](operating-systems.md) |
| 38 | Cerf and Kahn, *A Protocol for Packet Network Intercommunication* (1974) | GATEWAY, TCP, fragmentation, ports, window | [networks.md](networks.md) |
| 39 | Liskov and Zilles, *Programming with Abstract Data Types* (1974) | abstract data type, operation cluster, rep | [programming-languages.md](programming-languages.md) |
| 40 | Brooks, *The Mythical Man-Month* (1975) | man-month myth, n(n − 1)/2, Brooks's Law | [software-engineering.md](software-engineering.md) |
| 41 | Metcalfe and Boggs, *Ethernet* (1976) | Ether, carrier detection, collisions, binary exponential backoff | [networks.md](networks.md) |
| 42 | Diffie and Hellman, *New Directions in Cryptography* (1976) | public key cryptosystem, key exchange, one-way and trap-door functions | [cryptography.md](cryptography.md) |
| 43 | Knuth, *Big Omicron and Big Omega and Big Theta* (1976) | O, Ω, Θ as sets of functions | [algorithms-and-complexity.md](algorithms-and-complexity.md) |
| 44 | DeMillo, Lipton and Perlis, *Social Processes and Proofs of Theorems and Programs* (1977) | proofs as social process, verification bound to fail | [software-engineering.md](software-engineering.md) |
| 45 | Rivest, Shamir and Adleman, *A Method for Obtaining Digital Signatures and Public-Key Cryptosystems* (1978) | M^e mod n, e·d ≡ 1 mod φ(n), Alice and Bob | [cryptography.md](cryptography.md) |
| 46 | Shamir, *How to Share a Secret* (1979) | (k, n) threshold scheme by polynomial interpolation | [cryptography.md](cryptography.md) |
