---
name: computational-thinking
description: "Denning and Tedre's \"Computational Thinking\" (MIT Press Essential Knowledge): CT as designing computations that get computers to do jobs and interpreting the world as information processes. Use when the user names the book or its authors, or its terms: CT for beginners vs CT for professionals, wishful thinking, the six dimensions, DRUSS, CT in the small vs in the large, the software quality ladder and delight, virtual worlds, the transfer hypothesis, information interpretation, grand challenges, wicked problems. Also use when defining, teaching or assessing CT or a computing curriculum; judging whether a job can be computed or automated (impossible, intractable, heuristics); designing large software systems (Saltzer-Schroeder principles, Lampson's hints, abstraction, virtual machines, No Silver Bullet); designing software for users' satisfaction; modeling and simulating systems or natural processes; or weighing claims about AI, neural networks, quantum computing or the limits of computing."
---

# Computational Thinking

Denning and Tedre lay out "the magnificent fullness of computational thinking" and correct the misunderstandings about what computing can and cannot do. Their thesis: CT is an old, rich human practice (over 4,500 years) that was perfected in the age of the electronic computer. It is "powerful, but not universal". It depends on machines. Advanced CT is mostly domain dependent. Its public face, the K-12 "set of concepts for programming", is only its elementary layer. Use this skill to frame a computing question the way the authors would: name the kind of CT involved, test the proposal against wishful thinking, and bring in the practices of the dimension it touches.

## The definition

"Computational thinking is the mental skills and practices for
- designing computations that get computers to do jobs for us, and
- explaining and interpreting the world as a complex of information processes."

The *design* aspect is computing's engineering tradition: people build methods and machines to help other people, immersed in the community being helped. The *explanation* aspect is its science tradition, the dispassionate external observer. Either can exist alone in principle; in practice they go hand in hand. CT "is not a set of concepts for programming": it is ways of thinking and practicing, sharpened through practice. The authors picture CT as Janus. One face looks back and explains the mechanics (machines, algorithms, languages, modules combined into systems). The other looks ahead to what can be designed, with sensibility for the context of the software's users. CT is also a thinking tool for the technology-infused social world. It shows how everyday digital tools work, grounds cyber ethics, and builds resilience against algorithms that steer behavior, tailored fake news, viral social media and mass analysis of people's movements.

- ***Computation***: "complex series of numerical calculations and symbol manipulations". Trillions of simple operations in the proper order forecast weather or design a wing.
- ***Computer***: "An entity, human or machine, that can perform calculations and symbol manipulations according to a set of precisely specified rules." From the 1600s to the 1930s a computer was a person; the first electronic ones were "automatic computers".
- ***Algorithm***: "Description of a method to compute a function, or more broadly, to solve a category of computational problems. All the steps are so precisely specified that a machine can perform them." The authors call a definition of algorithms as possibly ambiguous steps resolved by human computers "a misunderstanding of computing": "ultimately nearly all CT will boil down to machine-realizability."
- ***Job***: any task someone considers valuable. Doing a job is not the same as automating it. Well-defined routine jobs can be automated; ill-defined ones such as "meeting a concern" cannot, and design CT helps with those.
- ***Automation***: using machines to replace human controllers of physical processes, to perform knowledge-work processes, or to perform a task humans formerly did.

The popular definition, "formulating problems so that their solutions can be expressed as computational steps carried out by a machine", generalizes the von Neumann CPU stepping through stored instructions. It fails for quantum annealers, DNA computers and neural networks, which have no instruction sequence, so use the broader definition above.

## CT for beginners and CT for professionals

- ***CT for beginners***: what K-12 educators built, the insights and methods for easing newcomers into computing. Its public story is problem solving with algorithms and thinking at many levels of abstraction, with children programming and playing games that simulate algorithms.
- ***CT for professionals***: the advanced CT of designing hardware, networks, storage systems, operating systems and the cloud, building complex software that works reliably and safely, and conducting computational science. It "is deadly serious": an algorithm error in an aircraft's control network can cause a death spiral before the pilot can react.

Together they make "a rich tapestry of computational thought", and their synergy propelled the computer revolution. Like any skill, CT has levels: beginner, advanced beginner, competent, proficient, expert, master. Many debates about what CT "really" is mix skill levels in one argument: teachers want a small teachable set for beginners while others mean years of professional practice. Settle which level and which context a question concerns before answering it.

