# Teaching CT, and where CT is going

## The waves of K-12 computing education

Getting computing into K-12 schools was "a struggle of a whole different order" from getting it into universities: few teachers had computer experience, and school boards gave little political support. The waves:

1. **Algorithmizing and mathematical problem solving (1950s–1960s).** Perlis's *algorithmizing* meant the mental skills of reasoning about problems and developing computational solutions. He and Forsythe believed everyone in every field would benefit from computing's procedural ways. Forsythe, citing Perlis: "we don't really know it until we can code it for an automatic computer!" Minsky claimed computing would surpass mathematics in early education, and Knuth that teaching a computer forces precision and deeper understanding. The authors call this optimism about transfer to general problem solving "premature". Programming arrived in high schools with the mid-1960s DEC PDP-8, along with the Little Man Computer (1965), Logo (1967) and the Dynabook concept (1968). Pilots never scaled, for lack of money and political will.
2. **Papert's Mindstorms (1980).** Logo was part of an integrated pedagogical framework. Papert coined "computational thinking" for the procedural thinking he taught children. His *constructionism* holds that learners "construct knowledge": they acquire practices by being immersed in a world of practices, building knowledge by practicing it rather than being told. He advocated self-directed and project learning, meaningful representations, facilitation-based education, and technology in the classroom. The central idea, the shift from "learning to program" to "programming to learn", was hard to sell to teachers.
3. **Literacy (1980s–1990s), then fluency (1999 onward).** "Computer literacy" courses taught word processors, spreadsheets and sketchpads; motivated students and teachers found them boring. A 1999 National Research Council commission reframed literacy as *fluency with information technology*, with a popular textbook of that name, to make children smart users who know the limits and risks of algorithmic processes. Schools adopted computing for pragmatic reasons: simulations and teaching software, basic programming, the Internet, 21st-century skills, STEM jobs, broadened participation and creative expression. Python, drag-and-drop interfaces and automating tools made programming accessible. Still, in 2010 many schools had no computing course; "Gaining fluency was not powerful enough to be a driving force."
4. **CT revived (2006 onward).** Jeannette Wing proposed that CT, not literacy or fluency, is what everyone needs, and the term "resonated and inspired action where literacy and fluency had not." At NSF she mobilized $48 million to train teachers in CS principles, get organizations to define CT and grade-level curricula, start CS-principles introductory college courses, and build a new Advanced Placement curriculum and exam. CSTA, Britain's CAS (Computing at School), Code.org and Australia's ACARA issued K-12 frameworks; coding clubs, boot camps and the "Hour of Code" followed. CT went mainstream.

CS Unplugged (late 1990s, Tim Bell, Michael Fellows, Ian Whitten) teaches computing concepts and practices through games, magic tricks and activities. It influenced the ACM K-12 and Code.org recommendations.

## The transfer hypothesis

The *transfer hypothesis* is "a belief that CT is a metacognitive skill learned from programming; students who learn CT in one domain became better problem-solvers in other domains, too." It would predict that a good problem solver in computer science solves physics problems with the same expertise. It was paired with the hope that a few teachers could teach CT to everybody. Its enthusiasts claimed "the concept of procedure is the secret educators have so long been seeking" and that programming "sharpens the mind."

The verdict: developmental cognitive science found no evidence of transfer from programming to other subjects, and research with adults did not support transfer of cognitive skills between domains. Programming is itself a complex network of skills: mathematical abilities, conditional reasoning, analogical reasoning, procedural thinking, temporal reasoning and memory capacity. It was never clear which of these transfer. Researchers concluded there is not enough evidence to accept the hypothesis, so it cannot justify teaching computing in K-12. What follows is that schools need many more teachers who understand CT in different contexts. Teaching a literacy course is a baby step that does not qualify a teacher to teach CT.

## The sixteen points of contention

Newcomers unfamiliar with CT's history built K-12 frameworks from scratch. They imperfectly reinvented old ideas, omitted important ones, confused CT with using applications, and absorbed misconceptions about computing and algorithms. Many of the resulting disputes come from mixing beginner and professional CT, or different contexts of application. When a disagreement about CT arises, locate it among these:

