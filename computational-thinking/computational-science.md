# Computational science

The dimension in which scientists brought computing into science. *Computational science* is the branches of every field that specialize in computation: computational physics, bioinformatics, digital humanities and more. Von Neumann (1955): "The sciences do not try to explain, they hardly even try to interpret, they mainly make models."

Models written as differential equations were usually incomputable without closed-form solutions. The supercomputers of the 1980s were the tipping point. Simulation became a third way of doing science alongside theory and experiment, and was described as "the most significant scientific paradigm shift since quantum mechanics." This wave of CT was started by scientists in other fields, not by computer scientists, and each field's CT grew from within it. Kenneth Wilson won the 1982 Nobel Prize in physics for computational renormalization group methods that revealed how materials change phase. He campaigned for the idea that every discipline has *grand challenge* problems that yield to massive computation, a campaign that ended in the US High Performance Computing Act of 1991. By extrapolating Moore's law, scientists predicted accurately when each challenge would fall: aeronautics engineers projected that by 1995 they could design a safe airliner by simulation instead of wind tunnels, and Boeing's 777 first flew in 1994. "Instead of computing becoming more like other sciences, other sciences became more like computing." Simulation reaches where theory and experiment cannot.

## Three roles of the scientist

- **Experimenter**: gathers data to explore and isolate phenomena, describe recurrences, and reveal when a hypothesis works and when it does not.
- **Theoretician**: designs mathematical models to explain what is known and predict what is not.
- **Computational explorer**: uses the computer as a simulator, which "could make any computer into a laboratory," evaluating models and producing data for analysis.

**Numerical methods.** Numerical analysts made models computable on finite-precision machines, controlling round-off and raising speed. John Rice estimated that mathematical software improved by a factor of 10^12 from the 1950s to the late 1980s: 10^6 from faster hardware and 10^6 from better algorithms. The basic move: if the rate of change of f(t) is g(t), step forward in small increments with the difference equation f(t+Δt) = f(t) + g(t)Δt. The sequence of Δt-separated points is a time-series sample of the function. On a two-dimensional grid, relate f(x,y) to f(x+Δx,y) and f(x,y+Δy).

## Two aspects of CT in science

1. **Modeling and simulation**: the skills of designing computational models of natural processes and methods of evaluating them.
2. **Information interpretation**: interpreting the world in terms of information processes. "For the quantities modeled, the real process behaves as if it were an information process." It is a mainstay of modern biology (sequencing and editing genes). The two are often combined, when the information process serves as a simulation of the physical process it models.

Where computing asks "Can an information process be efficiently automated?", computational scientists ask:
- Can a simulated information process replicate a real process?
- What kind of information process creates an observed phenomenon?
- What computational mechanism is behind an observed process?

**The orientations differ.** Computational science uses modeling and simulation to explore phenomena, test hypotheses and make predictions; its practitioners are often investigating behaviors, not formulating problem statements. Computer science designs algorithms to solve problems and software to do jobs for users. Collaboration works when the computing people learn the science domain and the scientists learn the computing domain. In the 1980s Denning watched a team of computational fluid dynamics PhDs invite computer science PhDs in. The computer scientists could not think fluid dynamics fluently, and the scientists ended up treating them as programmers rather than peers.

**"Computational model" means two things.**
- To a scientist: a set of equations, often differential equations, describing a physical process, which can be used computationally to generate numerical data about it. Simulations are often the algorithms that do this.
- In computing: an abstract machine that runs programs written in a language. The Turing machine is the fundamental theoretical model but too primitive for most purposes. Every language presents one: FORTRAN's is good at evaluating mathematical expressions, Java's hosts many autonomous objects exchanging messages concurrently, and C++ has objects but sits closer to the real machine and yields more efficient code.

In computational science the models are realized as abstract machines "that bring a replica of a natural information process to life," and simulations are the executions of the programs that implement them. *Simulation* uses a model's elements (theories, variables, equations, parameters and other known features of the phenomenon) to track how the system changes from one time unit to the next.

## Five modeling methods

**1. Grid visualization: the Mandelbrot set.** Walk every point on a grid, compute a function at each, and color the points by result. For each complex number c, iterate z(n+1) = z(n)^2 + c starting from z(0) = c. If the series converges (stays within limits), color c black; if it diverges, color it blue or yellow. Zooming into any small square and recomputing reveals more copies of the set at smaller scales without end. Such a simple computation yields a beautiful, mysterious object, revealing behavior no one suspected from the equations. Mandelbrot called self-similarity at all scales *fractals*: a coastline looks ragged from a satellite, from a hang glider and up close on the sand. The fractal idea drove Wilson's renormalization group algorithms and renders realistic trees and horizons quickly.

