# Cryptography

Papers 42, 45 and 46: Diffie and Hellman's public key cryptography and key exchange, the RSA method, and Shamir's threshold secret sharing.

## 42. Diffie & Hellman, *New Directions in Cryptography* (1976)

**Set out to.** "We stand today on the brink of a revolution in cryptography."
- Cheap digital hardware has made high-grade devices affordable for remote cash dispensers and computer terminals. That creates a need for systems that minimize secure key distribution channels and supply the equivalent of a written signature.
- Theory, from information theory and computer science, promises provably secure systems, "changing this ancient art into a science."
- Teleprocessing must be secure against eavesdropping and the injection of illegitimate messages. But privacy today requires a key sent in advance over a secure channel, by courier or registered mail, and the cost and delay of key distribution are "a major barrier" to private conversation between strangers.

**Conventional cryptography.** Cryptography is "the study of 'mathematical' systems for solving two kinds of security problems: privacy and authentication."
- **The two problems.** A **privacy** system prevents unauthorized extraction of information from a public channel. An **authentication** system prevents unauthorized injection of messages. On the telephone injection is the paramount threat, because the called party cannot tell which phone is calling. On radio eavesdropping is the threat, because it is passive and carries no legal hazard.
- **User authentication** is largely equivalent to message authentication, with the implicit message "I AM USER X".
- **Fig 42.1.** MESSAGE SOURCE → P → TRANSMITTER → C = S_K(P) → RECEIVER → P = S_K⁻¹(C). The CRYPTANALYST taps C and produces an estimate P̂. The KEY SOURCE supplies K to the transmitter and, over a shielded path, to the receiver. The secure channel cannot carry P itself, for reasons of capacity or delay.
- **Definition.** A **cryptographic system** is a single-parameter family {S_K}_{K∈{K}} of invertible transformations S_K: {P} → {C} from plaintext space to ciphertext space. The parameter K is the **key**, drawn from the finite **keyspace** {K}.
- **Computationally secure** systems would succumb to unlimited computation. **Unconditionally secure** systems resist any attack, however much computation is spent.
  - Unconditional security comes from multiple meaningful solutions: the substitution cryptogram XMD could be "now", "and" or "the".
  - The one time pad is the only unconditionally secure system in common use, and it is impractical.
  - The paper deals with computationally secure systems, using "only a few hundred bits of key". **Computationally infeasible** means a cost that is "finite but impossibly large".
- **Stream and block ciphers.** **Stream ciphers** add a pseudorandom bit sequence modulo 2. **Block ciphers** transform large blocks so that a small input change makes a major output change. The paper prefers block ciphers, because that **intentional error propagation** serves authentication: noise that turns "erase file 7" into "erase file 8" also corrupts the authentication information, and the message is rejected.
- **Attacks,** in increasing strength:
  - **Ciphertext only** attacks use statistics (e is 13 percent of English letters) and probable words ("Dear Sir:"). A system that succumbs is "totally insecure".
  - **Known plaintext** attacks use plaintext from press releases, product announcements and declassified correspondence. A system that cannot resist one is "not considered secure".
  - **Chosen plaintext** attacks are harder but approximable: submit a proposal to a competitor, who enciphers it to headquarters.
- **Assumptions.** The opponent is assumed to know the general system {S_K}; Lewis notes this is Kerckhoffs's principle (1883), "often unwisely been ignored". "Cryptanalysis is a system identification problem."
- **The IFF attack.** The chosen plaintext attack is also called the IFF attack, after identification friend or foe systems. Over enemy territory the enemy can send the challenges; the counter is challenges that "need not be unpredictable, but only nonrepeating."
- **Two new threats.** The **compromise of the receiver's authentication data**: password tables are more vulnerable than individuals. And **dispute**: a message sent and repudiated, or alleged when none was sent, like a stockbroker forging orders or a client disowning one. Both need ways to verify authenticity without being able to generate it.

**Construct: public key cryptosystem.** Cryptography had been "a derivative security measure", limited to people with prior preparation. n users form (n² − n)/2 potential pairs. In Fig 42.2 there is no secure key channel: each end has its own key source, and the cryptanalyst hears the whole two-way public channel.

