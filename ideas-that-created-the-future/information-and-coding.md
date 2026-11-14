# Information and coding

Papers 12 and 13: Shannon's measure of information and Hamming's codes that detect and correct errors.

## 12. Shannon, *A Mathematical Theory of Communication* (1948)

**Set out to.** Build a general theory of communication. Earlier work (Nyquist 1924 and 1928, Hartley 1928) had laid foundations, and PCM and PPM (pulse code and pulse position modulation) had shown that bandwidth can be traded for signal-to-noise ratio. Shannon adds the effect of noise in the channel and the savings available from the statistical structure of the message and the nature of its destination.

"The fundamental problem of communication is that of reproducing at one point either exactly or approximately a message selected at another point." Meaning is set aside: "These semantic aspects of communication are irrelevant to the engineering problem. The significant aspect is that the actual message is one selected from a set of possible messages." The system must be designed for every possible selection.

**Construct.**
- **Measure of information.** For a finite set of messages, any monotonic function of their number can measure the information in a choice. Following Hartley, Shannon takes the **logarithm**, for three reasons:
  1. It is practically more useful. Time, bandwidth and number of relays vary linearly with the log of the number of possibilities: adding a relay doubles the states and adds 1 to log₂, and doubling the time roughly squares the number of messages.
  2. It is nearer intuition: two punched cards should have twice the capacity of one.
  3. It is mathematically more suitable.
- **Units.**
  - Base 2 gives **binary digits**, or **bits**, a word Shannon credits to J. W. Tukey. N bistable devices store N bits, since log₂ 2ᴺ = N.
  - Base 10 gives decimal digits. Since log₂ M = log₁₀ M / log₁₀ 2 = 3.32 log₁₀ M, a decimal digit is about 3⅓ bits.
  - Base e gives natural units. To change from base a to base b, multiply by log_b a.
- **The communication system (Fig 12.1)** has five parts, with a **noise source** acting on the signal between transmitter and receiver:
  1. The **information source**. Its message may be a sequence of letters; a function f(t), as in telephony; f(x, y, t), as in television; several functions, as in multiplex or three-dimensional sound; or combinations.
  2. The **transmitter**, which turns the message into a **signal**. In telephony, sound pressure becomes current. In telegraphy, dots, dashes and spaces. In PCM, the message is sampled, compressed, quantized and encoded.
  3. The **channel**, the medium: wires, coaxial cable, a radio band, a light beam.
  4. The **receiver**, which inverts the transmitter.
  5. The **destination**, a person or a thing.

  Systems are **discrete** (telegraphy), **continuous** (radio, TV) or **mixed** (PCM speech). The discrete case also covers computing machines and telephone exchanges.

**The discrete noiseless channel.** A sequence of choices from symbols S₁, …, S_n, each with duration t_i; only certain sequences may be allowed.
- **Telegraph:** a dot is closure for 1 unit and open for 1; a dash is closure for 3 units and open for 1; a letter space is 3 units open; a word space is 6 units open; spaces may not be adjacent.
- **Teletype:** 32 symbols of equal duration, any sequence allowed, so 5 bits per symbol and 5n bits per second for n symbols per second. That is the maximum; the actual rate depends on the source.
- **Capacity:** C = lim_{T→∞} log N(T) / T, where N(T) is the number of allowed signals of duration T.
- If all sequences are allowed, N(t) = N(t − t₁) + … + N(t − t_n). Then N(t) grows like X₀ᵗ, where X₀ is the largest real root of X^{−t₁} + … + X^{−t_n} = 1, and C = log X₀.
- For the telegraph, N(t) = N(t − 2) + N(t − 4) + N(t − 5) + N(t − 7) + N(t − 8) + N(t − 10). Then C = −log μ₀, where μ₀ is the positive root of 1 = μ² + μ⁴ + μ⁵ + μ⁷ + μ⁸ + μ¹⁰, giving C = 0.539.
- **Constraints by states.** A channel can have states a₁, …, a_m, each allowing a subset of symbols and fixing the next state. The telegraph has two states: last symbol a space or not (Fig 12.2).
- **Theorem 1.** Let b_ij^(s) be the duration of the s-th symbol allowable in state i and leading to state j. Then C = log W, where W is the largest real root of the determinant equation |Σ_s W^{−b_ij^(s)} − δ_ij| = 0. For the telegraph this is

  | −1,  W⁻¹ + W⁻⁴ ;  W⁻³ + W⁻⁶,  W⁻² + W⁻⁴ − 1 | = 0

  (a 2 × 2 determinant, rows separated by the semicolon).

**The discrete source.** Statistical knowledge of the source lets a proper encoding reduce the capacity needed. In English, E is commoner than Q, and TH than XP. Morse gives E a dot and Q, X, Z long sequences; commercial codes use 4–5-letter groups; standard greeting telegrams encode a sentence in a few numbers.

