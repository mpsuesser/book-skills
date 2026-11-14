# Operating systems

Papers 23, 26, 28 and 37: CTSS time-sharing and its scheduler, Dijkstra's mutual exclusion, the layered THE system with semaphores, and UNIX.

## 23. Corbató, Daggett and Daley, *An Experimental Time-Sharing System* (1962)

**Set out to.** Argue the need for time-sharing, lay out its problems, describe an experimental system for the IBM 7090, and give a scheduling algorithm with performance bounds.

Computing has had three phases: hardware construction and maintenance in the early 1950s, better languages through compilers in the mid-1950s, and better man–machine interaction through time-sharing in the early 1960s. *Time-sharing* has two meanings. One is using different parts of the hardware simultaneously for different tasks, which is **multiprogramming** and serves hardware efficiency. The other, meant here, is several persons using the computer at once, which serves the efficiency of persons. Computer efficiency matters only in the perspective of total system utility.

**The motivation.** The rate of man–computer interaction has changed little in a decade, or worsened. Bigger problems mean bigger programs, more errors and longer debugging. Under a batch monitor each bug can cost hours, if not a whole day, while debugging at the console is grossly wasteful. The goal is a "computer made simultaneously available to many users in a manner somewhat like a telephone exchange", each user working at a console at their own pace, ideally with a display.

**Construct.** A **time-sharing supervisor** runs each user program in turn for "a short burst or quantum of computation". In simple round-robin, each program resident in memory gets a quantum at least once per human reaction time (∼.2 seconds), so the system can answer single keystrokes. Response time grows with the complexity of the request, the slowness of the computer and the number of active users; with n users, each sees on average 1/n of the effective speed. That is fine for debugging, where each response needs little computation. The authors expect programming to improve "by one or two orders of magnitude".

**Hardware needs.**
1. Memory protection, so user programs cannot interfere with each other or with the supervisor.
2. Dynamic relocation of every memory access, since the supervisor may run a program from different locations.
3. Trapping of all I/O instructions in protection mode.
4. Large random-access backing storage; disks are adequate.
5. An interrupt clock to end a quantum.
6. Large core memories, perhaps a million words.

**Programming needs.**
1. Automatic charge accounting.
2. Supervisor coordination of all user I/O.
3. System programs potent enough that users think about their problem rather than coding details: compilers, editors, loaders, post-mortem programs.
4. Maximum flexibility in language choice.

**Usage needs.**
1. A special termination signal.
2. "Real-time is not computer usage-time", so keep users informed.
3. Expect malfunctions, and keep "Which program is running?" answerable.

**The experimental system.** It runs on MIT Computation Center's 7090. Two hardware modifications add 60-cycle accounting and an interrupt clock, and a special mode adds memory protection, dynamic relocation and I/O trapping. Four users share the machine: three foreground users at Flexowriter typewriters, and one passive background user running the ordinary monitor system.
- Foreground users get languages compatible with the background, a private file of programs, a debugging session that resumes where the last one ended, and work at their own pace.
- Users occupy the upper 27,000 words of core, and the supervisor permanently holds the lower 5,000.
- For want of a disk, each user has a separate private file tape and a dump tape.

**Commands.** Commands go to the supervisor at any time.
- A command line is made of segments separated by vertical strokes; the first is the command name. Each segment is the last 6 characters typed, so spacing over corrects typos. A carriage return starts the command, and the system answers WAIT and then READY.
- A quit sequence abandons a command.
- Completed commands join a waiting-command queue, which gets top priority after each quantum. With no commands waiting, the supervisor runs round-robin over the working queue, and with that empty too, it runs the background user.
- Programs leave working status for **dead** (completed), **dormant** (still restartable and examinable) or **input-output wait**.

**Observations.**
- "Once a user gets accustomed to computer response, delays of even a fraction of a minute are exasperatingly long."
- Line-at-a-time interaction is like a press-to-talk radio-telephone, character-at-a-time like an ordinary telephone. The latter needs a vestigial response program in core.
- The weakest areas are input conventions, file editing and rapid interaction while debugging, which call for experiment.
- Ultimately the foreground/background distinction could go: users would submit production work from their consoles, and "the distinction of whether one is time-sharing or not would vanish".