**Definition.** A **public key cryptosystem** is a pair of families {E_K}_{K∈{K}} and {D_K}_{K∈{K}} of algorithms for invertible transformations E_K: {M} → {M} and D_K: {M} → {M} on a finite message space {M}, such that:
1. for every K, E_K is the inverse of D_K;
2. for every K and M, E_K and D_K are easy to compute;
3. for almost every K, any easily computed algorithm equivalent to D_K is computationally infeasible to derive from E_K;
4. for every K, it is feasible to compute the inverse pair E_K and D_K from K.

Property 3 lets E go into a public directory with the user's name and address while D stays secret and is never communicated: a **multiple access cipher**. Property 4 means a true random number generator, such as a noisy diode, plus an algorithm that turns K into the E–D pair. The public file needs elaborate write protection but no read protection, and since it changes infrequently, that is economical.

**Two attempts.**
- **The matrix example** is "suggestive, although unfortunately useless". E is an invertible binary n × n matrix, c = Em and m = Dc with D = E⁻¹, and enciphering costs about n² operations. E is built from I by elementary row and column operations, and D by their inverses in reverse order. But inverting E takes only about n³ operations, so the work ratio is at most n.
- **A one-way compiler** is the practical idea: turn an easily understood high-level program into an incomprehensible machine-language program, feasible to compile and infeasible to reverse.

**Public key distribution.** Two users exchange messages over the public channel until they share a key, and an eavesdropper finds it computationally infeasible to compute the key from what was overheard.
- **Merkle's** partial solution makes the cryptanalyst's cost grow as n² where the users' cost is n. With a one-megabit setup that gives a ratio of about 10,000 to 1, which is too small.
- **The new system** has three advantages: only one "key" is exchanged, the cryptanalytic effort appears to grow exponentially in the legitimate effort, and it ties into a public file that authenticates the users to each other.
- **The one-way function.** It rests on the apparent difficulty of computing logarithms over GF(q), q prime:

  Y = α^X mod q, for 1 ≤ X ≤ q − 1, with α a fixed primitive element of GF(q)

  X = log_α Y mod q, for 1 ≤ Y ≤ q − 1

  - Computing Y from X takes at most 2 log₂ q multiplications, as in α¹⁸ = (((α²)²)²)² × α².
  - Computing X from Y takes on the order of q^(1/2) operations with the best known algorithm, for carefully chosen q.
- **The protocol (Diffie–Hellman key exchange):**
  1. Each user i picks a random X_i, uniform from {1, 2, …, q − 1}, keeps it secret, and places Y_i = α^{X_i} mod q in the public file.
  2. Users i and j share K_ij = α^{X_i X_j} mod q.
  3. User i computes K_ij = Y_j^{X_i} mod q = (α^{X_j})^{X_i} mod q = α^{X_i X_j} mod q, and user j computes Y_i^{X_j} mod q.
- **The attacker** must compute K_ij from Y_i and Y_j, for example K_ij = Y_i^{(log_α Y_j)} mod q. If logarithms are easy, the system is broken. The converse is unproven, but "neither do we see any way to compute K_ij from Y_i and Y_j without first obtaining either X_i or X_j."
- **The numbers.** With q a prime slightly less than 2^b, exponentiation takes at most 2b multiplications mod q, while logarithms take q^(1/2) = 2^(b/2) operations. For b = 200: at most 400 multiplications against 2^100, about 10^30, operations.

**One-way authentication.** This is "perhaps an even more serious barrier" than key distribution: "Authentication is at the heart of any system involving contracts and billing. Without it, business cannot function." A written signature is easy for anyone to recognize and impossible for anyone but the signer to produce. "Since any digital signal can be copied precisely, a true digital signature must be recognizable without being known."