**2. State space with flow balance: the telephone exchange.** A town of K customers has potentially K^2 connections, but most customers are silent most of the time. So build switches that carry at most N calls (N far below K), and choose N to keep the chance of a busy signal small, say 0.001.
1. Define states n = 0, 1, …, N for the number of calls in progress (here N = 10).
2. New calls arrive randomly at rate λ, moving n to n+1. Each caller hangs up at rate μ, so state n moves to n−1 at rate nμ.
3. Let p(n) be the fraction of time in state n. Flow balance gives p(n) = (λ/nμ)p(n−1).
4. Guess p(0), compute each p(n) from p(n−1), then normalize so all p(n) sum to 1.
5. Find the largest N for which p(N) is below the target. If p(N) = 0.001 at N = 10, a new caller has a 0.001 chance of no dial tone with a capacity of 10 calls.

The general method: model the system as a state space of all its possible states, with transitions carrying the random rates of flow between pairs of states. Apply the *flow balance principle*, "total flow into a state equals total flow out", to get equations for the proportion of time p(s) each state is occupied. Throughput, response time and overflow probability all follow easily from the p(s), which is why the method is standard in queueing theory and system performance evaluation.

**3. State-machine controller: the doctor's waiting room.** A doctor has a four-person waiting room and a one-person treatment room. She wants a lamp in the treatment room lit when patients are waiting, and one in the waiting room lit when she is busy.
- States (n,t): n = 0…4 people waiting, t = 0 or 1 in treatment.
- Events, signaled by sensors in the three doors: arrival a moves (n,t) to (n+1,t); departure d moves (n,1) to (n,0); a call c by the doctor moves (n,0) to (n−1,1).
- The treatment-room lamp glows when n > 0, the waiting-room lamp when t > 0.

Here the state diagram plans the states and transitions of an electronic circuit rather than yielding probabilities, though the same diagram could be read with the events as flow rates.

**4. Mesh simulation: aircraft airflow.** Build a 3-D mesh of the space around the aircraft, with grid points closer together near the fuselage where air movement changes most. Convert the differential equations of airflow to difference equations on the mesh, let a supercomputer compute the flow field and forces over time, and render the results as shaded images showing where stresses are greatest. This replaced wind tunnels for new aircraft and test flights for space shuttle designs. The general form is common across science: model a process as differential equations relating each point to its close neighbors, model the space as a mesh, relate each mesh value to its neighbors by a difference equation, render the field as a colored picture, and recompute per time step for an animation.

**5. Genetic algorithms.** John Holland (1975) generalized geneticists' simulations of evolution into a method for near-optimal solutions to complex problems.
1. Encode a population of candidate solutions as bit-strings.
2. Evaluate each member's fitness with a fitness function, and select a large subset of the most-fit members.
3. Breed a new population by *mutation* (randomly flip one or a few bits) and *crossover* (choose a random breakpoint in two strings and exchange their tails).
4. Iterate until the most-fit individuals stop improving or the computational budget is exhausted.

It is surprisingly good at finding near-optimal solutions to optimization problems whose direct solution would be intractable.

## Limits of computing power

The host for grand-challenge models moved from the supercomputer to the cloud: worldwide storage and processing mobilized when needed, located no one knows where. Computations are no longer finite (start, compute, deliver, stop) but endless flows that users expect to run indefinitely, so many more people can be computational designers. The limits:

- **Sharp focus.** Most methods are very good at the task they were designed for and poor at seemingly similar ones. A new design can close the gap, as deep learning did for face recognition.
- **Fragility.** Trained recognizers are "fragile": no one knows how they will do on inputs outside their training sets. Hence the turn to machines that learn without training sets, such as the Go machine that learned by playing other machines and beat the world's highest-ranked player.
- **Explainability.** A step-by-step algorithm's conclusion can be explained by examining its steps. A face recognizer or a Go machine holds only "an inscrutable, complex mass of connections", much as we cannot explain our own actions by dissecting brains. "Other ways are needed to know when machines can be trusted and when not. Machine learning-related computational thinking is still in its infancy."
- **Problems beyond computation.** Some problems are not computational at all, or are forever too complex. Some are inherently outside science and technology. ***Wicked problems***, especially in the interactions of social communities and technologies, "defy solution when factions have enough power to defeat a proposal they dislike but not enough power to form a consensus." Millions of "clean" cars collectively produce smog in dense cities. Information technology fosters income inequality, with designers reaping far more than users. STEM education struggles to prepare students for uncertainty about work, safety nets, technology and climate. Their solutions "are not scientific, technical, or computational" and will come from social cooperation among the competing groups. CT can help by visualizing the large-scale effects of individual actions, but "only social consensus and social action can resolve wicked problems."
