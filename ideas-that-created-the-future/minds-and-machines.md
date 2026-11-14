# Minds and machines

Papers 9, 14, 18, 19 and 27: neurons as logic, the imitation game, the perceptron, Wiener's warning about machines that learn, and ELIZA.

## 9. McCulloch and Pitts, *A Logical Calculus of the Ideas Immanent in Nervous Activity* (1943)

**Set out to.** Show that, because of the "all-or-none" character of nervous activity, neural events and the relations among them can be treated by propositional logic. Every net can be described this way, with more complicated logical means needed for nets containing circles. Conversely, for any logical expression meeting certain conditions there is a net that behaves as it describes.

**Facts from neurophysiology.**
- A neuron is a soma with an axon, and synapses join axons to somas.
- Conduction runs from under 1 m/s in thin axons to over 150 m/s in thick ones.
- A single synapse never fires a neuron. The latent addition period is under 0.25 ms, and the synaptic delay over 0.5 ms.
- Some inhibitions act in under 1 ms, so there are inhibitory synapses.
- Facilitation, extinction and learning can be replaced by equivalent fictitious nets with fixed connections and thresholds. The authors are explicit that "neither of us conceives the formal equivalence to be a factual explanation. Per contra!"
- A neuron's response is "factually equivalent to a proposition which proposed its adequate stimulus".

**Physical assumptions.**
1. Activity is all-or-none.
2. A fixed number of synapses must be excited within the latent addition period to fire a neuron, independent of earlier activity and of position.
3. The only significant delay is synaptic delay.
4. Any active inhibitory synapse absolutely prevents excitation at that time.
5. The structure of the net does not change.

Nets are **equivalent in the extended sense** if they behave the same with different structure or timing, so convenient assumptions do no harm.

**Construct.**
- Neurons are c_i, and N_i(t) asserts that c_i fires at t. **Peripheral afferents** receive no synapses; they carry the sensory data. The notation is Carnap's Language II with *Principia*'s dots, in which dots act as parentheses and a single dot also means "and".
- The functor S shifts back one synaptic delay: S(P)(t) holds when P held at the predecessor time, and S²Pr = S(S(Pr)).
- A **solution** of a net 𝒩 is a class of sentences giving each non-afferent neuron's action as a predicate of afferent actions. A predicate is **realizable** in the narrow sense if a net produces it at the exact time, and in the extended sense if some Sⁿ(Pr) is realizable, that is, with a delay.
- The two central problems: calculate the behavior of any net, and find a net that behaves in a specified way when one exists.
- A **cyclic set** is a minimal set of neurons whose removal leaves no circles. Its size is the **order** of the net, an index of complexity.
- **Temporal propositional expressions (TPEs)**: p₁(z₁) is a TPE; if S₁ and S₂ are TPEs, so are S S₁, S₁ ∨ S₂, S₁ . S₂ and S₁ . ∼S₂; nothing else is.

**Theorem 1.** Every net of order 0 is solvable in TPEs. Neuron i fires iff, one delay earlier, none of its inhibitory inputs fired and some subclass of its excitatory inputs whose count exceeds θ_i did:

  N_i(z₁) ≡ S{ Π_{m=1}^{q} ∼N_{j_m}(z₁) · Σ_{α∈κ_i} Π_{s∈α} N_{i_s}(z₁) },

where κ_i is the class of subclasses of the excitatory synapses whose sum exceeds θ_i. Substituting back through a net with no circles reaches the afferents.

**Theorem 2.** Every TPE is realizable by a net of order zero, built from the elements of Fig 9.1a–d (precession, disjunction, conjunction, conjoined negation) just as TPEs are generated. For any description of a state other than the all-false one, there is a single neuron whose firing is necessary and sufficient for it. Indefinitely many topologically different nets realize any TPE.