A source picks symbols with probabilities that depend on earlier choices: a **stochastic process**. Any stochastic process producing a discrete sequence from a finite set counts as a **discrete source**: natural languages, quantized continuous sources, abstract processes. Examples:
- (A) Five letters A–E, each with probability .2, chosen independently.
- (B) The same with probabilities .4, .1, .2, .2, .1.
- (C) Each letter depends on the one before, with **transition probabilities** p_i(j) and **digram probabilities** p(i, j). They are related by:
  - p(i) = Σ_j p(i, j) = Σ_j p(j, i) = Σ_j p(j)·p_j(i);
  - p(i, j) = p(i)·p_i(j);
  - Σ_j p_i(j) = Σ_i p(i) = Σ_{i,j} p(i, j) = 1.

  Shannon's three-letter example:

  | | p_i(A) | p_i(B) | p_i(C) | p(i) |
  |---|---|---|---|---|
  | A | 0 | 4/5 | 1/5 | 9/27 |
  | B | 1/2 | 1/2 | 0 | 16/27 |
  | C | 1/2 | 2/5 | 1/10 | 2/27 |

  The digram probabilities are A: 0, 4/15, 1/15; B: 8/27, 8/27, 0; C: 1/27, 4/135, 1/135. The idea extends to trigrams, p(i, j, k) or p_ij(k), and to n-grams.
- (D) Word-level: sixteen "words", each chosen independently and followed by a space. With probabilities: A .10, BEBE .16, CABED .11, DEB .04, ADEB .04, BED .04, CEED .05, DEED .15, ADEE .05, BEED .02, DAB .08, EAB .01, BADD .01, CA .05, DAD .04, EE .05.

**The series of approximations to English** (27 symbols, including space):
1. Zero-order, all letters equally likely: XFOML RXKHRJFFJUJ ….
2. First-order, independent letters at English frequencies (E .12, W .02): OCRO HLI RGWR ….
3. Second-order, digram structure: ON IE ANTSOUTINYS ….
4. Third-order, trigram structure: IN NO IST LAT WHEY CRATICT ….
5. First-order word approximation: REPRESENTING AND SPEEDILY IS AN GOOD ….
6. Second-order word approximation: THE HEAD AND IN FRONTAL ATTACK ON AN ENGLISH WRITER ….

The resemblance to English grows at each step. A sample has reasonably good structure out to about twice the range used in building it; the ten words "attack on an English writer that the character of this" are not unreasonable. Hence "a sufficiently complex stochastic process will give a satisfactory representation of a discrete source."

Method: the first two use random numbers and frequency tables (Pratt for letters, Dewey for words). From the third on, Shannon samples the text itself. Open a book at random and pick a letter; open another page and read until that letter appears; record the letter after it; repeat.

**Markoff processes.** A **Markoff process** has finite states S₁, …, S_n and transition probabilities p_i(j), and emits a letter at each transition. The states are the "residue of influence" from earlier letters. Its graphs:
- Fig 12.3, example (B): one state with five loops, A .4, B .1, C .2, D .2, E .1.
- Fig 12.4, example (C): states A, B, C. From A go to B .8 or C .2; from B to A .5 or B .5; from C to A .5, B .4 or C .1.
- A trigram source needs at most n² states.
- Fig 12.5, example (D): paths spelling the words, with a space returning to the start.

**Choice, uncertainty and entropy.** For events with probabilities p₁, …, p_n, Shannon asks for a measure H(p₁, …, p_n) that meets three conditions:
1. H is continuous in the p_i.
2. If all p_i = 1/n, H increases monotonically with n.
3. If a choice is broken into two successive choices, the original H is the weighted sum of the parts: H(1/2, 1/3, 1/6) = H(1/2, 1/2) + (1/2)H(2/3, 1/3) (Fig 12.6).

**Theorem 2.** The only H satisfying these is

  H = −K Σ p_i log p_i,

with K a positive constant. Shannon says the theorem is "in no way necessary for the present theory"; it is there chiefly to lend plausibility, and the "real justification" lies in its implications. H is the **entropy**, as in Boltzmann's H theorem. H(x) for a chance variable x uses x as a label, not an argument. With two possibilities, H = −(p log p + q log q), which peaks at 1 bit when p = .5 (Fig 12.7).

**Properties of H.**
1. H = 0 if and only if all the p_i but one are zero, that is, when the outcome is certain. Otherwise H is positive.
2. For given n, H is greatest, log n, when all the p_i are equal.
3. For a joint event, H(x, y) = −Σ p(i, j) log p(i, j), and H(x, y) ≤ H(x) + H(y), with equality if and only if x and y are independent.
4. Any change toward equalizing the probabilities increases H. An averaging p′_i = Σ_j a_ij·p_j, with doubly stochastic a_ij ≥ 0, increases H unless it is a permutation.
5. **Conditional entropy** H_x(y) = −Σ p(i, j) log p_i(j) is how uncertain y is, on average, once x is known. H(x, y) = H(x) + H_x(y).
6. H(y) ≥ H_x(y): "The uncertainty of y is never increased by knowledge of x." It decreases unless x and y are independent.