**The login problem.** The password directory must be secure, and operators' legitimate access to it compounds the risk.
- The fix: store f(PW) instead of PW, and at login accept a proffered X iff f(X) = f(PW).
- f is computed once per login, so a million instructions, about $0.10 "at bicentennial prices", is a reasonable cost. If inverting f needs 10^30 or more instructions, someone holding the directory still cannot recover PW.
- Presenting f(PW) does not work, because login computes f(f(PW)), so f can be public.
- R. M. Needham first used one-way functions for login.

**Definition.** "A function f is a one-way function if, for any argument x in the domain of f, it is easy to compute the corresponding value f(x), yet, for almost all y in the range of f, it is computationally infeasible to solve the equation y = f(x) for any suitable argument x."
- This differs from mathematical noninvertibility. A constant function is noninvertible but trivially solved, since any x works, so f must not be too degenerate.
- Finding a root of a polynomial is harder than evaluating it; Purdy used sparse polynomials of very high degree over finite fields.
- The login protocol protects stored data, but the true password still crosses the line, and there is no protection against dispute.

**Signatures from a public key cryptosystem.** A "deciphers" M with her secret key and sends D_A(M). B authenticates it by "enciphering" with A's public E_A and keeps D_A(M) as proof. Anyone can recover M, but only A could have produced it, so one-way authentication follows immediately from a public key cryptosystem.

**Lamport's one-time scheme,** a partial solution for message authentication.
- **The scheme.** Take a one-way f on k-bit vectors, with k on the order of 100. For an N-bit message, the transmitter keeps 2N random vectors x₁, X₁, …, x_N, X_N secret, and the receiver holds their images y₁, Y₁, …, y_N, Y_N. To send m, transmit x_i if m_i = 0 and X_i if m_i = 1; the receiver applies f and recognizes y_i or Y_i. "The receiver is incapable of forging a change in even one bit of m."
- **Compression.** The scheme expands data about 100-fold. For long messages, first map m by a one-way g to n ≈ 50 bits and authenticate that. With N = 10^6 and k = 100, that is kn = 5000 authentication bits, a 5 percent expansion (15 percent counting the initial exchange of y's and Y's). g must be strong: hard to find a different preimage even given m.
- **User authentication.** The user holds a secret X and gives the system f^T(X). At time t the authenticator is f^{T−t}(X), checked by applying f^t, and past responses cannot forge future ones. But with t ticking every second and a password lasting a month, T = 2.6 million, and each login iterates f about 1.3 million times. A fast way to compute f^(2^n) would fix that, but it might preclude f being one-way.

**Interrelations and trap doors.**
- **Result.** "A cryptosystem which is secure against a known plaintext attack can be used to produce a one-way function": fix P₀ and let f(X) = S_X(P₀) (Fig 42.3). Solving f(X) = Y means finding a key from one known plaintext–cryptogram pair.
  - "A good key generator is, almost by definition, a one-way function."
  - f need not be uniquely invertible. A good cipher's f behaves like a random mapping: the probability that Y has k + 1 preimages is about e⁻¹/k!, so the expected number of preimages is only 2.
  - Evans et al. proposed f(X) = S_X(X), which is hard even for simple S but loses the equivalence with known-plaintext security.
- **Result.** "A public key cryptosystem can be used to generate a one-way authentication system." The converse does not appear to hold, so public key cryptosystems are strictly harder. A public key cryptosystem also serves as a public key distribution system, but not conversely.
- **Trap-door one-way functions.** A public key system is a set of **trap-door one-way functions**: simply computed inverses exist, but given the forward algorithm it is infeasible to find one without the **trap-door information**, such as the random bits that produced the E–D pair.
  - A **trap-door cipher** resists everyone except its designer, who could break it after selling it while "falsely" keeping "his reputation as a builder of secure systems". Like a combination lock, the advantage lies in information, not cleverness: forget the combination and you are no better off.
  - **Result.** "A trap-door cryptosystem can be used to produce a public key distribution system": A sends B an arbitrary plaintext–cryptogram pair under a random key, and B, holding the trap door, solves for the key.
  - There is little evidence that trap-door ciphers exist, but they are a "distinct possibility" to remember "when accepting a cryptosystem from a possible opponent".
