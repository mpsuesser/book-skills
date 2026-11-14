# Building complex systems

The engineering practice of the ARPA community, from Whirlwind and SAGE through CTSS, Multics, the Arpanet IMPs and the PARC Alto. Apply it when the user is planning how to build something large and new.

## Start from the user's scenario

Lick's design method in the Intergalactic memo: "It seems easiest to approach this matter from the individual user's point of view—to see what he would like to have, what he might like to do, and then to try to figure out how to make a system within which his requirements can be met."

Write the scenario concretely and in the first person. Lick's example fits curves to his own experimental data. He interrogates "first the local facility, and then other centers" for a grid-plotting program, borrows one written in another language, finds that no suitable curve-fitting function exists, writes a master program, and files the result under a name. He wants a deviation from the naming convention "called to my attention".

Then list the features the scenario exercised: retrieval by descriptors, linking borrowed programs, borrowing data, deciding where computation runs, and filing for others. Lick called it "a kind of example of example". The procedure is to "collect ... a considerable number of such examples, and to see what kind of software and hardware facilities they imply." Prefer designs that hide decisions the user should not have to make: "it seems better for the computer, or the network, somehow, to do that."

## Bootstrap

Project MAC's proposal: "[This information utility] will be by necessity a sort of bootstrap operation ... The evolving system will be, simultaneously, the main research tool and the primary object of experimentation, as well as the tangible product of the development effort." Its cycle was: run a working system, get people hooked on it, learn from how a large and diverse community uses it, and build the improved system on the next machine. Fano: "You couldn't develop and improve the system without seeing how a large and diverse community used it in practice."

## Prototype to give people a feel

The fastest way to win support is a working system. Herbert Teager wanted the ultimate time-sharing system and was "willing to wait". Corbató built a crude, compatible one that ran existing software now: "You could talk about it on a blackboard until you were blue in the face", and still get "'Oh, yes, but why do you need that?'" A prototype ended that argument. Compatibility counts: CTSS ran on the new machine within a week. Lick's own standard was to "buy into things and finish them and make them demonstrable."

## Live in the future

Taylor's rule at PARC: "Don't just *invent* the future; go *live* in it." Get five to ten years ahead and ignore today's cost, since Moore's law will bring it down. "Whatever you build, *use* it. In fact, get everybody in PARC to use it ... so they can see for themselves what the problems and the possibilities are. And then use what they learn to build better technology."

The forecasting method is a back-of-envelope run along the cost curves. Taylor and Kay each projected when a room-sized interactive machine would fit on a desk, then in a lap, then in a hand. Taylor's question was "how long before time-sharing was totally obsolete?" Pake's physicist version: "the first investigators to invest in the next level of instrumentation are usually the first to make the next level of discoveries." Taylor's caution about where to aim: the hardware is predictable, but "you couldn't predict with any accuracy what you could *do* with it." The significance lies in "how the technology was woven into the fabric of human life."

## Scope: prune, and walk before you run

- **Too many ideas.** Multics was "top-heavy with too many ideas, and we failed to recognize that they would not always go together." Its repair was "pruning things down to the bare essentials and trying to find a more elegant way of doing things." There were more causes: too many cooks with no one in charge, "minor" modifications that added up to a new machine, and dependence on an outside compiler. "Everyone thought it was easier to build systems than it turned out to be." Fredkin's epitaph: "excellent ideas in Multics, trapped in this overgrown, baroque monster." Unix kept "the features that seemed truly useful" and left out "the more baroque elaborations": "sweet, quick, and clean." Lick warned that overcomplex systems invite "general retrenchment to noninteractive applications". The book asks whether "perfect" was the enemy of "good."
- **Complexity is the barrier.** "The sonic barrier in the development of such systems is complexity." Large interactive systems "must be developed interactively. The systems being built must remain flexible and open-ended throughout the process of development, which is evolutionary". They "cannot be developed in small ways on small machines."
- **Walk before you run.** The Arpanet's request for quotation called for four nodes with an option to expand.
- **A system is never finished.** IBM's static view of systems is diagnosed in lab-to-market.md. Prefer architectures that grow by addition. The MIT team's version: a memory-centered design where you just add processors, for both reliability and expansion.

