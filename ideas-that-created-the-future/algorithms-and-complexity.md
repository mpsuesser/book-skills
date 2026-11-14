# Algorithms and complexity

Papers 17, 30, 34, 36 and 43: Kruskal's spanning tree, Strassen's matrix multiplication, Cook's theorem, Karp's 21 complete problems, and Knuth's O, Ω and Θ.

## 17. Kruskal, *On the Shortest Spanning Subtree of a Graph and the Traveling Salesman Problem* (1956)

**Set out to.** Give a simpler construction, and a proof, for a result whose typewritten translation "of obscure origin" from Borůvka had raised interest. The result: if a finite connected graph has a positive real length on each edge, and all the lengths are distinct, then the shortest spanning tree is unique. (A subgraph *spans* if it contains every vertex.) Borůvka's construction was "unnecessarily elaborate", and "probably it is true that any construction which solves Problem 1 may be used to prove this theorem."

- **Problem 1:** "Give a practical method for constructing a spanning subtree of minimum length."
- **Problem 2:** the same for an *unbranched* spanning subtree of minimum length, a version of the traveling salesman problem.

Assume without loss of generality that the graph is complete: insert any missing edge with a great length, which can be thought of as infinite.

**Constructions.**
- **Construction A.** Repeat as often as possible: among the edges not yet chosen, choose the shortest edge that does not form a loop with those already chosen. The chosen edges form the shortest spanning tree.
- **Construction B.** Fix any nonempty set V of vertices. Repeat: among the edges not yet chosen that touch a vertex of V or an edge already chosen, pick the shortest that forms no loop. With V = all vertices, this is A.
- **Construction A′**, the dual of A. Repeat: among the edges not yet chosen, choose the longest whose removal will not disconnect the remaining edges. The edges never chosen form the shortest spanning tree. Kruskal does not know whether B has a dual.

**Preliminary theorem.** Let G be connected with n vertices, and T a subgraph. These are equivalent: (a) T is a spanning tree; (b) T is a maximal forest; (c) T is a minimal connected spanning graph; (d) T is a forest with n − 1 edges; (e) T is a connected spanning graph with n − 1 edges. A *forest* has no loops. "For aesthetic reasons, I state considerably more than I need."

**Proof of uniqueness.**
1. Let T be any shortest spanning tree, that is, any shortest forest with n − 1 edges.
2. Let a₁, …, a_{n−1} be the edges chosen by Construction A, and A_i the forest of a₁, …, a_i. Since the lengths are distinct, A proceeds uniquely.
3. Suppose T ≠ A_{n−1}, and let a_i be the first edge of A_{n−1} not in T.
4. T ∪ a_i has exactly one loop, and that loop contains some edge e not in A_{n−1}. T ∪ a_i − e is a forest with n − 1 edges.
5. A_{i−1} ∪ e lies inside it, so it is a forest too. Construction A therefore preferred a_i to e: length(a_i) < length(e).
6. Then T ∪ a_i − e is shorter than T, a contradiction.

**Led to.** Lewis sees the paper as an early step from operations research, which flourished in the 1940s, into computer science as the study of algorithms. Construction A is **Kruskal's algorithm**: grow a forest by adding edges from shortest to longest, skipping any that would create a cycle. Borůvka (1926), designing the most efficient electrical network for Moravia, probably published the first such algorithm.

The paper is lucid, spare and elegant, but entirely without analysis; "practical" is never defined. A decade later Edmonds and Cobham (34) proposed polynomial running time as the proxy for practicality, and Knuth raised the bar further (43). A naive implementation runs in O(m log n) for m edges and n vertices. Tarjan's (1975) union-find analysis gives O(m α(n)) under commonly satisfied assumptions, where α is the inverse Ackermann function, less than 5 for any n smaller than the number of particles in the universe. That is effectively linear in the number of edges.

Prim's algorithm (1957) is Construction B with V a single vertex: grow one tree, always adding the shortest adjacent edge, a greedy strategy. Dijkstra rediscovered it in 1959 while working on shortest paths, and Jarník (1930) anticipated all three. A′ has no common name. Warshall's transitive closure and Floyd's all-pairs shortest paths (both 1962), dynamic programming, were another step from operations research into computer science.