**The multi-level scheduling algorithm.** When the active programs exceed memory, or are too many for good response, the system is **saturated**. Under simple round-robin, service collapses abruptly at a critical number of users N, because swap time suddenly sets in (Fig 23.1). The goal is "graceful degradation of the response time and effective real-time computation speed of the large and long-running users."
1. A program entering, or one that has just responded to its user, goes to priority queue ℓ₀ = [log₂([w_p/w_q] + 1)]. Here [ ] is the integral part, w_p is the program's size in words, and w_q is the number of words that can be moved in or out in one quantum q.
2. Run the head of the lowest occupied queue ℓ for up to 2^ℓ quanta. If it has not finished (that is, not responded to its user), put it at the end of queue ℓ + 1.
3. When level ℓ is exhausted, go to ℓ + 1 with 2^{ℓ+1} quanta.
4. If a lower level ℓ′ becomes occupied, put the current user back at the head of queue ℓ and restart at ℓ′.
5. If a program's memory size changes from w_p to w_p″, it goes to the end of queue ℓ″ = ℓ + [log₂([w_p″/w_p] + 1)].

**Bounds.**
1. **Efficiency.** A program always runs at least as long as its swap time, so efficiency never falls below one-half. Equivalently, one of n users fares no worse than if 2n users all fit in memory.
2. **Response.** With at most N active users, t_r ≤ 2Nq([w_p/w_q] + 1).
3. **Long runs.** At higher levels the relative swap time becomes vanishingly small. "Long runs must in effect prove they are long so that programs which have an unexpected demise are detected quickly." The maximum level needed for asymptotic swap overhead p is L = [log₂([w_pmax/(p·w_q)] + 1)].
4. **Multi-level versus single-level.** Take n equal programs at level ℓ, each ready to respond in its first quantum at level ℓ + j. The multi-level delay is T_m ∼ q2^ℓ{n(2^j − 1) + (n − 1)2^j}, and single-level round-robin gives T_s ∼ q2^ℓ·n(2^j − 1). So T_m/T_s ∼ 1 + ((n − 1)/n)(2^j/(2^j − 1)) ∼ 2. That is the least favorable case, with no swaps; with swaps the ratio is smaller and may be ≪ 1. Programs that finish just as their quanta complete get response twice as fast, T_m/T_s ∼ 1/2.
5. **Highest serviced level.** Classification is automatic, "depending on performance and program size rather than on the declarations (or hopes) of each user". Degradation starts with the large and long-running users. With N users at level ℓ, each running 2^ℓ quanta and returning after a user response time t_u, level ℓ + 1 gets no service if Nq2^ℓ ≥ t_u. So the guaranteed active levels are ℓ_a ≤ [log₂(t_u/(Nq))].

**Mechanics (Fig 23.2).**
- When a quantum finishes, set t ← t − q.
- If a user was initiated at some ℓ′ < ℓ, put the current user at the head of queue ℓ and set ℓ ← ℓ′. Otherwise, if t > 0, run another quantum. If t = 0, move the user to the end of queue ℓ + 1 and find the head of the lowest occupied queue.
- If that program is in memory, set t ← q·2^ℓ and start. If not, read it in if there is room. Failing that, consolidate slack if there is enough; failing that, read out the lowest-priority program and try again.
- To hide seek and latency, keep running the last user while the swap is readied.

**Numbers for the 7090.**
- q = 16 ms, with 1% switching overhead.
- w_q = 120 words, for one IBM 1301 disk without seek or latency.
- t_r ≤ 8Nf seconds for programs of (32K)f words.
- ℓ_a ≤ log₂(1000/N), taking t_u = 16 sec.
- ℓ₀ ≤ 8 for programs of at most 32K words.

Requiring max ℓ_a = max ℓ₀ gives a conservative N of 4, with a worst response of 32 seconds for a trivial reply. N is small because the disk moves data at only 3.3% of the core memory's rate. A high-capacity drum would multiply w_q by 30 and serve 120 users with the same response, though total computational capacity would be unchanged. All such estimates depend on distributions that experience cannot yet supply.

**Conclusion.** Present computers suffice for moderate time-sharing, and the hardware problems are solvable. But "until the system programming is completed, especially the critical time-sharing supervisor, the computer is completely worthless."