**Entropy of a source.** If state i has entropy H_i and occurs with probability P_i, the entropy per symbol is

  H = Σ_i P_i·H_i = −Σ_{i,j} P_i·p_i(j) log p_i(j).

Per second it is H′ = Σ_i f_i·H_i = mH, for m symbols per second; base 2 gives bits. For independent symbols, a long message of N symbols contains about p_i·N of each, so its probability is p ≐ p₁^{p₁N} ⋯ p_n^{p_nN}. Then log p ≐ N Σ p_i log p_i = −NH, and H ≐ log(1/p)/N. "H is thus approximately the logarithm of the reciprocal probability of a typical long sequence divided by the number of symbols in the sequence." The same holds for any source.

**Led to.** Binary storage was already known; the EDVAC report (10) made "the ability to retain the value of one binary digit" the unit of memory. Shannon named it the bit and asked how to encode long messages in few bits when messages are not all possible or not equally likely. That founded the theory of data compression and its limits (Huffman codes, 1952) and the reconstruction of corrupted messages, taken up by Hamming (13). "Entropy", borrowed from statistical physics, measures the information content of a source. Lewis calls *Communication Theory of Secrecy Systems* (1949), drawn from Shannon's classified wartime work, his third masterpiece, after this paper and the switching thesis (8).

## 13. Hamming, *Error Detecting and Error Correcting Codes* (1950)

**Set out to.** Make large computations "do things right". A telephone central office has self-checking circuits, failures that customers catch, and parallel independent paths. A digital computer is instead "a single long path which passes through the same piece of equipment many, many times", so one failure is a complete failure. If it is detected, the machine stops; if not, it invalidates everything after it.

Detecting codes already existed: 2-out-of-5 codes in switching and the Bell relay computers, 3-out-of-5 in radio telegraphy, and the word count at the end of telegrams. The Bell Model 5 relay computers at Aberdeen had two or three relay failures a day among the 8900 relays of the two machines, about one failure per two to three million relay operations. Self-checking prevented undetected errors, but computations halted, often unattended through nights and weekends. The next step was to correct errors. Binary is assumed (relays, flip-flops, dots and dashes, perforated tape).

**Construct.**
- **Systematic codes.** Each code symbol has n binary digits: m information digits and k = n − m check digits.
- **Redundancy** R is the ratio of the digits used to the minimum needed, R = n/m. It lowers the effective channel capacity.
- Little is known of the economics, so the first applications will be under extreme conditions:
  - (a) unattended operation over long periods with minimal standby equipment;
  - (b) extremely large, tightly interrelated systems, where one failure disables the whole installation;
  - (c) signaling in noise that cannot be reduced, or is uneconomical to reduce, as with jamming.
- Part I builds minimum-redundancy codes for single error detection, single error correction, and single error correction with double error detection. Part II proves them best.

**Single error detection.** Use n − 1 information digits and set the n-th digit to make the total number of 1s even. Then R = n/(n − 1) = 1 + 1/(n − 1). Larger n lowers the redundancy but raises the chance of an error and of an undetected double error. With p ≪ 1 and n ≈ 1/p, the probability that a symbol is correct is about 1/e = 0.3679…, and of a double error 1/(2e) = 0.1839…. A **parity check** may be even or odd, and may cover only selected positions.

**Single error correction.** Set k check positions by even parity checks over selected positions. On receipt, apply the k checks in order, writing 0 when a check agrees and 1 when it fails, right to left. This **checking number** must give the position of any single error, with 0 meaning no error. The condition is

  2^k ≥ m + k + 1, equivalently 2^m ≤ 2^n/(n + 1).

**Fig 13.1**, the smallest k for each n:

| n | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| m | 0 | 0 | 1 | 1 | 2 | 3 | 4 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 11 |
| k | 1 | 2 | 2 | 3 | 3 | 3 | 3 | 4 | 4 | 4 | 4 | 4 | 4 | 4 | 4 | 5 |

Check j covers the positions whose binary representation has a 1 in the j-th digit from the right:
- check 1: 1, 3, 5, 7, 9, …;
- check 2: 2, 3, 6, 7, 10, 11, …;
- check 3: 4–7, 12–15, 20, …;
- check 4: 8–15, 24, ….

Put the check digits at positions 1, 2, 4, 8, …, the powers of two, so that each is set independently of the others (Fig 13.2).