The traveling salesman problem looks similar, but the difference became dramatic when Karp (36) showed it NP-complete: UNDIRECTED HAMILTON CIRCUIT is its special case with all distances 1.

## 30. Strassen, *Gaussian Elimination is Not Optimal* (1969)

**Set out to.** Multiply two square matrices of order n with fewer than 4.7·n^{log 7} arithmetic operations (log base 2, log 7 ≈ 2.8), against about 2n³ for the usual method. The same bound, up to a constant, follows for inverting a matrix, solving n linear equations and computing a determinant. Klyuev and Kokovkin-Shcherbak (1965) had shown Gaussian elimination optimal among methods that operate on whole rows and columns; this result escapes that restriction.

**Construct: algorithms α_{m,k}** multiply matrices of order m2^k, by induction on k. α_{m,0} is the usual method, with m³ multiplications and m²(m − 1) additions. For α_{m,k+1}, partition A, B and C = AB of order m2^{k+1} into 2 × 2 blocks of order m2^k, and compute:

- I = (A₁₁ + A₂₂)(B₁₁ + B₂₂)
- II = (A₂₁ + A₂₂)B₁₁
- III = A₁₁(B₁₂ − B₂₂)
- IV = A₂₂(−B₁₁ + B₂₁)
- V = (A₁₁ + A₁₂)B₂₂
- VI = (−A₁₁ + A₂₁)(B₁₁ + B₁₂)
- VII = (A₁₂ − A₂₂)(B₂₁ + B₂₂)

Then:

- C₁₁ = I + IV − V + VII
- C₂₁ = II + IV
- C₁₂ = III + V
- C₂₂ = I + III − II + VI

The seven block products use α_{m,k}; additions and subtractions are done the usual way.

**Results.**
- **Fact 1.** α_{m,k} computes a product of order m2^k with m³7^k multiplications and (5 + m)m²7^k − 6(m2^k)² additions and subtractions. For order 2^k that is 7^k multiplications and fewer than 6·7^k additions and subtractions.
- **Fact 2.** A product of order n takes fewer than 4.7·n^{log 7} operations.
  1. Take k = ⌊log n − 4⌋ and m = ⌊n2^{−k}⌋ + 1, so that n ≤ m2^k, and imbed the matrices in matrices of order m2^k.
  2. The total is (5 + 2m)m²7^k − 6(m2^k)² < (5 + 2(n2^{−k} + 1))(n2^{−k} + 1)²7^k.
  3. Using 16·2^k ≤ n, that is < 2n³(7/8)^k + 12.03n²(7/4)^k = (2(8/7)^{log n − k} + 12.03(4/7)^{log n − k})·n^{log 7}.
  4. This is ≤ max_{4≤t≤5}(2(8/7)^t + 12.03(4/7)^t)·n^{log 7} ≤ 4.7·n^{log 7}.
- **Inversion.** Assume A is invertible and every division makes sense, as Gaussian elimination does. β_{m,0} is Gaussian elimination. For β_{m,k+1}, write A = (A₁₁ A₁₂; A₂₁ A₂₂) and A⁻¹ = (C₁₁ C₁₂; C₂₁ C₂₂), and compute:
  1. I = A₁₁⁻¹
  2. II = A₂₁·I
  3. III = I·A₁₂
  4. IV = A₂₁·III
  5. V = IV − A₂₂
  6. VI = V⁻¹
  7. C₁₂ = III·VI
  8. C₂₁ = VI·II
  9. VII = III·C₂₁
  10. C₁₁ = I − VII
  11. C₂₂ = −VI
- **Fact 3.** β_{m,k} inverts a matrix of order m2^k with m2^k divisions, at most (6/5)m³7^k − m2^k multiplications, and at most (6/5)(5 + m)m²7^k − 7(m2^k)² additions and subtractions.
- **Fact 4.** The inverse of order n takes fewer than 5.64·n^{log 7} operations. Linear systems and determinants follow similarly, with det A = (det A₁₁)·det(A₂₂ − A₂₁A₁₁⁻¹A₁₂).

