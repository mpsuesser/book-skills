# Software engineering: CT in the large

The dimension formed to overcome rampant errors and unreliability in large software. Epigraph (Fritz Bauer, 1971): "Software engineering is the part of computer science that is too difficult for the computer scientist."

## In the small and in the large

- ***CT in the small***: designing and writing single programs. These are the practices and thinking tools of a single programmer.
- ***CT in the large***: designing software systems and managing the projects that carry them from design into production and maintenance. These are the practices of teams building large production systems with long life spans and large user bases.

The two are qualitatively different: "something was qualitatively different about a program written by a single programmer and a system that required a team of 300 programmers." The skills for a thousand lines differ from those for a million, mainly because large systems must be built by teams.

**The Mariner I lesson (1962).** One missed punctuation detail made the ground computer steer on raw velocity data instead of data smoothed over a time window. The rocket overcompensated for minor perturbations and was destroyed 293 seconds after liftoff ("For Want of Hyphen Venus Rocket Is Lost"). A single-bit error can crash a system; losing a sliver of material only degrades a bridge.

**The software crisis.** Production-quality software must meet the ***DRUSS objectives***: dependable, reliable, usable, safe and secure. In the 1950s the machine was the product, and programs were written for personal or workgroup use. Tools for programming in the small did not scale. Projects ran late, over budget, too buggy to use, or were never delivered, and maintenance was costly or infeasible. Developers unfamiliar with the target domain left large gaps between customer needs and system functions. Companies responded by hiring highly skilled programmers and by the "non-warranty", licensing software only once users waived damages. The non-warranty fed public disillusionment. The NATO conferences of 1968 and 1969 turned to engineering. Traditional engineers brought fault-tolerant design, systems thinking and project management; theorists brought formal verification, structured programming and algorithms analysis. Neither dented the problem. Systems engineering missed that one bit can crash software. Proof was too hard for large systems, said nothing about usability, and ignored hardware failures and noise. Randell: the problem is "multi-person development of multi-version programs."

**Brooks's rules** (*The Mythical Man-Month*, 1975, from managing the 300 programmers who built the IBM 360 operating system, which grew to 10 million lines):
- A program becomes a production system along two dimensions: generalizing one program into a system of interacting programs, and adding the structures and components that guarantee reliability. Each tripled the effort; both together are nine times the effort of a single program.
- Time and people do not trade off equally: 12 programmers cannot do in a month what took one programmer 12 months.
- The structure of the software winds up resembling the organization that built it.
- Managing the team is a greater challenge than the technical problems the team solves.
- Productizing a program so non-programmers can use it safely and reliably is far harder than writing it.

**Practices CT in the large added**: decomposition, complexity, information structures, causality, closing semantic gaps, data abstraction, data structures, encapsulation, information hiding, recursion, project management and software life cycles.

## Science and engineering

The sharp line between them is recent: Vannevar Bush drew it in the late 1940s, and defining engineering as "application of science and mathematics" makes it a subset of science. That definition hides what engineering contributes to software. Three distinctions:

1. **Nature of work.** Engineers design and build technologies that serve useful purposes; design in engineering is finding practical, safe, cost-effective implementations. Scientists search for laws explaining and predicting phenomena. Scientists find and validate recurrences; engineers listen to clients and propose technologies of value to them.
2. **Knowledge.** Scientists treat knowledge as information organized into a "body of knowledge", produced by disinterested observers weighing evidence. Engineers treat knowledge as skillful practices for designing, building, maintaining and repairing. They are immersed in communities of use, attend to reliability, dependability and safety in context, and follow standards and codes of ethics.
3. **Abstractions and models.** Science emphasizes models, engineering machines and artifacts. "Abstractions are useful for what they leave out. Machines are useful for what they leave in." "Hardware and software are interchangeable to the theorist, but not to the engineer." "The devil is in the details" is the engineer's motto; scientists eliminate the details so recurrences stand out.

When one worldview dominates, whether in a department, a curriculum or a team, the synergies are lost.

## What CT in the small contributed

The pioneers found programming an "endless cycle of accommodations to surprises and obstacles": incomplete specifications, machine idiosyncrasies, poor performance, memory limits and debugging. In the 1950s it was "a black art". Modularity tools followed: subroutines, macros, separately compiled modules, linkers, libraries and version control.