**Fig 9.1, nets and their expressions.**
- (a) Delay: N₂(t) ≡ N₁(t − 1).
- (b) Or: N₃(t) ≡ N₁(t − 1) ∨ N₂(t − 1).
- (c) And: N₃(t) ≡ N₁(t − 1) . N₂(t − 1).
- (d) And-not: N₃(t) ≡ N₁(t − 1) . ∼N₂(t − 1).
- (e) The heat illusion, in which cold briefly applied feels hot: N₃(t) ≡ N₁(t − 1) ∨ (N₂(t − 3) . ∼N₂(t − 2)), and N₄(t) ≡ N₂(t − 2) . N₂(t − 1).
- (f) N₄(t) ≡ ∼N₁(t − 1) . N₂(t − 1) ∨ N₃(t − 1), and N₄(t) ≡ ∼N₁(t − 2) . N₂(t − 2) ∨ N₃(t − 2) ∨ N₁(t − 2) . N₂(t − 2) . N₃(t − 2).
- (g) N₃(t) ≡ N₂(t − 2) . ∼N₁(t − 3).
- (h) N₂(t) ≡ N₁(t − 1) . N₁(t − 2).
- (i) N₃(t) ≡ N₂(t − 1) ∨ N₁(t − 1) . (Ex) t − 1 . N₁(x) . N₂(x). There was a time x ≤ t − 1 when N₁ and N₂ fired together; a neuron feeding itself then keeps firing indefinitely.

**Learning.** Learning can mean new synapses, as when axonal terminations become synapses if the neuron fires while they are excited, or the loss of an inhibitory synapse. **Theorem 7:** alterable synapses can be replaced by circles (Fig 9.1i). A spontaneously active neuron can likewise be replaced by a circle started or stopped by afferents.

**Nets with circles.** Reverberating activity lets a net refer to past events of indefinite remoteness, which makes nets with circles much harder. A net with a tape, scanners and efferents computes only what a Turing machine computes, and every such number is computable by such a net. Nets with circles but no tape compute some numbers but not all. The authors offer this as a "psychological justification of the Turing definition of computability and its equivalents", Church's λ-definability and Kleene's primitive recursiveness.

**Consequences.**
- Causality is irreciprocal. The present state and the net determine the next state, but disjunctive relations keep the previous state from being determined.
- Because circles make the past indefinite, "knowledge of the world, including ourselves, is incomplete as to space and indefinite as to time"; ignorance is the counterpart of the abstraction that makes knowledge useful.
- Altering the net produces tinnitus, paraesthesias, hallucinations and delusions.
- The **psychon** is the activity of a single neuron. It is inherently propositional, so psychic events are intentional, or "semiotic", and the fundamental relations of psychology are those of two-valued logic.
- One cannot deduce the afferent from the central, the central from the efferent, or the past from the present; witnesses contradict each other.
- Systems that act to reduce the difference between afferents and net activity show purposive behavior: homeostasis, appetition, attention.
- "For prognosis, history is never necessary", and inference from behavior to net is not unique.
- With the net determined, "mind" no longer "goes more ghostly than a ghost".

**Led to.** Lewis calls it a "strange and wonderful paper, technically convoluted and hubristically prophetic", whose aim was to reduce the brain to logic and so explain thought, memory and mind. In modern terms the neurons are gates in threshold logic. The neuron is drawn as a triangle, with excitatory inputs on the slanted sides, the inhibitory input at the left point, and the output from the vertical right side. A global clock means the state at t + 1 depends on the inputs at t.

The technical accomplishment is that the predicates computable by neural nets are exactly those expressible in a certain very expressive logic. Feedback cycles explain memory, and "for prognosis, history is never necessary" makes the brain a deterministic finite-state machine. The paper confuses the successor functor S with a bold S for sentences.

Kleene (1951) found "the part of their paper which treats of arbitrary nerve nets obscure", simplified the model, and got finite automata and regular expressions. As a brain model it was poor: *What the Frog's Eye Tells the Frog's Brain* (Lettvin et al., 1959) showed that the eye does not send a bitmap, and that shattered Pitts's hope. Still the paper gave birth to finite automata theory and to neural computing: "Their audacity paid off—just not in the way they had hoped."

It is the only work the EDVAC report (10) cites. Rosenblatt (18) rejected its logical style. Pitts worked at MIT under Wiener (19).

## 14. Turing, *Computing Machinery and Intelligence* (1950)

**Set out to.** Replace "Can machines think?" with a question in unambiguous words. Defining the terms by common usage would make the answer a Gallup poll, which is absurd.

**Construct: the imitation game.** A man (A), a woman (B) and an interrogator (C) in a separate room. C knows them only as X and Y and must decide which is the woman. A tries to cause the wrong identification ("My hair is shingled…"); B tries to help, and her best strategy is the truth, though "I am the woman, don't listen to him!" avails nothing. Answers are typewritten. Then: "What will happen when a machine takes the part of A in this game?" Will the interrogator decide wrongly as often as with a man and a woman? This replaces the original question.