## The six dimensions

The development of CT opened six dimensions, "like different windows looking at CT". Each window shows CT from its own angle, and some aspects show through two windows in different lights.

- **Methods**: mathematicians and engineers devised methods of computing and reasoning that non-experts could use by following directions. See [machines-and-methods.md](machines-and-methods.md).
- **Machines**: inventors sought machines to automate computation for speed and fewer errors, which led to the electronic digital computer. See [machines-and-methods.md](machines-and-methods.md).
- **Computing education**: university educators formed computer science to study and codify computation and its ways of thinking and practicing. See [computer-science.md](computer-science.md) and [education-and-future.md](education-and-future.md).
- **Software engineering**: developers formed it to overcome rampant errors and unreliability in large software systems. See [software-engineering.md](software-engineering.md).
- **Design**: designers bring "sensibilities and responsiveness to concerns, interests, practices, and history in user communities". See [designing-for-humans.md](designing-for-humans.md).
- **Computational science**: scientists brought computing into science, supporting theory and experiment and offering new ways to interpret natural processes. See [computational-science.md](computational-science.md).

## Wishful thinking: the four checks

Run these on any proposal to put computers to a job, and on any claim about what CT or computing can deliver.

1. **The wish that computers can do any job we can conceive of.** Some jobs are *impossible*: Turing proved in 1936 that no algorithm can inspect another and tell whether it halts or loops forever. The same reasoning rules out deciding whether a program contains a virus. Others are *intractable*: enumerating all tours in the traveling salesman problem for 100 cities would take 10^130 years on the fastest supercomputer, against a universe about 10^10 years old. For such jobs, look for *heuristics*, fast algorithms for approximate answers. In 2004 a Waterloo team used optimization heuristics to find a shortest tour of all 24,978 cities in Sweden, and proved it shortest, where enumeration would take on the order of 10^100,000 years. Their run used 85 years of processing time spread over a cluster for several months.
2. **The wish that a programming course lets you solve problems in any field.** You must learn the other field too: search algorithms are of little use to a genomics project until you know genome biology and its data.
3. **The wish that computers are not essential to CT.** The machine shapes the solution. When memory is too small, divide the problem into subsets that fit. When one processor is too weak, use parallel processors and algorithms that split the work. When the machine is too slow, find the bottlenecked component and upgrade it or pick an algorithm that avoids it. The clock paces every step; clockless machines such as quantum computers and neural nets demand other ways of thinking.
4. **The wish that the computer is smart.** "Computers are incredibly dumb." They execute mindless steps very fast with no understanding of what the steps mean. They correct only the errors you anticipated and supplied corrective algorithms for. "You are the source of the intelligence; the computer amplifies your intelligence but has none of its own."

Approach CT with humility: it is a learned skill, and "Our brains do not naturally think computationally." Beyond these four, some problems lie outside computing altogether. *Wicked problems* in the interactions of social communities and technologies yield only to social consensus and social action (see [computational-science.md](computational-science.md)). The singularity is a product of computing that CT cannot address.

## Gauging what can be computed

- **Speed is the main enabler.** Machines are billions to trillions of times faster than humans, who manage about one calculation per second. In one second a computer performs a billion calculations and draws a complex image, which would take a human 100 years. "Computing machines do the humanly impossible." The revolution is about what computers do for people, not about people performing algorithms in their own lives.
- **Machines and humans process differently.** Machines process with no understanding of the data, whereas humans understand it and correct errors on the fly. A mistake in an algorithm becomes a costly disaster before any human can react.
- **Computational complexity** measures the intrinsic difficulty of a problem by the steps and memory it needs. Searching an unordered list of N items takes time proportional to N (*linear*). Sorting takes on the order of N^2 steps with some algorithms and N log N with the best (*quadratic*). Printing all subsets of N items takes 2^N (*exponential*). "Search is fast, enumeration is slow": the former is "easy", the latter "hard". At 10^9 instructions per second, searching 100 items takes 0.1 microseconds, while enumerating the subsets of 100 items takes about 10^14 years, 10,000 times the age of the universe.
- **"Not everything for which we have an algorithm is automatable in practice."** The boundary moves: new algorithms and faster machines make once-intractable tasks automatable.
- **Hard problems need good heuristics.** The knapsack heuristic is "rate each item with its value-weight ratio, and then pack in order of decreasing ratios until the knapsack is full": very good packings, fast, not necessarily the best. "We can automate them only if we find a good heuristic algorithm." Chess programs score moves by counting the points of pieces lost instead of enumerating future boards. "Good heuristics give solutions that are very good most of the time." A skilled computational thinker designs them from complexity theory, logic and optimization. Genetic algorithms are one general method for near-optimal answers to intractable optimization problems (see [computational-science.md](computational-science.md)).
- **Unsolvable problems get partial solutions.** Because no machine can decide halting or virus detection, "a large segment of CT is concerned with how to provide partial solutions to problems that cannot be solved by automatic computers."