**Led to.** At a 1954 MIT summer school, Hopper proposed several small mass-produced computers working in parallel. Backus answered that, since more speed costs little more, "by time sharing, a big computer could be used as several small ones". McCarthy proposed time-sharing the Computation Center's IBM machine around 1958 (21).

Corbató, with Marjorie Merwin (later Daggett) and Robert Daley, cobbled the system together in 1961, aiming "to convince the skeptics that it was not an impossible task". People could not imagine the psychological difference an interactive terminal made, the difference between writing a letter and making a phone call; once they tried it, the reaction was "Hey, it talks back. Wow!" The **Compatible Time-Sharing System (CTSS)** took its name from the compatibility of interactive and background jobs.

MULTICS ("MULTiplexed Information and Computing Service") was built on it and supplanted it, and was commercialized with limited success. Bell Labs pulled out of MULTICS, and Ken Thompson took its lessons into UNIX (37), whose name is a lighthearted pun. ELIZA (27) depended on this kind of time-sharing.

## 26. Dijkstra, *Solution of a Problem in Concurrent Program Control* (1965)

**Set out to.** Solve a problem open since at least 1962, solvable or not, and give the problem, the solution and the proof.

**The problem.** N computers each run a cyclic process, and each cycle contains a **critical section**. At any moment only one computer may be in its critical section: **mutual exclusion** of critical-section execution. The computers communicate through a common store, in which writing a word and nondestructively reading a word are indivisible operations; simultaneous accesses to one location happen one after the other in an unknown order. The requirements:
- (a) The solution must be symmetrical among the N computers, with no static priority.
- (b) Nothing may be assumed about their relative speeds, not even that the speeds are constant.
- (c) A computer stopped well outside its critical section must not be able to block the others.
- (d) If more than one is about to enter, it must be impossible to choose finite speeds that postpone the decision forever. "After you"–"After you" blocking, however improbable, is not a valid solution.

"We beg the challenged reader to stop here for a while and have a try himself."

**The solution.** The common store holds `boolean array b, c[1:N]; integer k`, with 1 ≤ k ≤ N. b[i] and c[i] are set only by the i-th computer and inspected by the others. All computers start well outside their critical sections with every boolean true; the starting value of k does not matter. The program for the i-th computer:

```
integer j;
Li0: b[i] := false;
Li1: if k ≠ i then
Li2:   begin c[i] := true;
Li3:     if b[k] then k := i;
         go to Li1
       end
     else
Li4:   begin c[i] := false;
         for j := 1 step 1 until N do
           if j ≠ i and not c[j] then go to Li1
       end;
     critical section;
     c[i] := true; b[i] := true;
     remainder of the cycle in which stopping is allowed;
     go to Li0
```

**The proof.**
- **Safety.** The only way into the critical section is to complete Li4 without jumping back, which means finding every other c true after setting one's own c false. So no two computers can be in their critical sections at once.
- **No infinite "After you".** When no computer is in its critical section, at least one of the looping computers, and therefore exactly one, enters in due time.
  - If the k-th computer is not looping, b[k] is true. The looping computers find k ≠ i, and one or more of them find b[k] true at Li3 and assign k := i.
  - After the first assignment, b[k] is false, so no new computer decides to assign. When the decided assignments are done, k points to a looping computer and stays there until that computer completes its critical section.
  - The k-th computer waits in Li4 until all other c's are true. That will happen, because the other looping computers find k ≠ i and set their c's true.
- "And this, the author believes, completes the proof."

**Led to.** Lewis calls it "arguably the first scientific paper on algorithmic problems—as opposed to language constructs—in the field of concurrent programming", a "model of logical rigor, though the code is far from self-documenting". It introduced the terms *critical section* and *mutual exclusion*, and proved what are now called safety and liveness conditions. It set off research in concurrent computing, where in operating systems and databases anything that can go wrong eventually will, and only clear reasoning precludes timing bugs.

Dijkstra preferred "computing science" to "computer science" and rejected any split between theory and engineering. "The art of programming is the art of organizing complexity, of mastering multitude and avoiding its bastard chaos as effectively as possible." His name is also on a shortest-paths algorithm (1959). His semaphores followed in the THE system (28), and his letter on go to (29).

## 28. Dijkstra, *The Structure of the "THE"-Multiprogramming System* (1968)