## Architecture: simplify by moving the boundary

- **Make the subsystem self-contained.** Wes Clark solved the network by putting routing in small dedicated machines rather than the hosts. See open-systems.md.
- **Let one general component do the work.** The Alto's second "aha" was simple device controllers, with the CPU doing input and output in software, an "enormous simplification". Its first "aha" was that memory was cheap enough "to devote a bit to every pixel."
- **Disintegrate rather than integrate** when independent parties must evolve separately (Kahn's gateways).
- **Watch the coordination cost.** Bill English's team split the POLOS system by task across a web of small machines, and the coordination overhead ate the resources.
- **Package data with its procedures.** Kay's air force trick sent data records together with the procedures for reading them, so "the data file would now behave like an intelligent assistant: it would 'know' how to do its job." From Simula he went on to object-oriented programming: "Why not divide it up into little computers ... thousands of them, each simulating a useful structure?"

## Programming: exploratory vs top-down

**Top-down programming** works when the problem is known. Lick accepted it as a "commonsense method of delegating responsibility", but "before you can delegate responsibilities ... you have to figure out precisely what those responsibilities are and how you should carve them up." On the frontier, "man must often chart his course by stars he has never seen. Rarely does one recognize or discover a complex problem, formulate it, and lay out a procedure that will solve it—all in one great flash of insight." When systems are truly complex, "programming has to be a process of exploration and discovery". The tools for it, like Lisp and Sketchpad, make ideas easy to formulate and reformulate on the fly.

Lisp was built bottom-up from small functions, with an interpreter that holds a question-and-answer dialogue. Lick's **software Tinkertoy** was a library of modules users assembled into models and extended, until "the library would eventually become the repository of the work of the community."

On errors in large programs: "The presence of such errors in a program is not evidence of poor workmanship ... no complex program can ever be run through all its possible states or conditions."

## "When this goes wrong"

Corbató "never said, '*If* this goes wrong ...'; he always said, '*When* this goes wrong.'" The discipline is to "give up every engineer's first instinct, which was to control things so that problems could not happen, and instead design a system that was guaranteed to fail—but that would keep running anyhow." Its mechanisms in CTSS were **firewalls** (each user's memory isolated), a **clock** (the supervisor grabs control back), and **backup** (a daemon saving files within half an hour). When Whirlwind's unreliability was admitted, the response was duplex redundancy.

## Test by measurement and by trying to break it

- **Measure from day one.** Kleinrock: "If this network is going to be an experiment, we must make measurements!" UCLA became the Network Measurement Center.
- **Try to crash it.** Kahn predicted failure modes and asked for test software: "I would program it overnight, and we would just blast the thing—and the network would break. Then Bob would be happy."
- **Test against reality early.** Whirlwind's Cape Cod System used actual radars as its test bed. The IMP team tested its code on a simulator before the hardware arrived. They also pushed the supposedly mature Honeywell machine hard with real-time traffic, which exposed a synchronizer flaw that crashed it only every three or four days.

## Team

- **Small and first-rate.** Frank Heart on the IMP: "only a very small group could do the project on that time scale ... a much larger group that had to start interacting with memos and formal documents ... would not have been feasible." There was no weekly progress meeting; they "probably did it hourly." BBN won the contract over Raytheon's top-heavy hierarchy with about a dozen people and no hierarchy.
- **Technical control through understanding.** Heart "wouldn't let go of anything until he completely understood every little piece of it ... by the time he understood it, everybody else understood it, too."
- **Invention by doing.** "There wasn't much theory ... So we just got out there and did it". They treated it as an "engineering problem as opposed to a theory problem."
- **Psychologists with engineers from the start.** At Lincoln, Lick insisted that human-factors people join the design from the beginning, not at the end.
- **Meet as individuals.** The first IBM and Lincoln meetings were "loud and rancorous ... social rather than technical ... a process of getting acquainted". After that, arguments were between individuals, not organizations.

## Name the prototype

Taylor: "Good names for prototypes are very important ... familiar, easy to pronounce, easy to spell, have a broad theme, and conjure up pleasant feelings." His name for PARC's personal computer was the Alto.