**Led to.** The conventional n × n product takes n² dot products: n³ multiplications and n²(n − 1) additions. Strassen may have been trying to prove n³ a lower bound. His two ideas:
1. Divide-and-conquer recursion beats the conventional method if two 2 × 2 matrices can be multiplied with fewer than 8 multiplications, since the extra additions are repaid asymptotically.
2. Seven multiplications suffice. "Any high school student might have figured that out… nobody noticed because nobody had a reason to try."

Karatsuba and Ofman (1962) had multiplied two 2n-bit numbers with three n-bit multiplications, giving O(n^{log₂ 3}) ≈ n^1.58 against Θ(n²). Together the two papers established divide-and-conquer as a general tool. Strassen's method is tricky to implement correctly and efficiently, but practically useful. It opened the problem of the smallest exponent: at Lewis's writing no more than 2.373, with no lower bound above 2 known, and the exotic algorithms are not practical.

## 34. Cook, *The Complexity of Theorem-Proving Procedures* (1971)

**Set out to.** Show that any recognition problem solved by a polynomial time-bounded nondeterministic Turing machine can be "reduced" to deciding whether a propositional formula is a tautology. *Reduced* means that the first can be solved deterministically in polynomial time given an oracle for the second. The paper also introduces polynomial degrees of difficulty and shows that tautologyhood has the same degree as the subgraph isomorphism problem. Inputs are strings over a fixed, large finite alphabet Σ, and Turing machines are deterministic recognition devices unless stated otherwise.

**Construct.**
- **Formulas.** Atoms are a member of Σ followed by a binary number, so a formula of length n has about n/log n distinct atoms. The connectives are ∧, ∨ and ¬. The set of tautologies is recursive, but no lower bound is known.
- **Query machine.** A multitape Turing machine with a distinguished query tape and query, yes and no states. In a T-computation, whenever the machine enters the query state with u on the query tape, its next state is yes if u ∈ T and no if u ∉ T. This is an "oracle" that knows T.
- **P-reducibility.** S is P-reducible to T iff there are a query machine M and a polynomial Q(n) such that, for each w, the T-computation of M on w halts within Q(|w|) steps and accepts iff w ∈ S. The relation is transitive. Mutual P-reducibility is an equivalence relation, and its class deg(S) is the **polynomial degree of difficulty**.
- **ℒ\*** = deg({0}): the sets recognizable in polynomial time, the string analog of Cobham's ℒ.
- **Special sets.**
  1. {subgraph pairs}: strings Ḡ₁**Ḡ₂, each graph written as the rows of its adjacency matrix over {0, 1, *}, such that G₁ is isomorphic to a subgraph of G₂;
  2. {isomorphic graph pairs};
  3. {primes}, in binary;
  4. {DNF tautologies};
  5. D₃: DNF tautologies in which each disjunct has at most three conjuncts.

**Theorem 1.** If a set S is accepted by some nondeterministic Turing machine within polynomial time, then S is P-reducible to {DNF tautologies}. As a corollary, each of the sets 1–5 is P-reducible to {DNF tautologies}.

**Proof.** M accepts S within time Q(n). For input w, build a CNF formula A(w) that is satisfiable iff M accepts w. Then ¬A(w), put in DNF by De Morgan's laws, is a tautology iff w ∉ S, and the construction is polynomial in |w|.

Setup: M has one tape, infinite to the right, with squares 1, 2, …. Let T = Q(n). The tape symbols are σ₁, …, σ_ℓ, with σ₁ the blank, and the states are q₁, …, q_r. No square beyond T is ever scanned. The proposition symbols are:
- P^i_{s,t}, true iff square s at step t holds σ_i;
- Q^i_t, true iff at step t the machine is in state q_i;
- S_{s,t}, true iff at step t square s is scanned.