- **Quasi one-way functions.** A **quasi one-way function** has an easily computed inverse that no one, not even the designer, can feasibly find. Losing the trap-door information turns a trap-door one-way function into a quasi one-way one, and whether to count those as one-way is "entirely a matter of definition". A **quasi secure cipher** likewise has an efficient attack that is infeasible to find.

**Computational complexity.** "Cryptography differs from all other fields of endeavor in the ease with which its requirements may appear to be satisfied."
- **History.** Sixteenth- and seventeenth-century counting arguments for astronomical numbers of keys fooled even Cardano. When such systems were repeatedly broken, proofs gave way to certification by cryptanalytic assault. Shannon showed the one time pad offers perfect secrecy, but provably secure systems of that kind are unwieldy.
- **No unconditional security.** Neither public key cryptosystems nor one-way authentication can be unconditionally secure, since the public information determines the secret uniquely within a finite set.
- **𝒫 and 𝒩𝒫.** 𝒫 is the functions computable by a deterministic Turing machine in polynomial time; "it is more accurate to say that a function not in this class must be hard to compute for at least some inputs." 𝒩𝒫 is the problems solvable in polynomial time on a "nondeterministic" computer with unlimited parallelism, and Karp's 𝒩𝒫 complete problems (36) are its hardest. But complexity theory measures the worst case, and cryptography needs typical-case difficulty.
- **Result.** "The cryptanalytic difficulty of a system whose encryption and decryption operations can be done in 𝒫 time cannot be greater than 𝒩𝒫": guess the key nondeterministically and verify in polynomial time.
- **The knapsack one-way function.** f(x) = a · x, where a = (a₁, …, a_n) is a known vector of integers and x a binary vector. Inverting it is the knapsack problem: find a subset of the a_i summing to y. Exhaustive search over 2^n subsets is infeasible for n above 100 or so, but the parameters matter:
  - With n = 100 and 32-bit a_i, y has at most 39 bits, so f is highly degenerate and needs on average only 2^38 tries.
  - With a_i = 2^(i−1), inversion is just the binary decomposition of y.
- **Credit.** John Gill of Stanford suggested exponentiation mod q.

**Historical perspective.** Production cryptanalysis was the work of professionals, but innovation came mostly from amateurs. Thomas Jefferson invented a system still in use in World War II, and the rotor machine was invented simultaneously by four amateurs. The authors hope to inspire others, whose participation has been discouraged "by a nearly total government monopoly."

**Led to.** Few papers announce so boldly that they are on "the brink of a revolution." (Turing (6), by contrast, felt unappreciated after his Entscheidungsproblem paper, which drew only two reprint requests.)
- **The two problems it attacked.**
  - **Key distribution:** it was "fundamentally no easier to transmit the key securely … than it would have been to send securely the unencoded message itself," which made secure encryption "a monopoly of the powerful and the wealthy".
  - **Digital signatures.**
- **The idea.** Parties at a distance agree on a key over an insecure channel without ever transmitting it. Even Shannon had seemed to dismiss this: "The key must be transmitted by non-interceptible means from transmitting to receiving points."
- **Signatures.** The paper's signature proposals are mathematically different from its key distribution method, and a unified solution waited for RSA (45).
- **Priority.** Diffie credits Ralph Merkle, as a Berkeley undergraduate in 1974, with the basic public-key idea, though he could get no one to listen. GCHQ scientists had it in the 1970s, classified.
- **Number theory.** Modular exponentiation's security depends on the discrete logarithm being hard, which set off a search for fast algorithms and made cryptography mainstream research. Number theory, which G. H. Hardy had proudly proclaimed of no practical use, "became the most relevant field of mathematics."
- **What held up.** No fast discrete logarithm has been found. But Shamir (1984) showed the paper's knapsack proposal for one-way signatures fatally flawed.

The paper matters "as much for opening a new sociopolitical world as for its technical importance". For centuries cryptography had been an intellectual backwater, its knowledge assumed to be kept under wraps by governments. This paper began open exchange about cryptography and put encryption, essential to internet commerce and banking, in the hands of ordinary citizens. Governments then tried to control it, through export controls on encryption software and back doors in communication systems and cell phones. The debate between freedom of communication and protection against hostile actors continues.