**Set out to.** Report on a multiprogramming system built at the Technological University Eindhoven by six people at, on average, half-time. The aim was to contribute to the art of system design, including its conception, construction and verification.

**Guiding principles.**
1. "Select a project as advanced as you can conceive, as ambitious as you can justify, in the hope that routine work can be kept to a minimum." Resist expansions that only add work.
2. Select a machine with sound basic characteristics, "an interrupt system to fall in love with". Keep the specific configuration out of consideration as long as possible.
3. "Experience does by no means automatically lead to wisdom and understanding", so make a conscious effort to learn.

Half-time people slow production by at least a factor of four. "The intellectual level needed for system design is in general grossly underestimated."

**The machine** is the Electrologica EL X8:
- core cycle 2.5 μsec, 27-bit words, 32K at present;
- a drum of 512K words, 1024 words per track, revolution time 40 msec;
- indirect addressing suited to a stack;
- a sound system for peripherals and interrupts;
- many low-capacity channels, ten of them in use: three paper tape readers at 1000 char/sec, three punches at 150 char/sec, two teleprinters, a plotter and a line printer.

The goal is to process a continuous flow of university user programs smoothly, so as to cut turnaround for short programs, use peripherals economically, control the backing store automatically, and run applications that need a general-purpose computer's flexibility but not its capacity. It is not multi-access. User programs are in ALGOL 60, not machine language.

**Mistakes.** Two major ones. The group designed too long for "a perfect installation", and handling peripheral breakdowns ("pathology") cost more energy. And they gave debugging only scanty thought. Real-time interrupts make errors irreproducible, so a program error looks like an occasional machine malfunction, and the group was "terribly afraid". "This decision, inspired by fear, is at the bottom of what I regard as the group's main contribution": a refined multiprogramming system can be designed so that "its logical soundness can be proved a priori and its implementation can admit exhaustive testing". Only trivial coding errors turned up, about one per 500 instructions, each located within 10 minutes. "The resulting system is guaranteed to be flawless."

**Construct.**
- **Storage allocation.** THE strictly separates memory units, **pages** (core pages and drum pages), from information units, **segments**, each of which just fits a page. Segment identifiers are far more numerous than pages. Each maps to a **segment variable** in core that is either empty or names the page holding the segment. Consequences: a dumped segment need not return to the same drum page, so the system picks a free page with minimum latency, and there is no drum allocation problem at all.
- **Processor allocation.** In a sequential process only the succession of states has logical meaning, not the actual speed. So the system is "a society of sequential processes, progressing with undefined speed ratios":
  - one process per user program;
  - one per input peripheral (buffering) and per output peripheral (unbuffering);
  - a **segment controller** for the drum;
  - a **message interpreter** for the console.

  They achieve **harmonious cooperation** through explicit mutual synchronization statements. These are necessary because no speed assumptions are allowed, and possible because temporarily delaying a process never harms its internal logic. Cooperation can then be established "by discrete reasoning", independent of the actual number of processors.
- **The hierarchy.** Each level provides an abstraction for the levels above.
  - **Level 0** allocates processors to processes, with a real-time clock interrupt to prevent monopoly and a priority rule for quick response. Above it, the number of processors is irrelevant: "the actual processor that had lost its identity."
  - **Level 1**, the segment controller, keeps the books for the automatic backing store. Above it, information is identified by segment, and pages lose their identity.
  - **Level 2**, the message interpreter, allocates the console keyboard. An operator's opening sentence must be interpreted before the system knows which process it addresses, which is the logical reason for a separate process. Above level 2, each process acts as if it had a private console, and "one conversation at a time" is enforced by synchronization. The interpreter sits above the segment controller because its vocabulary is stored in segments.
  - **Level 3** buffers input and unbuffers output, abstracting peripherals into "logical communication units". It sits above the message interpreter because it must be able to tell the operator about malfunctions.
  - **Level 4** holds the independent user programs.
  - **Level 5** is the operator.

**Design and verification.** A long conception stage developed the art of deducing mutual synchronization from the requirements (no information used before it is produced; no peripheral given two tasks at once), and of proving that the society behaves properly in time. Construction was plain machine code. Verification proceeded level by level from level 0 on a virgin machine. A new level was added only after the one below was thoroughly tested, by test processes that both forced the system into all relevant states and verified its reactions.