A(w) = B ∧ C ∧ D ∧ E ∧ F ∧ G ∧ H ∧ I, where:
- **B** = B₁ ∧ ⋯ ∧ B_T, and B_t says exactly one square is scanned at t: B_t = (S_{1,t} ∨ ⋯ ∨ S_{T,t}) ∧ ⋀_{1≤i<j≤T}(¬S_{i,t} ∨ ¬S_{j,t}).
- **C** says exactly one symbol is on each square at each time.
- **D** says the machine is in exactly one state at each time.
- **E** gives the initial conditions: E = Q⁰₁ ∧ S_{1,1} ∧ P^{i₁}_{1,1} ∧ P^{i₂}_{2,1} ∧ ⋯ ∧ P^{i_n}_{n,1} ∧ P¹_{n+1,1} ∧ ⋯ ∧ P¹_{T,1}, where w = σ_{i₁}⋯σ_{i_n} and q₀ is the initial state.
- **F, G, H** update the P's, Q's and S's properly. For example, G is the conjunction over t, i, j of G^t_{i,j}: if at t the machine is in q_i scanning σ_j, then at t + 1 it is in the state q_k that the transition function gives. G^t_{i,j} = ⋀_{s=1}^{T}(¬Q^i_t ∨ ¬S_{s,t} ∨ ¬P^j_{s,t} ∨ Q^k_{t+1}).
- **I** says the machine reaches an accepting state at some time; M is modified to continue trivially after accepting.

Lewis notes that the construction as presented is correct only for a deterministic machine. Cook's own copy carries a handwritten "(or states: nondeterminism)", and the nondeterministic case must be done somewhat differently.

**Theorem 2.** {tautologies}, {DNF tautologies}, D₃ and {subgraph pairs} are P-reducible to each other in pairs, so they share one polynomial degree. {primes} could not be added without deep number theory. {isomorphic graph pairs} probably could not be added without upsetting Corneil's conjecture that graph isomorphism is polynomial. D₂ is in ℒ*, by the Davis–Putnam procedure, so it cannot be added unless all of them are in ℒ*.

**Proof.** Each set reduces to {DNF tautologies}, which trivially reduces to {tautologies}. Two more reductions remain.
- **DNF → D₃.** Let A = B₁ ∨ ⋯ ∨ B_k with B₁ = R₁ ∧ ⋯ ∧ R_s, s > 3, and each R_i a literal. Then A is a tautology iff A′ = (P ∧ R₃ ∧ ⋯ ∧ R_s) ∨ (¬P ∧ R₁ ∧ R₂) ∨ B₂ ∨ ⋯ ∨ B_k is one, where P is a new atom. Repeat until every disjunct has at most three conjuncts; this is polynomial.
- **D₃ → subgraph.**
  1. Let A = C₁ ∨ ⋯ ∨ C_k with C_i = R_{i1} ∧ R_{i2} ∧ R_{i3}.
  2. Let G₁ be the complete graph on v₁, …, v_k. Let G₂ have vertices u_{ij} (1 ≤ i ≤ k, 1 ≤ j ≤ 3), with u_{ij} joined to u_{rs} iff i ≠ r and (R_{ij}, R_{rs}) is not an opposite pair (P, ¬P) or (¬P, P).
  3. A falsifying truth assignment exists iff there is a homomorphism φ: G₁ → G₂ with each φ(v_i) = u_{ij} for some j. The homomorphism says which literal of each disjunct to falsify, and the missing edges guarantee consistency.
  4. To force one-one maps to respect this, attach sufficiently distinct graphs H_i to v_i in G₁, and the same H_i to each of u_{i1}, u_{i2}, u_{i3} in G₂.
  5. Then G₁′ embeds in G₂′ iff A ∉ D₃.

**Discussion.**
- The theorems give strong evidence that tautologyhood is not easy, even in DNF. "It is fruitless to search for a polynomial decision procedure for the subgraph problem, since success would bring polynomial decision procedures to many other apparently intractable problems."
- {tautologies} is a good candidate for an interesting set not in ℒ*, and it is "worth spending considerable effort trying to prove this conjecture. Such a proof would be a major breakthrough in complexity theory."
- With numbers in m-adic notation, the relations accepted in nondeterministic polynomial time form ℒ+: relations of the form (∃y ≤ g_k(x̄)) R(x̄, y), with g_k(x̄) = 2^{(ℓ(max x̄))^k}, ℓ the dyadic length, and R in ℒ*.
- ℒ+ is the analog of the recursively enumerable sets, and tautologyhood is the analog of the halting problem. But the diagonal argument apparently cannot be adapted to show {tautologies} ∉ ℒ*.