**Why this game.**
- It draws "a fairly sharp line between the physical and the intellectual capacities of a man". There is no point dressing a machine in artificial flesh, so the interrogator cannot see, touch or hear the players.
- Specimen exchange:
  - Asked for a sonnet on the Forth Bridge: "Count me out on this one. I never could write poetry."
  - Asked to add 34957 to 70764: after a pause of about 30 seconds, "105621". The true sum is 105721.
  - Asked, with K at K1 and no other pieces against K at K6 and R at R1, what to play: after 15 seconds, "R-R8 mate".
- Question and answer suit almost any field. The machine is not penalized for losing beauty contests, nor a man for losing a race to an airplane.
- Objection: the odds are weighted against the machine, since a man pretending to be a machine would be given away by slow, inaccurate arithmetic. And might machines do something that ought to be called thinking but is very different from what a man does? That is strong, but if a machine plays satisfactorily, it need not trouble us.

**Which machines.** Every engineering technique is allowed, including machines whose builders cannot describe how they work. Men born in the usual manner are excluded. That leaves digital computers. The question is not whether present computers would do well, "but whether there are imaginable computers which would do well."

**Digital computers.** A digital computer does whatever a human computer could. It follows fixed rules from a book, altered for each job, with unlimited paper. Babbage's Analytical Engine had all the essential ideas and was mechanical. The fact that both computers and the nervous system are electrical is a superstition: Babbage's machine was not electrical, and all digital computers are equivalent, so "this use of electricity cannot be of theoretical importance". "We should look rather for mathematical analogies of function."

**Discrete-state machines** "move by sudden jumps or clicks from one quite definite state to another". Strictly none exist, since everything is continuous, but many machines are profitably thought of this way, light switches for example. A digital computer can mimic any discrete-state machine, so "considerations of speed apart, it is unnecessary to design various new machines to do various computing processes"; "all digital computers are in a sense equivalent."

The question becomes: fix one digital computer C. Can C, given adequate storage, more speed and an appropriate program, be made to play A's part satisfactorily, with a man as B?

**Turing's belief.** "In about fifty years' time it will be possible to programme computers, with a storage capacity of about 10⁹, to make them play the imitation game so well that an average interrogator will not have more than 70 per cent chance of making the right identification after five minutes of questioning." The original question is "too meaningless to deserve discussion", but by the end of the century usage will let one speak of machines thinking without contradiction. Conjectures matter "since they suggest useful lines of research", provided they are marked as conjectures.

**The nine objections and the replies.**
1. **Theological.** Thinking is a function of the immortal soul, given only to men. Reply: this restricts omnipotence; God could give a soul to an elephant with an improved brain. In building machines we would be "instruments of His will providing mansions for the souls that He creates". Scripture was once cited against Copernicus.
2. **"Heads in the sand."** "The consequences of machines thinking would be too dreadful. Let us hope and believe that they cannot do so." Reply: not substantial enough to need refuting; consolation would be more appropriate, perhaps in the transmigration of souls.
3. **Mathematical.** Gödel, Church, Kleene, Rosser and Turing show that any particular machine will answer some questions wrongly or not at all. Reply: the limits on any given machine are proved, but those on the human intellect have "only been stated, without any sort of proof". We often answer wrongly too, and superiority holds only over one machine at a time: "there might be men cleverer than any given machine, but then again there might be other machines cleverer again". People holding this objection would mostly accept the game as a criterion.
4. **Consciousness.** Jefferson's Lister Oration (1949) held that a machine equals the brain only when it writes a sonnet "because of thoughts and emotions felt, and not by the chance fall of symbols". Reply: in its extreme form this is solipsism, and we keep "the polite convention that everyone thinks". A viva voce test shows real understanding rather than learning "parrot fashion". In the sonnet dialogue, "Shall I compare thee to a summer's day" would not scan as "a winter's day", and Mr. Pickwick reminds one of Christmas, but "by a winter's day one means a typical winter's day, rather than a special one like Christmas". The mysteries of consciousness need not be solved first.
5. **Various disabilities**: "you will never be able to make one to do X". X might be: be kind, resourceful, beautiful or friendly; have initiative or a sense of humor; tell right from wrong; make mistakes; fall in love; enjoy strawberries and cream; learn from experience; be the subject of its own thought; do something really new. Replies:
   - These rest on unconscious induction from the ugly, limited machines people have seen, much as English children conclude that everybody speaks English.
   - On mistakes: distinguish **errors of functioning**, mechanical or electrical faults that abstract machines cannot make by definition, from **errors of conclusion**, which a machine can make, typing "0 = 1" or drawing a wrong induction. A machine in the game would make deliberate mistakes.
   - On being the subject of its own thought: a machine can treat its own program as subject matter, as it treats an equation like x² − 40x − 11 = 0. It can help write its own programs and predict the effect of changes in its structure; these are "possibilities of the near future".
   - Diversity of behavior is a matter of storage capacity.