## The eight lessons

1. **CT is an addition, not a replacement.** It is "often a welcome addition to other fields, but not a replacement for their ways of thinking and not a meta-skill for all fields."
2. **CT is an old, well studied, and diverse topic.** Curricula built from scratch without its long history carry conceptual errors and inflated expectations that become "CT folklore". Turn to the existing body of computing education research.
3. **The speed of computers is the main enabler of the computing revolution.**
4. **Advanced CT is domain dependent.** An expert programmer who knows nothing of quantum physics has little to offer a quantum computing team. A hospital information system needs deep understanding of the hospital's institutional, informational and workflow processes.
5. **CT has changed the tools, methods, and epistemology of science.** Each field grew its own strain of CT; none was imported from computer science.
6. **The public face of CT is that of elementary CT.** K-12 bills it as concepts and rules for programming; professionals see a design skill; natural scientists see an advanced method of scientific interpretation.
7. **Beginner and professional CT together comprise a rich tapestry of computational thought.**
8. **Change is an inseparable part of CT.** There has never been a consensus on what CT "really" is. Treat the lack of a fixed definition "as a sign of the vitality of the field rather than our own failure to understand an eternal truth."

## Reference files

- [machines-and-methods.md](machines-and-methods.md): the methods tradition, from Euclid to Turing (the quest to eliminate intuition, representation, the Aberdeen decomposition pattern, where errors arise), and the precepts machines gave CT (binary representation, the clock, control flow, loops, the address-contents distinction, subprograms, universal machines, isolation), plus the architectures beyond von Neumann. Read it when reasoning about how a computation is represented, decomposed or executed, or about the history behind a precept.
- [computer-science.md](computer-science.md): the four eras of academic CT, Knuth's and Dijkstra's accounts of algorithmic thinking, programming paradigms, strong vs weak AI and the computational universe. Read it when arguing what computer science studies or what distinguishes algorithmic thinking.
- [software-engineering.md](software-engineering.md): CT in the small vs in the large, Brooks's rules, the three science-engineering distinctions, DRUSS, the Saltzer-Schroeder principles table, Lampson's hints table, hierarchical aggregation, virtual machines, client-server, No Silver Bullet and the newer complexities. Read it when designing, reviewing or securing a large software system or diagnosing why a project fails.
- [designing-for-humans.md](designing-for-humans.md): design as shaping artifacts that address human concerns, Parnas's capabilities, why the requirements process breaks down, Winograd's designer's-eye view, virtual worlds, the ISO quality factors and the six-level quality ladder up to delight. Read it when judging software quality or user satisfaction, or designing for a user community.
- [computational-science.md](computational-science.md): the three roles of the scientist, the two aspects of CT in science and their questions, the two meanings of "computational model", five worked modeling methods (grid visualization, state space with flow balance, state-machine controller, mesh simulation, genetic algorithm), and the limits: fragility, explainability, wicked problems. Read it when modeling or simulating any system (a natural process, a queue or capacity question, a controller, an optimization search), when interpreting a phenomenon as an information process, or when collaborating across science and computing.
- [education-and-future.md](education-and-future.md): the waves of K-12 computing education, the transfer hypothesis and its verdict, the sixteen points of contention with the authors' stance, and the forces changing CT (new computational models, design, machine learning, human-computer teaming, technology jumping, the curriculum fights, the big questions). Read it when designing or critiquing CT teaching, or forecasting where computing and CT are going.