**Led to.** Edmonds (1965) had written: "For practical purposes the difference between algebraic and exponential order is often more crucial than the difference between finite and nonfinite." Cobham (1965) defined a machine-independent class ℒ of functions computable in time "bounded by polynomials in the lengths of the numbers involved". Cook's ℒ* is today's 𝒫.

His crucial contributions are the definition of polynomial-time reducibility and the proof that everything accepted in nondeterministic polynomial time reduces to propositional formulas. The theorem is stated for tautologyhood (co-NP), not satisfiability (NP); the NP notation came soon after, with Karp (36) and Knuth. "The proof is easy—the brilliant insight was to describe computations by formulas in a distant echo of Turing" (6).

Leonid Levin independently found the same idea in "Universal Search Problems" (1973), hence the Cook–Levin Theorem. Lewis calls Berkeley's denial of tenure to Cook in 1970 "a blunder"; Cook went to Toronto. The paper set off the still unfinished search for whether 𝒫 = 𝒩𝒫, which is on the Clay Millennium Prize list (5).

## 36. Karp, *Reducibility among Combinatorial Problems* (1972)

**Set out to.** Show that "a large number of classic unsolved problems of covering, matching, packing, routing, assignment and sequencing are equivalent, in the sense that either each of them possesses a polynomial-bounded algorithm or none of them does." Problems on graphs, digraphs, integers, arrays, finite families of sets and boolean formulas are encoded as words over a finite alphabet, which makes them language-recognition problems. A problem counts as satisfactorily solved when an algorithm terminates within a number of steps bounded by a polynomial in the input length. The theorems "strongly suggest, but do not imply, that these problems, as well as many others, will remain intractable perpetually."

**Construct.**
- Models are one-tape Turing machines; any of a wide variety of models gives the same theory. Σ* is the set of finite strings of 0s and 1s, and a language is a subset of Σ*.
- **𝒫** is the languages recognizable in polynomial time by one-tape deterministic machines. **𝒩𝒫** is those recognizable by one-tape nondeterministic machines. **Π** is the functions Σ* → Σ* computable in polynomial time.
- **L ≼ M** (L is reducible to M) if there is f ∈ Π with f(x) ∈ M ⇔ x ∈ L. If M ∈ 𝒫 and L ≼ M, then L ∈ 𝒫. L and M are equivalent if L ≼ M and M ≼ L.
- **Edmonds's working hypothesis**, widely accepted: a problem is tractable iff it has a polynomial-bounded algorithm. Problems are specified by an INPUT and a PROPERTY. Polynomial examples:
  - SATISFIABILITY WITH AT MOST 2 LITERALS PER CLAUSE (Cook);
  - MINIMUM SPANNING TREE (Kruskal, 17);
  - SHORTEST PATH (Dijkstra 1959);
  - MINIMUM CUT (Edmonds and Karp).
- **𝒩𝒫 by quantification.** 𝒫^(2) is the sets of pairs ⟨x, y⟩ recognizable in polynomial time. L = {x : ∃y, ⟨x, y⟩ ∈ L^(2) and lg(y) ≤ p(lg(x))} is derived from it by polynomial-bounded existential quantification, and 𝒩𝒫 is the languages so derived. Loosely, L is in 𝒩𝒫 iff it is solvable by backtrack search of polynomially bounded depth. For k-coloring, guess the colors and check them in polynomial time.
- **SATISFIABILITY.** INPUT: clauses C₁, …, C_p. PROPERTY: there is S ⊆ {x₁, …, x_n, x̄₁, …, x̄_n} with (a) no complementary pair and (b) S ∩ C_k ≠ ∅ for every k.
- **Theorem 2 (Cook).** If L ∈ 𝒩𝒫, then L ≼ SATISFIABILITY. Cook stated it with a weaker reducibility, but his proof supports this one.
- **Corollary 1.** 𝒫 = 𝒩𝒫 ⇔ SATISFIABILITY ∈ 𝒫. If 𝒫 = 𝒩𝒫, then 𝒩𝒫 is closed under complement and the polynomial-bounded analog of Kleene's arithmetic hierarchy collapses. That is "strong circumstantial evidence that SATISFIABILITY ∉ 𝒫."
- **Definition 5.** L is (polynomial) complete if (a) L ∈ 𝒩𝒫 and (b) SATISFIABILITY ≼ L. **Theorem 3:** either all complete problems are in 𝒫 or none are, and the former holds iff 𝒫 = 𝒩𝒫.