At level 1 the relevant states are sequential processes demanding core pages. The clock is so immaterial there that "one of the testers indeed forgot its existence!" Without levels 0 and 1, the system would react directly to every weird succession of clock and drum interrupts, the relevant states would explode, and "exhaustive testing would have been an illusion".

**Conclusion.** One cannot test a general-purpose object on all its cases, and the relevant test cases cannot be chosen by treating the mechanism as a black box. It is the designer's responsibility to structure his mechanism so effectively "that at each stage of the testing procedure the number of relevant test cases will be so small that he can try them all and that what is being tested will be so perspicuous that he will not have overlooked any situation." "The larger the project, the more essential the structuring!"

**Appendix: semaphores.** A **semaphore** is a special-purpose integer variable, initialized to 0 or 1 before the processes start, and accessed only by two primitives, P and V.
- **P(sem)** by process Q: decrease by 1. If the result is nonnegative, continue. If negative, Q stops and is booked on the semaphore's waiting list, and no processor is allocated to it until a V on the same semaphore.
- **V(sem)** by R: increase by 1. If the result is positive, nothing more happens. If it is nonpositive, one waiting process is removed from the list, and its progress becomes permissible again.
- **Corollary 1:** if the value is nonpositive, its absolute value is the number of processes waiting.
- **Corollary 2:** "The P-operation represents the potential delay, the complementary V-operation represents the removal of a barrier."
- P and V are indivisible actions. Which waiting process a V releases is undefined and logically immaterial. A process loses permission to progress only through a P on a semaphore with nonpositive value.

**Mutual exclusion with a semaphore:**

```
begin semaphore mutex; mutex := 1;
  parbegin
    begin L1: P(mutex); critical section 1; V(mutex);
              remainder of cycle 1; go to L1 end;
    begin L2: P(mutex); critical section 2; V(mutex);
              remainder of cycle 2; go to L2 end
  parend
end
```

For n processes, mutex ranges from 1 down to −(n − 1). Critical sections are used "always, and only" to inspect and modify the state variables that describe the system's state.

**Private semaphores** belong to one process: only it performs P on them. They start at 0, with maximum 1 and minimum −1.
- *Waiting pattern:* P(mutex); inspect and modify the state variables, including a conditional V(private semaphore); V(mutex); P(private semaphore). If the process should continue, it does V on its own semaphore; otherwise it leaves the obligation to others, recorded in the state variables.
- *Releasing pattern:* P(mutex); modify and inspect the state variables, including zero or more V's on other processes' private semaphores; V(mutex).
- Any strategy for assigning peripherals and buffers can be built this way. An **unstable situation**, such as a free reader together with a process that needs one, is removed in the same critical section that created it.

**Proving harmonious cooperation.** All processes are cyclic, with a neutral **homing position** that all occupy when the system is at rest. Leaving it means accepting a task; a process returns only when the task is done. Three things must be proved:
1. A single initial task cannot generate infinitely many generations of tasks. Processes generate tasks only for lower levels, so there is no circularity. One precaution: a segment fetched from the drum stays in core until its requester has used it, to prevent "unproductive page flutter".
2. All processes cannot be at home while a generated task is still unaccepted.
3. After an initial task is accepted, all processes eventually return home. That means no circular waits, where P waits for Q, which waits for R, which waits for P: "the Deadly Embrace".

**Led to.** The project cemented Dijkstra's reputation "as a computer scientist in the fullest sense of the word" and stimulated academic research into provable, secure and reliable operating systems. Lewis calls the semaphore "a very important control abstraction, encapsulating in a form suitable for general reasoning a variety of machine-specific techniques then in use for atomically locking and unlocking resources in concurrent programs." The Introduction places THE between CTSS (23) and UNIX (37).

## 37. Ritchie and Thompson, *The UNIX Time-Sharing System* (1974)

**Set out to.** Describe a general-purpose, multi-user, interactive operating system for the DEC PDP-11/40 and 11/45. It has features seldom found even in larger systems:
1. a hierarchical file system with demountable volumes;
2. compatible file, device and inter-process I/O;
3. the ability to start asynchronous processes;
4. a command language selectable per user;
5. over 100 subsystems, including a dozen languages.