## 45. Rivest, Shamir & Adleman, *A Method for Obtaining Digital Signatures and Public-Key Cryptosystems* (1978)

**Set out to.** Implement Diffie and Hellman's public-key cryptosystem (42), which they had presented as a concept with no practical implementation. The method's novel property is that publicly revealing the encryption key does not reveal the decryption key. That has two consequences:
1. Couriers are unnecessary: encipher with the recipient's public key, and only the recipient can decipher.
2. A message can be "signed" with the privately held decryption key and verified by anyone with the public encryption key. "Signatures cannot be forged, and a signer cannot later deny the validity of his signature."

The method: represent the message as a number M, raise it to a publicly specified power e, and take the remainder modulo a publicly specified product n of two large secret primes p and q. Decrypt with a secret power d, where e · d ≡ 1 (mod (p − 1) · (q − 1)). Security rests in part on the difficulty of factoring n.

**Construct: public-key cryptosystem.** Each user puts an encryption procedure E in a public file and keeps the decryption procedure D secret. Four properties:
- (a) D(E(M)) = M (45.1);
- (b) E and D are easy to compute;
- (c) revealing E does not reveal an easy way to compute D;
- (d) E(D(M)) = M (45.2).

A procedure is a general method plus a key, and everyone can share the method, so security rests on the key. Revealing E reveals only a hopelessly inefficient way to decrypt: try every M until E(M) = C.
- **Trap-door one-way function:** an E satisfying (a)–(c). It is "one-way" because it is easy in one direction and apparently very hard in the other, and "trap-door" because the inverse is easy with private trap-door information.
- **Trap-door one-way permutation:** one that also satisfies (d). Such an E must be one-to-one and onto, so every ciphertext is a permissible message. Property (d) is needed only for signatures.
- **The cast.** The two users are "A and B (also known as Alice and Bob)", with E_A, D_A, E_B, D_B.

**Privacy.** An eavesdropper hears only "garbage".
- The National Bureau of Standards' Data Encryption Standard, developed at IBM, lacks property (c). Like every classical method, it suffers the **key distribution problem**: a private transaction such as a courier must come first.
- Bob sends Alice E_A(M), and only Alice can compute D_A(E_A(M)) = M. She replies with E_B. The only setup is each receiver placing an enciphering algorithm in the public file.
- Without a public file, the two can exchange encryption keys directly, assuming the intruder cannot modify or insert messages.
- RSA can also "bootstrap" a standard scheme: the first message carries an NBS key. NBS is probably faster in special hardware; RSA may be faster on general-purpose computers, since multiprecision arithmetic is simpler than complicated bit manipulation.

**Signatures.** A signature is stronger than authentication: the recipient can convince a "judge" that the signer sent the message and that the recipient did not forge it. It must depend on the message as well as the signer, or electronic "cutting and pasting" would be undetectable. Signatures need property (d), because decryption is applied to messages that were never enciphered.
1. Bob computes S = D_B(M), encrypts E_A(S) for privacy, and sends it. M itself need not be sent, since it is computable from S.
2. Alice computes D_A to get S, then M = E_B(S).
3. The pair (M, S) is like a signed paper document.
   - Bob cannot deny it, since no one else could produce D_B(M).
   - Alice can show a judge that E_B(S) = M.
   - Alice can neither alter M to M′, which would need D_B(M′), nor forge Bob's signature on any other message.
- **Uses.** Electronic checks signed by a device in the home terminal and sent by electronic mail, with unique check numbers so the bank honors only the first copy. Fast devices could sign every word of a telephone conversation. The device works as a "hardware subroutine" rather than being wired in between terminal and channel.
- **The public file.** An intruder might forge messages purporting to come from the public file. That danger disappears if the file signs every message it sends, checked with E_PF, which each user receives in person on joining. "The need for a courier between every pair of users has thus been replaced by the requirement for a single secure meeting between each user and the public-file manager." Alternatively, a book like a telephone directory could list every key.