**The 21 complete problems** (INPUT; PROPERTY):
1. SATISFIABILITY. By duality, equivalent to DNF tautology.
2. 0-1 INTEGER PROGRAMMING: integer matrix C and vector d; a 0-1 vector x with Cx = d.
3. CLIQUE: graph G, k; k mutually adjacent nodes.
4. SET PACKING: family {S_j}, ℓ; ℓ mutually disjoint sets.
5. NODE COVER: G′, ℓ; R ⊆ N′ with |R| ≤ ℓ and every arc incident with some node of R.
6. SET COVERING: {S_j}, k; at most k sets whose union is ⋃S_j.
7. FEEDBACK NODE SET: digraph H, k; at most k nodes such that every directed cycle contains one.
8. FEEDBACK ARC SET: digraph H, k; at most k arcs such that every cycle contains one.
9. DIRECTED HAMILTON CIRCUIT: a directed cycle including each node exactly once.
10. UNDIRECTED HAMILTON CIRCUIT.
11. SATISFIABILITY WITH AT MOST 3 LITERALS PER CLAUSE.
12. CHROMATIC NUMBER: G, k; ϕ: N → Z_k with adjacent u, v ⇒ ϕ(u) ≠ ϕ(v).
13. CLIQUE COVER: G′, ℓ; N′ is a union of ℓ or fewer cliques.
14. EXACT COVER: {S_j}, subsets of {u_i}; a disjoint subfamily whose union is {u_i}.
15. HITTING SET: {U_i}, subsets of {s_j}; W with |W ∩ U_i| = 1 for each i.
16. STEINER TREE: G, R ⊆ N, weights w: A → Z, k; a subtree of weight ≤ k containing R.
17. 3-DIMENSIONAL MATCHING: U ⊆ T × T × T; W ⊆ U with |W| = |T| and no two elements agreeing in any coordinate.
18. KNAPSACK: (a₁, …, a_n, b) ∈ Z^{n+1}; Σ a_j x_j = b has a 0-1 solution.
19. JOB SEQUENCING: execution times (T₁, …, T_p), deadlines (D₁, …, D_p), penalties (P₁, …, P_p), k; a permutation π with Σ_{j=1}^{p} [P_{π(j)} if T_{π(1)} + ⋯ + T_{π(j)} > D_{π(j)}, else 0] ≤ k.
20. PARTITION: (c₁, …, c_s); I ⊆ {1, …, s} with Σ_{h∈I} c_h = Σ_{h∉I} c_h.
21. MAX CUT: G, weights w: A → Z, W; S ⊆ N with total weight of arcs from S to its complement ≥ W.

**Fig 36.1, the reduction tree** (each problem is reduced to those under it):
- SATISFIABILITY → CLIQUE, 0-1 INTEGER PROGRAMMING, 3-SAT.
- CLIQUE → NODE COVER, SET PACKING.
- NODE COVER → FEEDBACK NODE SET, FEEDBACK ARC SET, DIRECTED HAMILTON CIRCUIT, SET COVERING.
- DIRECTED HAMILTON CIRCUIT → UNDIRECTED HAMILTON CIRCUIT.
- 3-SAT → CHROMATIC NUMBER.
- CHROMATIC NUMBER → EXACT COVER, CLIQUE COVER.
- EXACT COVER → 3-DIMENSIONAL MATCHING, KNAPSACK, HITTING SET, STEINER TREE.
- KNAPSACK → JOB SEQUENCING, PARTITION.
- PARTITION → MAX CUT.