- ***Abstraction***: "Simplifying complex phenomena by representing only their salient features, while omitting or hiding details." In software, abstractions are "simplified models of something complicated with a simple interface." A file is a string of bits with read and write, its records scattered over a disk hidden from view. "Designing hierarchies of abstractions is seen as the only way to master the enormous complexity of software." Finding good abstractions is an essential design skill. Its companion is *generalization*, "Extending a solution to a broader class of similar problems." Brooks's warning cuts the other way: abstractions that abstract away complexity "often abstract away their essence."
- ***Data abstraction***: programmers designed a data structure, then a small set of subroutines operating on it. It "hides internal mechanisms of program components, while allowing the use of those components through well-defined interfaces," so programmers focus on what components do, not how. It matured into object-oriented languages.
- **Operating systems** made a system a "society of cooperating processes". A *process* is an independently executing program in private memory that other processes cannot access, standing by to perform a service on request. Operating systems also brought virtual memory (automating transfers between memory levels), file systems, interprocess messaging, and *kernels*, trusted sets of programs for basic functions that isolate processes so an error in one cannot affect another.
- Inherited precepts: modularity, abstraction, information hiding, hierarchical composition, recursion, design patterns, managing digital objects, visualization, verification and debugging.

## Principles, patterns and hints

Kernel functions have changed little since the 1970s, yet kernels grew from about 20 thousand instructions to 20 million, and vulnerability grew with them. Wirth blames the waste of cheap cycles and storage: inefficiency is covered up by faster processors and poor data design by larger storage, at the cost of reliability, robustness and ease of use. Careful design costs more but is cheaper than unreliable software once maintenance is counted. To reach DRUSS, developers use three kinds of practice:

- ***Design principles***: "descriptions of skills and strategies that developers follow when making design decisions." They are ways of thinking about the total system.
- ***Design patterns***: "descriptions of common situations a programmer is likely to encounter," with guidance on structuring the program or the process of writing it.
- ***Design hints***: "rules of thumb or morsels of advice, most useful to those with advanced skills at systems development."

**Saltzer and Schroeder's information protection principles** apply to any large system that accommodates many users and service processes:

| Principle | Directive |
|---|---|
| Economy of mechanism | Keep the design simple and small. |
| Fail-safe defaults | Deny access by default; grant access only by explicit permission. |
| Complete mediation | Check every access to every object. |
| Open design | Do not depend on attackers being ignorant of the design. |
| Separation of privilege | Grant access based on more than one piece of information. |
| Least privilege | Force every process to operate with the minimum privileges needed for its task. |
| Least common mechanism | Make shared state information inaccessible to individual processes, lest one corrupt it. |
| Psychological acceptability | Protection should be easy to use, at least as easy as not using it. |

**Patterns.** The software pattern community of the early 1990s drew on the architect Christopher Alexander. It distilled the essence of commonly solved situations so others could imitate them, for example *singleton* (limit an object to one instance) and *iterator* (sequential access to data elements). Its members are relentless about testing ideas with potential users.

**Lampson's hints.** "Designing a computer system is very different from designing an algorithm. The external interface is less precisely defined, more complex, and more subject to change. The system has much more internal structure and hence many internal interfaces. And the measure of success is unclear." Less skilled designers flounder in seas of possibilities, unsure how a choice now will affect later choices or performance. The hints are judgments skilled designers learn over time:

| | Correctness & Fit | Speed | Fault Tolerance |
|---|---|---|---|
| Use cases | Separate normal and worst cases | Safety first; Shed load; End-to-end | End-to-end |
| Interface | Keep it simple; Do one thing well; Don't generalize; Get it right; Don't hide power; Use procedure arguments; Leave it to the client; Keep interface stable; Keep a place to stand | Make it fast; Split resources; Static analysis; Dynamic translation | End-to-end; Log updates; Make actions atomic |
| Implementation | Plan to throw one away; Keep secrets; Reuse a good idea; Divide and conquer | Cache answers; Use hints; Use brute force; Compute in background; Batch processing | Make actions atomic; Use hints |