**The method.**
- **Keys.** The public encryption key is (e, n), and the private decryption key is (d, n).
- **Messages.** A message is an integer 0 … n − 1, after breaking a long message into blocks. This representation is not encryption, just numeric form.
- **Encryption and decryption.** C ≡ E(M) ≡ M^e (mod n), and D(C) ≡ C^d (mod n). Encryption does not increase message size.
- **Key choice:**
  - n = p · q, with p and q very large "random" primes. The difficulty of factoring n hides them, and hides how d derives from e.
  - d is a large random integer with gcd(d, (p − 1) · (q − 1)) = 1.
  - e is the multiplicative inverse of d: e · d ≡ 1 (mod (p − 1) · (q − 1)).
- **Related schemes.** This is not Diffie and Hellman's exponentiation, which is key agreement and not a trap-door permutation. Pohlig and Hellman's related scheme exponentiates modulo a prime.

**Why it works.**
- **Euler–Fermat:** for M relatively prime to n, M^φ(n) ≡ 1 (mod n) (45.3). φ(n), Euler's totient, counts the positive integers less than n that are relatively prime to n. φ(p) = p − 1 for prime p, and φ(n) = φ(p) · φ(q) = (p − 1) · (q − 1) = n − (p + q) + 1.
- **The inverse.** d is relatively prime to φ(n), so it has an inverse e in the ring of integers mod φ(n): e · d ≡ 1 (mod φ(n)) (45.4).
- **The argument.** D(E(M)) ≡ (M^e)^d and E(D(M)) ≡ (M^d)^e, both ≡ M^{e·d} ≡ M^{k·φ(n)+1} (mod n) for some integer k.
  1. If p does not divide M, then M^{p−1} ≡ 1 (mod p), and since p − 1 divides φ(n), M^{k·φ(n)+1} ≡ M (mod p). This holds trivially when M ≡ 0 (mod p).
  2. The same holds mod q.
  3. So M^{e·d} ≡ M (mod n) for all 0 ≤ M < n, and E and D are inverse permutations. (The improved proof is credited to Rich Schroeppel.)

**Algorithms.**
- **Exponentiation by repeated squaring and multiplication** takes at most 2 log₂(e) multiplications and 2 log₂(e) divisions:
  1. Let e_k e_{k−1} … e₁ e₀ be the binary representation of e.
  2. Set C := 1.
  3. For i = k, k − 1, …, 0: set C := C² mod n; if e_i = 1, set C := C · M mod n.
  4. Halt; C is the encrypted M.

  It is "half as good as the best". Enciphering and deciphering are the same operation, so a few special-purpose chips suffice. A high-speed computer encrypts a 200-digit message in a few seconds, and the time per block grows no faster than the cube of the number of digits of n.
- **Large primes.** Use 100-digit p and q, so n has 200 digits. Generate odd random 100-digit numbers until one is prime; by the prime number theorem, about (ln 10^100)/2 = 115 are tested.
  - **Solovay–Strassen test.** Pick a uniform from {1, …, b − 1} and test gcd(a, b) = 1 and J(a, b) ≡ a^((b−1)/2) (mod b) (45.5), where J is the Jacobi symbol. A prime always passes; a composite fails with probability at least ½. Passing for 100 random a leaves a 1 in 2^100 chance of compositeness, and if a composite slips through, the receiver will probably notice that decryption fails.
  - **The Jacobi symbol,** for odd b, a ≤ b and gcd(a, b) = 1: J(a, b) = if a = 1 then 1, else if a is even then J(a/2, b) · (−1)^((b²−1)/8), else J(b mod a, a) · (−1)^((a−1)·(b−1)/4).
  - **Hardening against factoring.** p and q should differ in length by a few digits, p − 1 and q − 1 should contain large prime factors, and gcd(p − 1, q − 1) should be small. For example, take a large random prime u and let p be the first prime in the sequence i · u + 1, i = 2, 4, 6, …. Deciding primality of a 100-digit number takes several seconds.