**Sample reductions.** Karp writes that "the reader should have little difficulty in verifying" them.
- **SATISFIABILITY ≼ 0-1 INTEGER PROGRAMMING.** Set c_ij = 1 if x_j ∈ C_i, −1 if x̄_j ∈ C_i, and 0 otherwise; set b_i = 1 − (the number of complemented variables in C_i). Each clause then becomes the constraint Σ_j c_ij x_j ≥ b_i, which says at least one of its literals is true. The list states the problem as Cx = d.
- **SATISFIABILITY ≼ CLIQUE.** N = {⟨σ, i⟩ : σ a literal occurring in C_i}; A = {{⟨σ, i⟩, ⟨δ, j⟩} : i ≠ j and σ ≠ δ̄}; k = p, the number of clauses.
- **CLIQUE ≼ SET PACKING.** N = {1, …, n}; S_i = {{i, j} : {i, j} ∉ A}; ℓ = k.

**Not known to be complete:** GRAPH ISOMORPHISM, NONPRIMES, and LINEAR INEQUALITIES (a rational solution of Cx ≥ d). Lewis's update: NONPRIMES is in 𝒫 (Agrawal et al. 2004), LINEAR INEQUALITIES is in 𝒫 (Khachiyan 1979), and graph isomorphism remains unknown, though Babai (2016) made significant progress.

**Led to.** Karp's first lesson in combinatorial explosion came from shuffling cards to arrange a school calendar of classrooms and teachers. His reaction to Cook (34) was that many combinatorial problems resemble satisfiability: each searches an exponentially large space for a certificate that is small and easily verified. He defined 𝒫, 𝒩𝒫, polynomial-time reducibility (a version of the computable reducibility studied by his undergraduate advisor Hartley Rogers) and completeness. His 21 problems, each with a long history, turned out to be "all the same problem except for superficial variations", and hundreds more have been added.

𝒫 = 𝒩𝒫 is one of the most important unsolved problems of modern mathematics. Garey and Johnson's compendium (1979) gives the practical upshot: once a problem is shown 𝒩𝒫-complete, stop seeking an efficient exact solution and look for approximations or tractable special cases.

## 43. Knuth, *Big Omicron and Big Omega and Big Theta* (1976)

**Set out to.** Supply a lower-bound notation. O(f(n)) stands for a function whose magnitude is bounded above by a constant times f(n) for all large n, but people misuse O for lower bounds, rejecting a sorting method "because its running time is O(n²)". Knuth sees this in print quite often, hence the letter.

**The history.** Ω appears in the classical literature, most prominently in Titchmarsh's book on the Riemann zeta function, which devotes all of Chapter 8 to "Ω-theorems". Yet Knuth spent "a surprisingly fruitless hour" in the library looking for a reference, and more than half the prominent mathematicians he asked had never seen Ω(n²).
- Cajori's history of notations mentions none of them. Dozens of early-century books define O and o but not Ω.
- Landau traced O to Bachmann (1894) and invented o himself. He never used Ω; his student Pólya knew it but never used it either: "Like teacher, like pupil."
- On the fourth library trip Knuth found that Hardy and Littlewood introduced Ω in 1914, calling it new. Their Ω is the negation of o(f(n)): the absolute value exceeds Cf(n) for *infinitely many* n, for some small positive C.
- For computer science, the stronger requirement, *all large* n, is more appropriate.

**Definitions.**
- **O(f(n))** is the set of all g(n) such that there exist positive constants C and n₀ with |g(n)| ≤ Cf(n) for all n ≥ n₀. Read "order at most f(n)".
- **Ω(f(n))** is the set of all g(n) such that there exist positive constants C and n₀ with g(n) ≥ Cf(n) for all n ≥ n₀. Read "order at least f(n)".
- **Θ(f(n))** is the set of all g(n) such that there exist positive constants C, C′ and n₀ with Cf(n) ≤ g(n) ≤ C′f(n) for all n ≥ n₀. Read "order exactly f(n)".

These are for n → ∞. For f(x) as x → 0, use |x| ≤ x₀ in place of n ≥ n₀.