## Three structures for recurrent design patterns

**Hierarchical aggregation.** Objects consist of smaller objects connected by well-defined interfaces. Interact with an object as a unity through its interface; looking inside, ignore the environment. Each level is insulated from the details above and below.
- *Decomposition*: subdivide a large system into smaller, manageable components; in software they become modules plugged together via interfaces.
- *Modularity*: modules designed, compiled and stored separately, then assembled; they interact across precisely defined interfaces and can be reused from libraries.
- *Abstraction*: define a simplified version of something and state the operations that apply to it.
- *Levels*: peer components share a common interface. Dijkstra first used levels in 1968 to organize an operating system. Each level depended only on its components and the correctness of lower levels, which made the system provable; designing as levels yields much smaller, more easily verified systems.
- *Information hiding*: conceal implementation details. This protects users from errors caused by changes in the details, and the module from errors caused by external changes.
- *Encapsulation*: goes further, shielding everything outside an untrusted module from errors within it. It improves reusability, access restriction, protection of information from user errors, and maintainability.
- *Objects*: abstract entities "viewed and altered only through a defined set of operations", with hidden internal structure and state; a file is acted on only by open, close, read and write. A *class* is a set of objects with the same interface, and classes form their own hierarchy. Novices find objects confusing until they understand abstract machines, information hiding and synchronization.

**Virtual machines**: "a simulation of one computer by another"; Turing's universal machine was the first. Four senses:
1. Any abstract computing machine, the platform a computation runs on.
2. A simulation of a hardware computer. The late-1950s "emulation mode" let new computers run their predecessors' software; today VMware and Hyper-V simulate whole computers, and the Java Virtual Machine runs byte code anywhere.
3. A simulation of the host inside its own memory partitions, as in IBM's VM 370. Each virtual machine is identical to the mainframe except for smaller memory and runs at nearly full speed.
4. A standard environment for every program in an operating system (Multics 1968, UNIX 1972): each process runs on a template virtual machine that provides input, output and connections to the submachines it spawns.

**Clients and servers.** A *server* is a process dedicated to performing a service on request; a *client* makes requests, usually from another host, by messages over the network. Examples are network file servers, authentication servers and web servers. The idea is simple; getting communications, error control and synchronization right takes mastery of many subtle details.

## No Silver Bullet

Brooks (1987) found two complexity factors. The limits of technology can be overcome by better tools: high-level languages, interactive environments, visualization of control and data flow, faster hardware, better operating systems. The other is "our own mental ability to comprehend the essence of complex problems. Coping with complexity is intrinsic to software design and construction and will never go away." The design problem is mostly conceptual: getting an intellectual grasp of the system's functions and organizing a simple, elegant design. His remedies:
- Grow large systems in relatively easy increments.
- Reuse existing software as much as possible.
- Prototype rapidly for early feedback before technical decisions are locked.
- Above all, "cultivate great designers."

There is "no silver bullet" for the werewolf of complexity.

**Complexities added since the NATO conferences:**
- **Malware and intruders** hunt bugs in complex programs for theft, destruction and ransom.
- **Fault tolerance.** Correctness proofs assume the hardware works, but hardware is too complex to prove, tested chips carry bugs, and parts wear out or are thrown into unstable states. Fault-tolerant hardware uses extra circuits that monitor each other, for example shutting the system down rather than performing a critical operation incorrectly, which no software structure can do. "Software correctness proofs are not sufficient for correct operation."
- **Secure hardware.** Most attacks hit the lowest levels of kernel and network, where dynamic monitoring is hardest. 1960s architectures that encapsulated untrusted programs and limited error propagation were lost in the 1980s RISC (Reduced Instruction Set Computer) revolution, which cut instructions for speed. Secure hardware is coming back. Outsourced chip production lets third parties insert backdoors.
- **Machine learning.** No one knows why a trained network's weights are what they are, how to prove it correct for untrained inputs, or how to detect that it is about to go bad. This is the *fragility problem*: to what extent can we trust the AI with inputs outside its training data?
- **Safety.** In safety-critical applications an error can cause catastrophic loss of life or property.
- **Mass production of diverse applications.** Millions of apps from networks of developers selling through app stores, with development outsourced.