- **Choosing d.** Any prime greater than max(p, q) works, drawn from a set large enough to defeat direct search.
- **Computing e** uses a variation of Euclid's algorithm.
  1. Let x₀ = φ(n), x₁ = d, and x_{i+1} = x_{i−1} (mod x_i) until x_k = 0; then gcd(x₀, x₁) = x_{k−1}.
  2. Track a_i and b_i with x_i = a_i · x₀ + b_i · x₁.
  3. If x_{k−1} = 1, then b_{k−1} is the inverse of x₁ (mod x₀). Since k < 2 log₂(n), this is very fast.

  If e < log₂(n), choose another d, so that every message except 0 and 1 undergoes "wrap-around", reduction modulo n.

**Security.** There are no techniques for proving a cryptosystem secure; the only test is whether anyone can break it. The NBS standard was "certified" that way, by seventeen fruitless man-years at IBM. Every obvious attack on RSA is at least as hard as factoring n, a problem worked on for three hundred years, since Fermat and Legendre. No one can factor a 200-digit number in reasonable time, so the system is "already been partially 'certified'".
- **Factoring n** yields φ(n) and then d. Factoring seems much harder than primality testing.
- **Computing φ(n) without factoring** would factor n anyway: p + q follows from n and φ(n) = n − (p + q) + 1, p − q is the square root of (p + q)² − 4n, and q is half the difference of the two. This is also why n must be composite, since φ(n) is trivial for prime n.
- **Determining d.** Once d is known, e · d − 1 is a multiple of φ(n), and Miller showed that n can be factored from any multiple of φ(n). Equivalent d′ differ by lcm(p − 1, q − 1), and finding any one of them factors n.
- **e-th roots.** "Computing e th roots modulo n without factoring n" is not a well-known hard problem, but the authors are "reasonably confident that it is computationally intractable". "The reader is challenged to find a way to 'break' our method."

**Avoiding reblocking.** A signature's n may be larger than the encryption n. One fix uses a threshold h, say 10^199, with two public pairs per user, every signature n below h and every enciphering n above it. Another (Levine and Brawley) uses one pair with h < n < 2h: if a ciphertext exceeds h, re-encipher until it does not.

**Conclusions.** Security rests in part on factoring, which deserves close study. "The reader is urged to find a way to 'break' the system." This is the only candidate trap-door one-way permutation the authors know, and they urge a search for others.

**Led to.** A copy of Diffie–Hellman quickly reached MIT, and the three set out to find a public-key system serving both key distribution and signatures, using factoring. When the Web went commercial in the late 1990s, RSA was widely deployed for internet security. "Every banking transaction, e-commerce purchase, and rideshare summons involves an unspoken key exchange."

Lewis calls it a "remarkable testament to the beauty of algorithms and to the utility of even the purest mathematics". It is easy to describe if you know the eighteenth-century mathematics of integers, and it rests on an unproven premise: that there is no fast factoring algorithm.
- Gauss (1801) wrote that the best factoring methods "try the patience of even the practiced calculator", and urged that "every possible means be explored for the solution of a problem so elegant and so celebrated".
- William Jevons, inventor of the logic piano, noted in 1874 the asymmetry we now call one-way: multiplying two numbers is a simple and infallible process, but factoring a large number "is quite another matter".
- The exponential cost of factoring is often asserted and never proved.

RSA remains unbroken as far as is known, with key lengths increased in practice; elliptic-curve systems are not proved secure either. The book includes the early sections because they introduce "Alice" and "Bob". The three founded a company in 1983 (RSA Security, later part of EMC and then Dell) and won the 2002 Turing Award. Shamir's other contributions include secret sharing (46).

## 46. Shamir, *How to Share a Secret* (1979)

**Set out to.** Generalize a puzzle from Liu (1968). Eleven scientists are working on a secret project, and the documents in a cabinet should open iff six or more are present. What is the smallest number of locks, and keys per scientist? The minimal answer, 462 locks and 252 keys per scientist, is impractical and gets exponentially worse as the group grows.

**Construct: (k, n) threshold scheme.** Divide secret data D, such as a safe combination, into n pieces D₁, …, D_n so that:
1. knowledge of any k or more pieces makes D easily computable;
2. knowledge of any k − 1 or fewer leaves D completely undetermined, with all its possible values equally likely.