"Perhaps the most important achievement of UNIX is to demonstrate that a powerful operating system for interactive use need not be expensive either in equipment or in human effort": hardware as cheap as $40,000, and less than two man-years on the main system software. The hoped-for characteristics are "simplicity, elegance, and ease of use." PDP-11 UNIX has run since February 1971, at about 40 installations.

**The file system.** "The most important job of UNIX is to provide a file system." There are three kinds of file.
- **Ordinary files** hold whatever the user puts there, with no structure imposed: "the structure of files is controlled by the programs which use them, not by the system."
- **Directories** map names to files. A directory behaves exactly like an ordinary file, except that unprivileged programs cannot write it.
  - Names are up to 14 characters. A **path name** is directory names separated by "/", ending in a file name. A leading "/" starts at the root, as in /alpha/beta/gamma; otherwise the path starts in the current directory.
  - A file can appear in several directories under different names. Each entry is a **link**, and "all links to a file have equal status"; the file disappears with its last link.
  - Every directory has at least the entries "." (itself) and ".." (its parent). Apart from these, each directory appears in exactly one other, so the hierarchy is a rooted tree. That simplifies programs that visit subtrees and keeps parts of the hierarchy from being cut off.
- **Special files** are the "most unusual feature". Each I/O device has at least one, in /dev, read and written like an ordinary file; writing /dev/ppt punches paper tape. The advantages are threefold: file and device I/O are as similar as possible; a device name can go wherever a file name is expected; and one protection mechanism serves both.

**Protection.** Each user has a unique ID, and each file is marked with its owner's ID and seven protection bits. Six give read, write and execute permission for the owner and for everyone else. The seventh is **set-user-ID**: while the file runs as a program, the user ID temporarily becomes the file owner's. That lets privileged programs use files inaccessible to others; the invoker's real ID is always available for checking credentials.

For example, mkdir is owned by the super-user and has set-user-ID set; it checks authorization and creates the directory with "." and "..". Anyone may set the bit on their own files, without administrative intervention. The super-user is exempt from access constraints, so the file system can be dumped and reloaded.

**I/O calls** remove the differences between devices and between access styles. There is no distinction between random and sequential access and no logical record size; a file's size is the highest byte written.
- filep = open(name, flag) returns a small-integer **file descriptor**. create makes or truncates a file and opens it for writing.
- There are no user-visible locks: "locks are neither necessary nor sufficient, in our environment". No large single-file databases are kept by independent processes, and locks would not stop two users editing copies of the same file.
- n = read(filep, buffer, count) and n = write(filep, buffer, count) transfer up to count bytes from a pointer that advances by n. A read of a typewriter returns at most a line, and n = 0 means end of file. Writing beyond the end grows the file.
- location = seek(filep, base, offset) moves the pointer relative to the beginning, the current position or the end.

**Implementation: i-nodes.** A directory entry holds a name and an **i-number**, an index into the **i-list** kept on the device. Each entry, an **i-node**, holds:
1. the owner;
2. the protection bits;
3. the physical disk or tape addresses;
4. the size;
5. the time of last modification;
6. the number of links;
7. a directory bit;
8. a special-file bit;
9. a "large" or "small" bit.