6. **Lady Lovelace's objection.** The engine "has no pretensions to originate anything" (3). Reply: the Analytical Engine was universal, so it could mimic a learning machine. The better variant is that a machine can "never take us by surprise", and "Machines take me by surprise with great frequency." The underlying fallacy is "the assumption that as soon as a fact is presented to a mind all consequences of that fact spring into the mind simultaneously with it."
7. **Continuity in the nervous system.** Reply: the interrogator cannot exploit the difference. Asked for π, a digital computer can choose among 3.12, 3.13, 3.14, 3.15 and 3.16 with probabilities 0.05, 0.15, 0.55, 0.19 and 0.06.
8. **Informality of behavior.** No set of rules covers every circumstance, so men cannot be machines. Reply: the "undistributed middle is glaring". Distinguish **rules of conduct**, precepts one can be conscious of and act on ("Stop if you see red lights"), from **laws of behavior**, the laws of nature applied to the body ("if you pinch him he will squeak"). We cannot be sure complete laws of behavior are absent. A small Manchester program that maps a sixteen-figure number to another within two seconds already defies anyone to predict its untried replies.
9. **Extrasensory perception.** Turing calls the statistical evidence, at least for telepathy, "overwhelming". A telepathic player might get 130 cards right out of 400 against the machine's 104 by chance. Remedy: a "telepathy-proof room".

**Learning machines.** Turing has no convincing positive arguments, only "recitations tending to produce belief".
- A mind may be **subcritical**, like a subcritical atomic pile: an idea injected yields less than one idea in reply. A small proportion of minds are **supercritical**, and a single idea yields a whole theory. "Can a machine be made to be supercritical?"
- The **skin of an onion**: strip away mechanical skins one at a time and either a real mind remains or the whole is mechanical.

The problem is mainly one of programming.
- Brain storage estimates run from 10¹⁰ to 10¹⁵ binary digits; Turing inclines to the lower figure. The game needs at most 10⁹, and the *Encyclopaedia Britannica* (11th edition) is 2 × 10⁹. 10⁷ is practicable now.
- Speed is adequate, since machine parts are about a thousand times faster than nerve cells.
- Turing writes about a thousand digits of program a day, so about sixty workers would need fifty years. A more expeditious method is needed.

**The child machine.** The adult mind comes from (a) its initial state at birth, (b) education and (c) other experience. "Instead of trying to produce a programme to simulate the adult mind, why not rather try to produce one which simulates the child's?" A child's brain is like a notebook from the stationer's, with little mechanism and many blank sheets.

The analogy with evolution:
- the structure of the child machine corresponds to hereditary material;
- changes to it correspond to mutation;
- the experimenter's judgment corresponds to natural selection.

The process is faster because the experimenter can trace the cause of a weakness instead of waiting on random mutation.

**How to teach it.**
- **Punishments and rewards**: events just before a punishment become less likely to recur, and rewards make repetition more likely. No feelings are presupposed. But the information they carry is at most their total number, so "unemotional" channels are needed. Teach the machine to obey orders in a symbolic language.
- Build in a system of logical inference, with propositions carrying a status: well-established fact, conjecture, proved theorem, statement by authority. **Imperatives** classed as well established are acted on ("Do your homework now" with "Everything that teacher says is true").
- The imperatives that regulate the order of applying rules "make the difference between a brilliant and a footling reasoner, not the difference between a sound and a fallacious one". Examples: "When Socrates is mentioned, use the syllogism in Barbara"; "If one method has been proved to be quicker than another, do not use the slower method".
- The rules that learning changes are "of a rather less pretentious kind, claiming only an ephemeral validity".
- The teacher can be largely ignorant of what goes on inside, yet still predict the pupil to some extent.
- "Intelligent behaviour presumably consists in a departure from the completely disciplined behaviour involved in computation, but a rather slight one."
- "Processes that are learnt do not produce a hundred per cent certainty of result; if they did they could not be unlearnt."
- **A random element.** To find a number between 50 and 200 equal to the square of the sum of its digits, a systematic search from 51 can waste a large block with no solutions, while random tries need no bookkeeping. Learning is a search with many solutions, so random may be better.
- **Where to start**: an abstract activity like chess, or the best sense organs money can buy and English taught as to a child. "Both approaches should be tried." "We can only see a short distance ahead, but we can see plenty there that needs to be done."