**Why it matters.** Keys need management: "further encryptions change the problem rather than solve it". A single well-guarded copy, in a computer, a brain or a safe, can be lost to breakdown, sudden death or sabotage, and multiple copies multiply the breaches.
- With n = 2k − 1, D survives the destruction of ⌊n/2⌋ = k − 1 pieces, and opponents who expose k − 1 of the remaining k still cannot reconstruct it.
- **Safety against convenience.** A company signs checks digitally, using RSA (45). Giving every executive the key is convenient and easy to misuse; requiring all of them is safe but inconvenient. A (3, n) scheme, like the requirement of three signatures, gives each executive a magnetic card with one D_i.
  - The signature device accepts any three cards, generates a temporary copy of the key D, and later destroys it.
  - The device holds no secret and needs no protection against inspection.
  - An unfaithful executive needs at least two accomplices.
- For mutually suspicious parties, unanimous consent gives everyone a paralyzing veto. Choosing k and n gives "any sufficiently large majority the authority to take some action while giving any sufficiently large minority the power to block it."

**The scheme: polynomial interpolation.** Given k points (x₁, y₁), …, (x_k, y_k) with distinct x_i, there is one and only one polynomial q(x) of degree k − 1 with q(x_i) = y_i for all i.
1. Pick a random polynomial q(x) = a₀ + a₁x + ⋯ + a_{k−1}x^{k−1} of degree k − 1 with a₀ = D.
2. Compute the pieces D₁ = q(1), …, D_i = q(i), …, D_n = q(n).
3. Any k pieces, with their indices, give the coefficients of q(x) by interpolation, and D = q(0). k − 1 pieces are not enough.

**In modular arithmetic.** Work modulo a prime p larger than both D and n, so the integers mod p form a field. Choose a₁, …, a_{k−1} uniformly from the integers in [0, p), and compute the D_i mod p.
- An opponent holding k − 1 pieces finds that, for each candidate D′ in [0, p), exactly one polynomial q′(x) of degree k − 1 has q′(0) = D′ and q′(i) = D_i. These p polynomials are equally likely, so there is "absolutely nothing the opponent can deduce about the real value of D."
- Evaluation and interpolation take O(n log² n) with efficient algorithms, but straightforward quadratic algorithms are fast enough.
- A long D can be broken into shorter blocks, which avoids multiprecision arithmetic. The smallest usable p is n + 1, since n + 1 distinct arguments are needed, and a sixteen-bit modulus suffices for up to 64,000 pieces.

**Properties,** in contrast with mechanical locks and keys:
1. Each piece is no larger than the original data.
2. With k fixed, pieces can be added or deleted dynamically as executives join or leave, without affecting the others. A piece is truly deleted only when the leaver makes it inaccessible, even to himself.
3. The pieces can be changed without changing D, by choosing a new polynomial with the same free term. Frequent changes enhance security, because exposed pieces cannot accumulate unless they come from the same edition of q(x).
4. Giving tuples of values creates a hierarchy. With the president holding three values, each vice-president two and each executive one, a (3, n) scheme lets checks be signed by any three executives, any two of whom one is a vice-president, or the president alone.

Any functions that are easy to evaluate and interpolate can replace polynomials. G. R. Blakley (1979) gave a different, somewhat less efficient scheme.

**Led to.** Networked information gave secrecy and privacy new dimensions, and playful metaphors like this 1968 puzzle took on grave significance. Papers 42 and 45 promised communication secure barring unrealistic computational effort, a promise not yet mathematically verified. This paper instead gives a protocol under which it is "provably impossible" for a smaller cabal to expose the secret, "even by devoting unlimited resources". Secret sharing now runs to many thousands of papers.

Shamir, the RSA coauthor (45), met an apparently impossible challenge with a "beautiful, short solution using only high school mathematics". The paper is practically about distributed systems, yet says nothing about computer technology. Computer science, Lewis notes, is full of simply stated problems begging for elegant solutions.