1. Is CT limited to the mechanics of constructing algorithms, or does it include machines, computational science, software engineering and design?
2. Is CT mostly about programming, or also systems, networks and architectures, or about none of those?
3. Is "CT is the formulation of algorithms to solve problems" too narrow a view of its scope?
4. Are algorithms only those fitting the strict theory-of-computing definition, or can they be defined more loosely?
5. Do algorithms necessarily include an abstract machine in the background?
6. Are algorithms primarily directions for controlling machines, or primarily means of expressing procedures?
7. Does using computational tools teach CT?
8. Is carrying out daily step-by-step procedures a manifestation of CT?
9. Is CT learned from practicing programming, or from well-designed learning activities that use steps and rules?
10. Does CT learned in computing transfer to problem-solving in other fields?
11. Is CT domain dependent, or a meta-skill valid in all domains?
12. Are computational processes found in nature, or limited to algorithms and machines?
13. Does computer information processing differ from human information processing, and can "information processing agents" include molecules, DNA or quarks?
14. Should students be assessed by demonstrated skill at designing computations, or by knowledge of key concepts?
15. Should customers' satisfaction with the job software does count in assessing its success?
16. Must K-12 CT stick to strict definitions of computing, or may it take pragmatic and pedagogical liberties?

**The authors' stance.**
- CT is "an old, rich human practice that has been perfected in the modern age of the electronic computer."
- It is "a mental discipline for thinking about designing computations of all kinds, a skill at the advanced levels honed and improved through extensive practice and experience."
- It has many levels and styles, from basic skills to highly specialized ones, and there are many good ways to teach entry-level CT.
- Nearly all CT ultimately boils down to machine-realizability.
- CT is mostly domain dependent: computational thinking in biology differs from that in physics, chemistry or the humanities.
- The notion that CT is an innate ability exercised daily by using computational tools and following routine procedures is wishful.
- Defining algorithms as possibly ambiguous steps resolved by human computers misunderstands computing.

They want a broad, pluralistic approach to teaching CT "while remaining faithful to computing's well-honed disciplinary ways of thinking and practicing," and teachers who convey the richness and beauty of computation's many dimensions.

## Forces changing CT

CT is "an ongoing quest to capture computing's ways of thinking and practicing," in never-ending flux. Development suites, languages and cloud services push design work to ever higher levels of abstraction, making computing jobs more design-intensive. Traditional programming is losing its place as the primary interface to computation, as domain-specific and intelligent tools let users harness computers without programming.

**New computational models.** Moore's law cannot be sustained, given the physics of silicon and how chips are made. The candidates to succeed silicon von Neumann machines are quantum, neural network, reversible, DNA and memristor computers, and each defines a new computational model for designers.
- The D-wave quantum computer solves Ising Model equations, which describe how systems settle into minimum energy states. Programming it means encoding the problem as Ising equations and entering their coefficients. Execution is letting the machine settle into a minimum energy state (a few microseconds). Readout is reading the qubits and interpreting them as the answer. It has no instruction set and no "sequence of steps". Most computer scientists experience a "mind tilt" on first setting one up, while trained physicists have much less trouble.
- In DNA computing, a 1994 experiment encoded the possible paths on a map into DNA strands and chemically evolved the mixture until most strands represented the shortest tour. In 2016 a team used CRISPR to insert an image into a bacterium's DNA. Molecular biologists grasp this more easily than step-trained computer scientists.
- Both show CT has outgrown "problem solving with computational steps".

**Design.** Only a small portion of app development concerns algorithms; most of it is designing systems for the concerns of a community. Automating cognitive tasks displaces workers, but new technologies breed new problems that need new designs, and so new jobs for designers. "You do not have to be a computer scientist to be a computational designer." "Computational design captures the spirit of today's computing revolution better than computational thinking does." Past technology revolutions created more jobs than they displaced, and governments should fund training so displaced workers can learn design skills. Design is rejuvenating computing's engineering side. It brings concerns about reliability, fault tolerance, architecture and systems that theory-centered definitions sideline. It also brings human concerns: recognizing the social worlds embracing computing, adopting a design into a community's practice, recognizing ethical issues raised by technology's side effects, and letting human judgment and care influence what machines do.