**Led to.** The paper made the "Turing test" popular. Lewis stresses that the imitation game is "not a test of whether machines can think (a question Turing describes as 'meaningless') but instead a scientifically tractable substitute question". ELIZA (27) challenged the test's appropriateness; Searle (1980) argued against it with more nuance, followed by Shieber (2004). The paper appeared in *Mind*, a philosophy journal, and is reprinted here in full except for the section on universality.

## 18. Rosenblatt, *The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain* (1958)

**Set out to.** Answer two of three fundamental questions: (1) how information about the physical world is sensed, (2) in what form it is stored, and (3) how stored information influences recognition and behavior. Only the first is appreciably understood, through sensory physiology; this article takes up the second and third.

**Two positions on storage.**
- **Coded representations**: a one-to-one mapping between stimulus and stored pattern, a "wiring diagram", with sensory patterns reconstructable from memory traces like a photographic negative.
- **The empiricist position**, from British empiricism: images are never recorded. The nervous system is an "intricate switching network", and retention is the formation of new connections between centers of activity (Hebb's "cell assembly"). Information is stored as a "preference for a particular response", in connections or associations rather than topographic representations. A response is any distinguishable state of the organism, possibly inside the central nervous system, an "idea".

For coded-memory theorists, recognition is matching stored patterns against incoming ones. Empiricists merge storage and recognition: new stimuli use the new pathways and automatically activate the response. Rosenblatt takes the empiricist, or **connectionist**, position. The perceptron is a hypothetical nervous system or machine that shows fundamental properties of intelligent systems in general.

**Against logical models.** Symbolic logic, digital computers and switching theory led to brain models as "logical contrivances for performing particular algorithms": McCulloch and Pitts (9), Kleene, Minsky. Ashby and von Neumann studied imperfect random networks that still perform reliably, a task for which symbolic logic and boolean algebra are less suited. Hence the model is formulated in probability theory, not symbolic logic.

Deterministic models fail biologically. They lack equipotentiality and neuroeconomy, demand excessive specificity of connections and synchronization, require unrealistic specificity of the stimuli that fire a cell, and use variables with no neurological correlates. "A difference in principle is clearly indicated." The theory of statistical separability offers a solution in principle.

**Assumptions** (from Hebb, Hayek, Uttley, Ashby):
1. The connections used in learning and recognition differ between organisms; at birth they are largely random, with minimal genetic constraints.
2. Plasticity: after neural activity, the probability that a stimulus on one set of cells causes a response in another changes.
3. Exposure to a large sample makes similar stimuli form pathways to the same responding cells and dissimilar ones to different cells.
4. Positive and negative reinforcement help or hinder connections that are forming.
5. **Similarity** is the tendency of similar stimuli to activate the same sets of cells. It is not an attribute of formal or geometric classes but of a physical organization evolving with its environment.

**Construct: the photo-perceptron (Fig 18.1).** Retina → (localized connections) → A_I projection area → (random connections) → A_II association area → (random connections) → responses R₁, …, R_n, with feedback from the R-units to A_II.
1. Stimuli fall on a retina of **sensory units** (S-points), which respond all or nothing.
2. Impulses go to **association cells** (A-units) in a projection area A_I, which may be omitted. The S-points feeding an A-unit are its **origin points**, excitatory or inhibitory. If their algebraic sum reaches the threshold θ, the A-unit fires. The origin points of an A_I unit cluster around a central point, falling off exponentially with retinal distance.
3. Connections from A_I to A_II are random; otherwise A_II units are like A_I units.
4. **Responses** R₁, R₂, …, R_n are cells that act like A-units, each with many origin points at random in A_II. The A-units transmitting to a response form its **source-set**.

Up to A_II all connections run forward; between A_II and the R-units they run both ways. The feedback rule is either (a) each response excites the cells of its own source-set, or (b) each response inhibits the complement of its own source-set. (a) is more plausible anatomically; (b) is easier to analyze and is assumed for most systems.

**Conclusions.**
1. In an environment of random stimuli, randomly connected units can learn to associate specific responses with specific stimuli, better than chance even with many stimuli per response.
2. In such an "ideal environment", the probability of a correct response falls toward chance as more stimuli are learned.
3. There is no basis for generalization there.
4. In a **differentiated environment**, where each response goes with a distinct class of mutually correlated, "similar" stimuli, retention approaches a better-than-chance asymptote. The asymptote can be brought arbitrarily close to 1 by adding association cells.
5. The probability of correct generalization to unseen members of a class approaches the same asymptote.
6. A contour-sensitive projection area and a binary response system help; each response, or "bit", becomes an independent feature of the stimulus.
7. Trial-and-error learning is possible with bivalent reinforcement.
8. Temporal patterns can be learned by extending statistical separability.
9. Memory is distributed. Removing part of the cells has no appreciable effect on any one discrimination, but causes a general deficit across all learned associations.
10. Simple cognitive sets, selective recall and spontaneous recognition of classes are possible. Recognizing relationships in space and time is a limit to cognitive abstraction.

**Six physical parameters.** For a given mode of organization, learning, discrimination and generalization "can be predicted entirely from six basic physical parameters":
- x, excitatory connections per A-unit;
- y, inhibitory connections per A-unit;
- θ, the expected threshold of an A-unit;
- ω, the proportion of R-units to which an A-unit is connected;
- N_A, the number of A-units;
- N_R, the number of R-units.

The number of sensory units matters only if very small. Each parameter is a "clearly defined physical variable, which is measurable in its own right".

**Claims for the theory.**
- **Parsimony**: only one hypothetical construct, V, the "value" of an association cell.
- **Verifiability**: earlier theories measure behavior to predict behavior. That is curve fitting, essentially irrefutable, and the choice of model becomes "a matter of personal aesthetic preference"; as Kistiakowsky put it, "given seven parameters, I could fit an elephant." Measuring the parameters independently means a fit cannot be forced.
- **Explanatory power and generality**: the theory is not specific to one organism, permits building behaving systems to order, and "loses none of its precision through generality."

**Led to.** Lewis calls the perceptron "at once a dramatic early step toward artificial intelligence, a temporary casualty of intellectual rivalry, and a case study in the faddishness of scientific research trends". The first perceptron (1957, on an IBM 704) trained a pattern recognizer by reinforcement; this paper refines it with tunable parameters and physics-style mathematics.

Minsky and Papert's *Perceptrons* (1969) proved the limits of a restricted "one-layer" version. They were correct, but the book sidetracked work on the full model at a moment of slow AI progress, as MIT's symbolic, logic-based approach won out over mimicking the brain's architecture. The ideas came out of mothballs in the 1980s, when computers could simulate multilayer nets and train them on sizable data sets. The line to today's neural networks is "anything but direct".

## 19. Wiener, *Some Moral and Technical Consequences of Automation* (1960)

**Set out to.** Take stock thirteen years after *Cybernetics* (1948). Wiener rejects entirely the view that machines cannot possess any originality, that "nothing can come out of the machine which has not been put into it". He sets against it Samuel Butler's prediction that machines might take control of mankind. Butler's machines involved only power; today's involve thinking and communication.

**Thesis.** "Machines can and do transcend some of the limitations of their designers, and that in doing so they may be both effective and dangerous." We may in principle come to understand any machine's elements, but not in less time than it takes to operate, nor within any given number of years. Machines are faster and more precise over a limited range, so they transcend us in performing tasks even without intelligence, and our understanding arrives after the task is done. Understanding should develop pari passu with performance; otherwise the car runs into the wall before we can stop it.

**Game-playing machines.** IBM's checkers machines do not work from a perfect closed theory. Von Neumann and Morgenstern's game theory is suggestive but does not describe them, and minimax over all best responses is both impossible and not the best policy against a limited opponent. Ticktacktoe has a complete theory; chess, checkers, war and business competition do not. The machines resemble expert but limited human players, whose strategic evaluations are "in essence not complete". Nelson and Napoleon won by appraising their opponents' particular limitations.

**Levels of play.** Tactics, strategy, the considerations that shape strategy, the length of the relevant past: each level demands study of a longer past. The levels correspond to Russell's logical types. An infinity of types brings paradoxes like the barber who shaves all and only those who do not shave themselves, so "the search for the best policy under all levels of sophistication is a futile one." These problems arise in "the programming of programming".

The lowest machine plays a rigid evaluation, with empirical numerical weights on pieces, command, mobility and so on, and chooses the play of greatest weight.

**Learning machines.** The next step is a machine that reviews its record of earlier games and reweights its factors to match won against lost games. Its game personality becomes less rigid, and old tricks stop working. Such a checkers machine showed marked superiority to its programmer after 10 to 20 hours of play and indoctrination. Such machines "most definitely escape from the completely effective control of the man who has made them".

Its weakness is the end game, where the same strategy at every stage leaves it clumsy at the coup de grâce. In chess the opening also needs its own waiting strategy, because the initial position has exceptionally low mobility. Wiener's friends predict master-level chess in 10 to 25 years.

**Push-button war.** Learning machines may come to program the pushing of the button. They cannot learn from real war, which would end humanity and whose techniques keep changing, so they learn from war games. If the game's rules for victory do not match what we want, the machine may pursue "a policy which would win a nominal victory on points at the cost of every interest we have at heart, even that of national survival."

**Man and slave.** The moral problem is close to slavery. Slavery is cruel, but it is also self-contradictory: we want the slave both intelligent and subservient, and "complete subservience and complete intelligence do not go together." The brain remains more efficient at higher logic, as "a self-organizing system which depends on its capacity to modify itself into a new machine rather than on ironclad accuracy and speed". But the level at which it wins keeps shifting upward.

Automation takes from the designer and operator any effective understanding of the machine's stages and real tactical intentions, so they cannot foresee consequences outside the frame of the game while it runs. "Human action is a feedback action." It is not enough that some action could change the machine's course; we may lack the information to know when. Ataxia, the loss of feedback about position, is as disabling as paralysis.

**Literal-minded agencies.**
- The sorcerer's apprentice, whose broom keeps carrying water.
- A bottle factory programmed for maximum productivity, bankrupted by an inventory of unsalable bottles six months after it should have stopped.
- The genie and the fisherman.
- W. W. Jacobs's "The Monkey's Paw", a talisman granting three people three wishes each. The first's third wish is for death, and the sergeant major's experiences are too terrible to relate. His friend wishes for £200; his son is killed in factory machinery, and the company sends £200 without admitting responsibility. He wishes the son back, and the ghost knocks. The third wish sends it away.

Two agencies "essentially foreign to each other", coupled for a common purpose with incomplete communication, give unsatisfactory results. Hence: "we had better be quite sure that the purpose put into the machine is the purpose which we really desire and not merely a colorful imitation of it."

**Time scales.** A man and a machine working on very different time scales do not gear together, whichever is faster. The same holds for slower processes like political history and the development of science, "a control and communication process for the long-term understanding and control of matter", in which "50 years are as a day in the life of the individual". Wiener's creed: incomplete knowledge is better than none, but nothing justifies assuming that the faster we rush to use new powers the better. "We must always exert the full strength of our imagination to examine where the full use of our new modalities may lead us."

**Led to.** Wiener was the father of **cybernetics**, "control and communication in the animal and the machine". Its crucial concept is **feedback**, and the name comes from the Greek for steering a boat. His tools were continuous and statistical rather than discrete; his wartime work was missile guidance. In the 1920s, working with Vannevar Bush on a differential-equation machine, he suggested vacuum tubes in place of mechanical linkages. Pitts (9) was his protégé.

In 1946 he refused a paper to a military contractor, holding that "to provide scientific information is not a necessarily innocent act", and he never again accepted government money. His influence faded as defense funding nourished the postwar boom. *The Human Use of Human Beings* (1950) argued against "the American worship of know-how as opposed to know-what". The field diffused, but "cyber" persists as a prefix.

## 27. Weizenbaum, *ELIZA—A Computer Program for the Study of Natural Language Communication between Man and Machine* (1966)

**Set out to.** Present a program, running on MIT's MAC time-sharing system, that makes natural-language conversation with a computer possible. Then unmask it. "It is said that to explain is to explain away." Once a program is explained, "its magic crumbles away; it stands revealed as a mere collection of procedures, each quite comprehensible", and the observer moves it from the shelf marked "intelligent" to the curios. "Few programs ever needed it more."

**Construct.** ELIZA is written in MAD-SLIP for the IBM 7094. Like Shaw's Eliza, it can be made to appear more civilized by a "teacher", "the relation of appearance to reality, however, remaining in the domain of the playwright". Input is analyzed by **decomposition rules** triggered by **keywords**, and responses are generated by **reassembly rules** attached to selected decomposition rules.

**Procedure.**
1. Scan the input for a keyword.
2. If one is found, transform the sentence by the rule attached to it. If none is found, give a content-free remark or, under certain conditions, an earlier transformation.
3. Keywords carry a **RANK**: drop the current keyword when the scan finds one of higher rank.
4. A comma or period is a delimiter. If a keyword has already been found, delete the text after it; if not, delete the phrase before it. So only single phrases or sentences are ever transformed.

The keywords and transformation rules make up the **script** for a class of conversation. "A script is data; i.e., it is not part of the program itself", so scripts exist in Welsh and German as well as English. A transformation rule is a pair of SLIP functions: one decomposes a string by criteria, testing whether it satisfies them, and one reassembles it by an assembly specification.

**The five technical problems.**
1. Identify the most important keyword.
2. Discover a minimal context. For example, "you" followed by "are" is an assertion.
3. Choose the appropriate transformation and carry it out.
4. Respond intelligently when there is no keyword.
5. Provide editing, especially extension, of scripts, with economy of time and storage.

**The typical conversation** (the machine in capitals). "Men are all alike." IN WHAT WAY. "They're always bugging us about something or other." CAN YOU THINK OF A SPECIFIC EXAMPLE. "Well, my boyfriend made me come here." YOUR BOYFRIEND MADE YOU COME HERE. … "I am unhappy." DO YOU THINK COMING HERE WILL HELP YOU NOT TO BE UNHAPPY. … It ends: "Bullies." DOES THAT HAVE ANYTHING TO DO WITH THE FACT THAT YOUR BOYFRIEND MADE YOU COME HERE.

The **MEMORY** machinery keeps a few earlier inputs; Lewis notes it is revived when the dialog peters out. Users type with ordinary punctuation, except that the question mark is MAC's line-delete character.

**Why the doctor script works.** The script makes ELIZA respond roughly as a Rogerian psychotherapist would. A psychiatric interview is one of the few "categorized dyadic natural language communication" situations in which one party may pose as knowing almost nothing of the real world. Answering "I went for a long boat ride" with "Tell me about boats" is taken as purposeful, not ignorant. The speaker keeps the sense of being heard and understood, and supplies the background knowledge, insight and reasoning in the interpretations. That removes the need to store real-world information.

The speaker will not defend the illusion against all odds, but makes generous assumptions and rationalizes hard responses until the image crumbles. With a machine, credibility stands in for plausibility. "Some subjects have been very hard to convince that ELIZA (with its present script) is not human. This is a striking form of Turing's test." Important decisions are made in response to computer output. "ELIZA shows, if nothing else, how easy it is to create and maintain the illusion of understanding, hence perhaps, of judgment deserving of credibility. A certain danger lurks there."

**Understanding.**
- A script holds some world information. "Everybody hates me" draws "Can you think of anyone in particular", a specific hypothesis.
- Writing a script is a programming act that "clearly shows where the programmer's understanding and command of his subject leaves off".
- "The crucial test of understanding, as every teacher should know, is not the subject's ability to continue a conversation, but to draw valid conclusions from what he is being told." That would require storing selected inputs, and the problem lies in "selected".
- The next goal is to switch from concealing misunderstanding to revealing it. An augmented ELIZA would show what it knows and where its knowledge ends, and add to it by talking with many people.
- A model of the subject would follow: if someone says they are not married and later speaks of a wife, infer that they are widowed or divorced, or confused. A **belief structure** (Abelson's phrase) would let it detect rationalizations and contradictions, and conversations would turn into arguments.

**What ELIZA is.** "Seen in the coldest possible light, ELIZA is a translating processor in Gorn's sense." It operates only syntactically, producing expressions of another language to which we attribute meanings, the "semantic intents" of the source. The target can be English, or the algebra-word-problem English that Bobrow's STUDENT translates into equations.

**Led to.** Lewis calls ELIZA the first example of a chatbot: a program that "knows" very little but creates the illusion of conversation by manipulating its partner's own discourse. Weizenbaum was surprised how intensely people engaged; his staff assistant asked him to leave the room while she used it. The sensation owed something to time-sharing (23), which was new in 1966 and which he explains to his readers.

The name comes from Eliza Doolittle in Shaw's *Pygmalion*, "reprogrammed" by Professor Higgins. The Greek myth of Pygmalion's statue brought to life, the animation of the inanimate, is closer to ELIZA. Troubled by how easily people were fooled, Weizenbaum became a lifelong critic of AI. In *Computer Power and Human Reason* (1976) he tried to separate humans and machines once and for all. The debate continues over where computers should, as opposed to can, replace human interaction. ELIZA challenged the appropriateness of Turing's test (14).