**The seven-position code.** n = 7, m = 4, k = 3. The checks cover positions 1, 3, 5, 7; 2, 3, 6, 7; and 4, 5, 6, 7. The information sits in positions 3, 5, 6 and 7. There are 16 code symbols (Fig 13.3; the symbol for 12 is 0111100), leaving 2⁷ − 16 = 112 meaningless ones. The all-zero symbol may be dropped, since it could be confused with no message, leaving 15.

To decode, send 0111100 and suppose position 5 flips, so 0111000 arrives.
- Check 1 (positions 1, 3, 5, 7) fails, so write 1.
- Check 2 (positions 2, 3, 6, 7) passes, so write 0.
- Check 3 (positions 4, 5, 6, 7) fails, so write 1.
- The checking number is 101 = 5: flip position 5.

**Single error correction plus double error detection.** Add one position that makes the parity of all the previous positions even.
- No errors: every check is satisfied.
- One error: the last check fails, and the checking number gives the position (zero means the last position itself).
- Two errors: the last check is satisfied, but the checking number shows an error.

Fig 13.4 adds the eighth column to the seven-position code. For symbols 0–15 it reads 0 0 1 1, 1 1 0 0, 1 1 0 0, 0 0 1 1.

**The geometric model.** Code symbols are vertices of the unit n-dimensional cube. The **distance** D(x, y) is the number of coordinates in which x and y differ, the least number of edges between them. It is a metric: D(x, y) = 0 iff x = y; D(x, y) = D(y, x) > 0 if x ≠ y; and the triangle inequality holds. For example, 001, 010, 100 and 111 are mutually at distance 2. A **sphere** of radius r about x is all points at distance r from x.

**Fig 13.5**, what the minimum distance buys:

| Minimum distance | Meaning |
|---|---|
| 1 | uniqueness |
| 2 | single error detection |
| 3 | single error correction |
| 4 | single error correction plus double error detection |
| 5 | double error correction |

Conversely, each of these requires every distance to be at least that minimum. Finding codes is finding subsets of the cube that keep a minimum distance. Correction can be traded for detection: minimum distance 5 serves for double error correction, for single correction plus triple detection, or for quadruple detection.

Two codes are **equivalent** if one becomes the other by interchanging positions and complementing the values in a position. That is an equivalence relation, and amounts to the rotations and reflections of the cube.

**Optimality.**
- **Detection.** At most 2^{n−1} points can have minimum distance 2. Split the n-cube into two (n − 1)-cubes; one holds at least half the points. Recurse down to a square, which holds at most two points at distance ≥ 2, so A ≤ 2^{n−1}. Every optimal code is equivalent to the parity code. The proof assumes only that symbols have length n.
- **Correction.** A systematic code is redefined by three properties: the positions checked are independent of the information in the symbol; the checks are independent of each other; and the checks are parity checks. In matrix form, the i-th row has 1s at the positions of the i-th check, the matrix has rank k, the k check positions can be solved in terms of the other n − k, and the arithmetic has 1 + 1 = 0.

  Spheres of radius 1 about the codewords are disjoint, and each holds n + 1 points. So there are at most 2ⁿ/(n + 1) codewords, which is the bound above, and the code above has minimum redundancy. Hamming found no non-systematic code with more symbols for given n and distance.

  Optimal codes need not be equivalent: for n = 4, m = 1, k = 3 there are two non-equivalent optimal codes of two symbols each. {0000, 1110} and {0000, 1111} are a pair of that kind.
- **Correction plus double detection** is minimal too. A better code with minimum distance 4 in n dimensions would give, on dropping the last coordinate, one with distance ≥ 3 in n − 1 dimensions and the same number of symbols, a contradiction.

  In general, a minimum-redundancy code of N points in n − 1 dimensions with minimum distance 2k − 1 corresponds to one in n dimensions with distance 2k. Adding an overall even-parity coordinate gives the pairs at odd distance 2k − 1 opposite parities, raising their distance to 2k; dropping the coordinate reverses this.

**Led to.** Today bits are reliably correct even though the media are continuous and imperfect: π always reads 3.14159, and location 2468 never becomes 2478. "When data does become garbled, our computers tend to tell us so. It was not always so." Early parity codes made a fifth bit the mod 2 sum of four data bits.

Hamming had worked on the Manhattan Project with von Neumann and shared an office at Bell Labs with Shannon (12). The relay calculators would halt on an error found over a weekend. His insight was that if a computer can tell there is a mistake, it might tell where, and correct it. A four-bit datum needs three more bits. The EDVAC report (10) had already observed that some errors could be corrected automatically.

**Hamming distance**, the number of positions in which two bit vectors differ, turns coding into **sphere packing** in {0, 1}ⁿ: distance ≥ 2 detects single errors, and distance 3 corrects them, because a received vector lies within distance 1 of only one codeword. The field exploded. Modern computers "achieve macroscopic perfection today by including carefully designed redundancy at the microscopic level, invisible to users".