**Machine learning.** A neural network is a circuit that takes a very large bit pattern (the 12 megapixels of a photograph) and produces an output (the faces in it). Its components are loosely like neurons, which "fire" when combined input signals exceed a threshold, and it "learns by being trained rather than being programmed." Modern networks have many layers and higher capacity and are less easily confused. Once trained, their layers, nodes and weights are fixed, and they typically have no loops. So they run in constant time and constant memory, and meet real-time deadlines far more reliably than traditional programs. They are called "self-programmed", though the weight-adjusting training algorithm can be viewed as an automatic programmer. For many problems, finding or creating training data is easier than writing a rule-based program. The cost is that the network cannot "explain" its output, which matters in medical diagnosis, and assessing its reliability and security is the larger challenge ahead. Networks can also train against each other: AlphaGo learned Go by playing another AlphaGo network and beat the world champion in 2017, a method with "the potential to be game changing." Chip makers such as IBM and Intel offer courses because their chips demand a new way of thinking.

**Human-computer teaming.** After Deep Blue beat Kasparov in 1997, Kasparov invented Advanced Chess, in which each player consults a computer before committing to a move. The teams played better than humans alone and better than computers alone. Whether teams always beat a very good machine is controversial: some recent Advanced Chess teams did poorly against computers, and teamed diagnosticians do not always match the best diagnostic computer. Teams can still compute what neither can alone. In Luis von Ahn's 2006 game, pairs of humans labeled images and matching keywords entered a searchable database; the "labeling function" had been thought non-computable. Teaming needs a different kind of CT from traditional programming.

**Technology jumping.** Moore's law, Gordon Moore's 1965 prediction that chips would double in capacity about every two years for the same price, held for over half a century, "a triumph of computational thinking." Kurzweil observed the same doubling in earlier technologies such as punched card and vacuum tube machines, making silicon the fifth such wave. Extrapolating, he prophesied a brain-sized computer by 2030, conscious and superintelligent: the *singularity*, named for the utter unpredictability of what follows. Technology jumping is standard industry practice. A technology's adoption follows an S-curve, growing exponentially until an inflection point and then slowing as the market saturates. Business leaders develop the next technology in their labs and jump to it when their business reaches the inflection point, riding the next exponential wave, because a competitor on a better curve can upend them. The singularity is a product of computing, yet "it cannot be addressed with computational thinking."

**The whole-world-is-a-computer hypothesis.** Some argue that information is the basis of all physics (Wolfram's 2002 book), or that we live in a simulation run by a more intelligent species (Bostrom, 2003). Physicists grant some merit to explaining particles and interactions as quantum probability waves, which are forms of information, but regard a digital-simulation world as far-fetched.

**The curriculum fights.** One recurring fight is the first language: an easy one with the least confusing syntax (Python), or the one employers use (Java, Javascript)? An *imperative* framework (programs as instructions to a machine) or a *functional* one (programs as compositions of functions)? The other is the science-mathematics ideal against the engineering-design ideal. The first teaches abstractions and leaves their application to the student. The second focuses on all the details a builder must get right for a program to be safe and reliable. The science-math view long had the upper hand; design is restoring the engineering view. "the science and engineering sides need each other."

**What the inheritance cannot do.** Computing's battle-hardened CT does not help with the world's pressing issues: conflicts between non-state groups and nations, trade wars, terrorism, fake news, polarization, contested resources and environmental damage. Access to troves of information shows "that knowledge does not confer wisdom." A curriculum packed with the 2013 body of knowledge cannot develop the design sensibilities, wisdom and caring graduates need. The authors' prescription is to open space for interdisciplinary, intergenerational conversations whose purpose is not to solve problems but to think together, "to edify", building mutual understanding, appreciation and respect. They bring in mathematicians, scientists, sociologists, philosophers, anthropologists, lawyers and engineers. Their big questions:
- What cannot be automated? What should be? How far can automation take us? Who decides?
- How can AI generate more jobs through automation than it displaces, and how can we help people whose jobs our designs displace?
- How do we cultivate good designers?
- How can we increase trust in neural networks' decisions on inputs outside their training sets?
- How will we discourage an automated surveillance society? What technological solutions exist for cybersecurity?
- How do we make the world work when computers are embedded in almost every networked device?
- How does digital technology affect global politics, nationalism, trade balance and climate change?
- Will blockchains and cryptocurrencies ease our problems with trust in central authorities, and are they too expensive to maintain?
- How do we protect computing-dependent societies from attacks on critical infrastructure such as the electric grid or the Internet?
- How do we prepare people to appreciate the difference between wisdom and an abundance of information?
- What are the social implications of brain-computer interfaces and neural implants?
- What economic avalanches can follow from many interdependent technologies dropping in cost exponentially?

The authors claim no answers. Their point is that the conversations need to happen.