**Why these choices.**
- Changing Hardy and Littlewood's Ω is justified: it is not in wide use, there are other ways to say it, and the new Ω is mnemonic by analogy with O and easy to typeset.
- Θ was suggested independently by Bob Tarjan and Mike Paterson.
- The set definition was Ron Rivest's suggestion. Formulas then speak of sets of functions, with A + B = {a + b : a ∈ A, b ∈ B}. So "1 + O(n⁻¹)" is the set of functions 1 + g(n) with |g(n)| ≤ Cn⁻¹ for some C and all large n.
- Equalities are one-way. 1 + O(n⁻¹) = O(1), but not O(1) = 1 + O(n⁻¹); "=" really means ⊆. Knuth keeps the one-way equality, the practice of thousands of mathematicians.
- ω(f(n)) is the functions whose ratio to f(n) is unbounded, by analogy with o(f(n)). Knuth seldom needs the o-notations: "a good discipline to obtain O-estimates at all times, since it has taught me about more powerful mathematical methods".
- Only O has an absolute value. That is no anomaly, since O concerns a neighborhood of zero and Ω a neighborhood of infinity.
- The notations will not meet every need. A function like (log log n)^{cos n}, oscillating between log log n and 1/log log n, needs a local notation confined to one paper.

**Relational notations** came first.
- du Bois-Reymond (1870–71) wrote g(n) ≺ f(n) for g(n) = o(f(n)).
- Hardy's *Orders of Infinity* (1924) wrote:
  - g(n) ≼ f(n) for g(n) = O(f(n));
  - f(n) ≍ g(n) for g(n) = Θ(f(n));
  - f(n) ∼ g(n) when lim f(n)/g(n) = 1.
- Hardy proved that functions built from the arithmetic operations, exp and log satisfy exactly one of f ≺ g, f ≍ g with a finite nonzero limit, and f ≻ g.
- Vinogradov's f(n) ≪ g(n) for f ≼ g distorts the symbol. He is comfortable writing 200n² ≪ (n choose 2); Knuth is not.

Relational notations make transitivity clear and avoid one-way equalities. But "the main reason why O is so handy is that we can use it right in the middle of formulas", and in sentences and tables of running times. For example:

  (1 + H_n/n)^{H_n} = exp(H_n ln(1 + H_n/n))
   = exp(H_n(H_n/n + O((log n/n)²)))
   = exp(H_n²/n + O((log n)³/n²))
   = exp((ln n + γ)²/n + O((log n)³/n²))
   = (1 + O((log n)³/n²))·e^{(ln n + γ)²/n}

This would be "extremely cumbersome in relational notation."

On scratch paper Knuth uses ad hoc sets such as "(≤ 5n²)" and "(∼ 5n²)". He still publishes O, Ω and Θ: O is "so universally established and accepted", and the others are mnemonic. "I am not abandoning decimal notation although I find that octal (say) is more logical." "Well, I think I have beat this issue to death." He proposes that SIGACT members and journal editors adopt O, Ω and Θ as defined, "unless a better alternative can be found reasonably soon", with Hardy's relational notations where those fit better.

**Led to.** Lewis says that anyone calling Knuth the "greatest computer scientist of all time" might get an argument, but nobody would think them crazy. Knuth's unpublished notes on hashing with linear probing (1963) were among the first mathematical analyses of an algorithm, and his 1965 paper introduced LR parsers. A planned book on compilers became *The Art of Computer Programming*, because many basic algorithms lacked proper analysis until he supplied it. Knuth and his students created the analysis of algorithms as he wrote. Dissatisfied with the typesetting of the later volumes, he created TeX and METAFONT, which typeset this book.

Like Leibniz (2), he shaped good mathematical notation, here for algorithm analysis, and earlier he had standardized the use of "𝒫" and "𝒩𝒫". The impish title plays on the letters' names, "little o" (omicron) and "big o" (omega). Knuth scolded the great figures of the previous century for getting their definitions wrong and suggested, conversationally, that we all do it his way: "Which is exactly what happened; these notations are now the world's standards."