How the operations work:
- open and create turn a path name into an i-number. Link adds a directory entry with the same i-number and increments the link count. Remove decrements it, and at zero frees the blocks and the i-node.
- Blocks are 512 bytes, and an i-node has room for eight addresses. A small file of up to eight blocks is addressed directly. In a large file, each address points to an indirect block of 256 addresses, for up to 8 · 256 · 512 = 1,048,576 (2²⁰) bytes.
- For a special file, the first address word holds the device type and subdevice number.
- mount keeps a table keyed on the (i-number, device) of an ordinary file; during a path scan a match is replaced by i-number 1 (every file system's root) on the mounted device.
- I/O looks synchronous and unbuffered but is buffered underneath: a single-byte write finds or reads the block, replaces the byte, queues the block for writing and returns.
- The linear i-list allows a simple, fast consistency check, independent of the hierarchy: the used and free portions must be disjoint and exhaust the device.
- One peculiarity is who should be charged for a linked file. UNIX currently charges no fees at all.

**Processes and images.** An **image** is the "current state of a pseudo computer": core image, registers, open files, current directory. A **process** is the execution of an image. User core has three segments: write-protected program text at location 0, shared by all processes running the same program; a writable data segment at the first 8K boundary above it; and a stack at the top, growing downward.
- **processid = fork(label)** is the only way to make a new process. It splits into two processes with independent copies of the core image and shared open files. The parent returns directly, the child goes to label, and each receives the other's ID.
- **filep = pipe()** returns a descriptor for an interprocess channel, passed from parent to child by fork. A read waits until another process writes. "Neither process need know that a pipe, rather than an ordinary file, is involved." A pipe must be set up by a common ancestor.
- **execute(file, arg₁, …, arg_n)** replaces code and data but keeps open files, current directory and process relationships. It returns only on failure, so it "resembles a 'jump' machine instruction rather than a subroutine call."
- **processid = wait()** suspends until a child completes. **exit(status)** destroys the image, closes files, and passes status to the parent through wait.

**The Shell.**
- *Commands.* A command is a name and arguments separated by spaces. The Shell finds the file, executes it, and prompts again; if the name is not found, it tries prefixing /bin/.
- *Standard I/O.* Programs start with file descriptor 0 open for reading and 1 open for writing, both on the typewriter. "ls >there" puts the listing in a file named there, and "ed <script" takes input from script. The Shell interprets the redirection, so commands need no special code.
- *Filters.* "ls | pr -2 | opr" runs the commands simultaneously, each one's standard output feeding the next one's input. The alternatives are worse: temporary files, or ls itself accepting pagination and printing options, which would be "surprising, and in fact unwise for efficiency reasons". "A program such as pr which copies its standard input to its standard output (with processing) is called a filter."
- *Separators.* ";" sequences commands. "&" runs a command in the background, with the Shell printing its process ID and prompting immediately. Parentheses group: "(date; ls) > x &".
- *The Shell as a command.* "sh < tryout" runs a command file.
- *Implementation.* The Shell reads a line, forks, and the child executes the command while the parent waits; for "&" it simply does not wait. Redirection is easy because open assigns the smallest unused descriptor: the child closes 0 or 1 and opens the named file just before executing. The Shell loops until end of file on its input.
- *Initialization.* init creates one process per typewriter line, which asks for a login and checks the password file. With the right password it sets the current directory and user ID and executes the Shell. When that Shell ends, init recreates the process, so typing end-of-file logs a user out.
- *Other programs as Shell.* A password entry may name another program. Secretaries can get the editor directly, and game players are confined to their game, "unable to investigate the presumably more interesting offerings of UNIX as a whole."

**Traps.** Hardware faults terminate the process and write its image to a file named core for the debugger. The interrupt signal stops a process without a core file, and quit forces one. The Shell ignores quits; the editor catches interrupts and returns to command level; floating point can be interpreted by catching unimplemented-instruction traps.

**Perspective.** "Perhaps paradoxically, the success of UNIX is largely due to the fact that it was not designed to meet any predefined objectives." Thompson found a little-used PDP-7, and the goals were "building a comfortable relationship with the machine and with exploring ideas and inventions in operating systems". Three considerations shaped it:
1. It was written by programmers for programmers, and "a properly designed interactive system is much more productive and satisfying to use than a 'batch' system".
2. Severe size constraints encouraged economy and "a certain elegance of design", a "thinly disguised version of the 'salvation through suffering' philosophy, but in our case it worked."
3. Almost from the start the system maintained itself: its designers used it and fixed deficiencies "before it is too late".

There are no large access-method routines and no complicated control blocks; device dependencies are pushed into the system. The Shell is an ordinary swappable user program. Given a Shell that spawns processes, "I/O redirection, background processes, command files, and user-selectable system interfaces all become essentially trivial to implement."

**Led to.** CTSS (23) was succeeded by MULTICS. Bell Labs withdrew from MULTICS, and a few of its researchers built a simpler, leaner system, mostly to make writing and debugging code easier. It was originally single-user on a small computer, hence the play on "MULTICS". The team developed C, a "low-level higher-level language", to implement it. The hierarchical file structure, inherited from MULTICS, was widely influential. Cheap licenses to universities made UNIX the de facto standard in computer science departments, and generations grew fond of its "modular, flexible, unencumbered design". It was the basis for BSD, GNU ("GNU's not UNIX"), Linux and Apple's Mac OS. Ritchie and Thompson won the Turing Award in 1983.
