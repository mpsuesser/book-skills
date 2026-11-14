# Designing the human-machine partnership

Diagnostics and design rules for any tool, interface or system where people and machines work together. Run them in order. The core definitions (symbiosis, the two aims, the division of labor, the 85 per cent) are in SKILL.md.

## 1. Which kind of system is it?

Lick distinguishes three kinds of man-machine system. Classify the user's system first.

- **Mechanically extended man** (J. D. North's term): "the human operator supplied the initiative, the direction, the integration, and the criterion. The mechanical parts of the systems were mere extensions, first of the human arm, then of the human eye." There is one organism, and the rest is there to help it.
- **Semi-automatic systems** ("humanly extended machines"): "systems that started out to be fully automatic but fell short of the goal." In these, "the human operators are responsible mainly for functions that it proved infeasible to automate", and "the men who remain are there more to help than to be helped."
- **Man-computer symbiosis**: two dissimilar partners, each doing what it does best, coupled tightly enough that the partnership "will think as no human brain has ever thought and process data in a way not approached by the information-handling machines we know today."

The tests: who supplies initiative, direction, integration and criterion? Are the people there to be helped, or to plug the holes automation left? A design that ends with people doing leftover chores is semi-automatic, and the fix is to redesign the division of labor from the human side.

## 2. Does it need symbiosis at all?

"If the user can think his problem through in advance, symbiotic association with a computing machine is not necessary." Programming a solution in advance does discipline thought. Symbiosis pays where problems are "very difficult to think through in advance", or where they "simply cannot be formulated without computing-machine aid", or where time "moves too fast to permit using computers in conventional ways." Present-day computers (and, by extension, any fixed pipeline) solve "preformulated problems" in which "all the alternatives must be foreseen in advance". When an unforeseen alternative arises, "the whole process comes to a halt."

The rival frame is Norbert Wiener's: "The modern industrial revolution is similarly bound to devalue the human brain, at least in its simpler and more routine decisions." Wiener argued for embracing the technology cautiously, not for suppressing it. Symbiosis is the design answer, which puts the machine on the routine decisions and keeps people on the rest.

## 3. Divide the functions

Start from the **genotypic differences**:
- "men are noisy, narrow-band devices, but their nervous systems have very many parallel and simultaneously active channels."
- Computers are "very fast and very accurate, but they are constrained to perform only one or a few elementary operations at a time."
- Men are "capable of 'programming themselves contingently' on the basis of newly received information"; computers are "single-minded, constrained by their 'pre-programming.'"
- Men "speak redundant languages organized around unitary objects and coherent actions", while computers speak nonredundant ones "with only two elementary symbols."

The picture is "of dissimilarity (and therefore potential supplementation)."

Then assign the work. Lick expects the two contributions to "blend together so completely in many operations that it will be difficult to separate them neatly". Where they do separate:

**People** "set the goals and supply the motivations", "formulate hypotheses", "ask questions", "think of mechanisms, procedures, and models". They remember that "such-and-such a person did some possibly relevant work". They "make approximate and fallible, but leading, contributions, and they will define criteria and serve as evaluators, judging the contributions of the equipment and guiding the general line of thought." They also "handle the very-low-probability situations", because "the sum of the probabilities of very-low-probability alternatives is often much too large to neglect." And they "fill in the gaps" where the machine has no applicable routine.

**The machine** will "convert hypotheses into testable models and then test the models against data". It answers questions, simulates, and transforms and plots data, "'cutting the cake' in whatever way the human operator specifies, or in several alternative ways if the human operator is not sure what he wants." It will "convert static equations or logical statements into dynamic models so the human operator can examine their behavior", and "carry out the routinizable, clerical operations that fill the intervals between decisions." It makes elementary statistical, decision-theory or game-theory evaluations "whenever there is enough basis to support a formal statistical analysis". In diagnosis, pattern-matching and relevance-recognizing it "will accept a clearly secondary status."

Done when every recurring operation in the user's workflow sits on one side or is marked as blended, and the people's side contains goals, hypotheses, criteria, evaluation and the rare cases.

## 4. Check the prerequisites

Lick's 1960 list of hurdles doubles as a design checklist for any symbiotic system:

- **Speed mismatch.** A fast, costly machine idles waiting on one person, so it must divide its time among many (time-sharing). Lick extrapolated to a "thinking center" combining library functions, storage and retrieval, and symbiotic functions. That picture "readily enlarges itself into a network of such centers", with cost "divided by the number of users."
- **Memory.** Store what can be summarized succinctly (the quantitative parts and the citations), not everything. "Books are among the most beautifully engineered, and human-engineered, components in existence." Plan for **indelible memory** (write once, read indefinitely) and **published memory** (read-only, "introduced into the computer already structured").
- **Memory organization.** Information must be "retrievable both by name and by pattern" and "accessible through procedure much faster than serial search." Fredkin's **trie memory** is Lick's model of storage in "resonance with human operators and their predilection to designate things by naming or pointing". Its properties: retrieval is simple; shared prefixes share storage; arguments vary in length; nothing is reserved until stored; a function can serve as an argument (enter "matrix multiplication" and retrieve the program); and examining one level shows "what thus-far similar items have been stored".
- **The language problem**, "the most serious obstacle to true symbiosis." The rule is **courses versus goals**: "instructions directed to computers specify courses; instructions directed to human beings specify goals." Human instructions "present or imply something about incentive or motivation, and they supply a criterion by which the human executor of the instructions will know when he has accomplished his task." People think in goals. Nobody leaves Boston for Los Angeles with the route specified; to paraphrase Wiener, they "try continually to decrease the amount by which they are not yet in the smog." There are two paths to goal-directed instruction:
  1. "problem-solving, hill-climbing, self-organizing programs" that, "within the loose constraints of predetermined strategies", "devise and simplify their own procedures for achieving stated goals."
  2. "real-time concatenation of preprogrammed segments and closed subroutines which the human operator can designate and call into action simply by name": programs "connected together like the words and phrases of speech". This path is simpler and can come sooner, yet it was neglected because "it would be unrewarding to develop the language before there are any computing machines capable of responding meaningfully to it."
- **Input and output**, the least advanced area. The benchmark is "the flexibility and convenience of the pencil and doodle pad or the chalk and blackboard." The three designs Lick specifies:
  1. **Desk-surface display and control.** Person and machine "draw graphs and pictures and ... write notes and equations to each other on the same display surface." The person sketches roughly and the machine renders precisely ("sketch out the format of a table roughly and let the computer shape it up with precision"). The person defines new symbols, corrects the machine's data, and instructs it via flow diagrams, as with "another engineer, except that the 'other engineer' would be a precise draftsman, a lightning calculator, a mnemonic wizard, and many other valuable partners all in one."
  2. **Computer-posted wall display** for teams. Show shared information to all on a common grid, and show each operator's own information on individual display-control units: "There would be only a confusion of uninterpretable clutter if all the information were presented on one display to all of them." Experiments showed that "informal, parallel arrangements of operators, coordinating their activities through reference to a large situation display, have important advantages over" separate consoles correlated "through the agency of a computer."
  3. **Speech.** Decide by who the user is and how fast decisions must be made. A corporation president, whose business moves slowly enough for briefings, would want symbiosis "only as an avocation", so specialists should operate the machine. A military commander cannot count on "more than ten minutes", so natural input is worth "considerable cost." Feasibility "depends heavily upon the size of the vocabulary of words to be recognized and upon the diversity of talkers and accents". Truly symbiotic dialogue needs "a vocabulary of about 2000 words", with "1000 words of something like basic English and 1000 technical terms".

## 5. Make it interactive on human terms

- **Optimize human time instead of machine time.** Batch processing kept the machine efficient and the user waiting. Time-sharing inverted that. IBM's objection ("If people were too lazy to write their programs correctly in the first place, why was that the computer's problem?") is the batch mindset to recognize and answer.
- **Response time.** "Experience has shown the importance of making the response time short and the conversation free and easy." Fano's **Threshold of Impatience**: about five seconds before the hand falls from the keyboard.
- **"People are fast, and machines are slow."** Butler Lampson's inversion: the old wisdom that machines are fast "holds only when the people are required to play on the machine's terms." Suppose the machine must present "a pageful of attractively ... formatted text, graphs, or pictures in the fraction of a second in which the human can pick out a significant pattern". Then the person is the fast one, and the system should spend machine power (one machine per person, a bit for every pixel) to keep up with them.
- **Predictability.** The Alto only had to beat a time-shared machine, and it was predictable. As Jim Morris put it, it wouldn't run faster at night.
- **Responsiveness as an instrument.** Taylor's guitar: "if the guitar is set up correctly, it is a delight to play. Otherwise, it's a struggle."
- **Run it and see.** After Turing, "the programmers can't really know the consequences of their commands until they see their program running." Interactivity is what makes exploration possible where "there were no textbooks and you had to grope your way toward the solution every step of the way."
- **Let users choose the device.** Engelbart's team tried trackballs, light pens, joysticks and knee and head controls. Users given the choice "consistently" picked the mouse, so it became the standard. When Lick doubted the RAND Tablet's design, he let the team do it their way, and later told them: "You were right ... It works."

## 6. Build models that solve themselves

**Dynamic modeling** is Lick's central use of the medium. "Ordinary mathematical models are static models ... They do not 'solve themselves.'" A dynamic model "can be set into action ... and when it is active, it does exhibit behavior and does 'solve itself.'" A digital model is both static (it can be stored and transmitted) and dynamic (it can be executed). It lives in "the moldable, retentive, yet dynamic medium—the medium within which one can create and preserve the most complex and subtle patterns and through which [one] can make those patterns operate (as programs) upon other patterns (data)." A graphics display lets the user *feel* the model's behavior. Lick: "To anyone who has had the pleasure of close interaction with a good, fast, responsive analog simulation, a mathematical model consisting of mere pencil marks on paper is likely to seem a static, lifeless thing."

What dynamic models transcend:
1. **Complexity.** Knowledge becomes process: "As soon as information is freed from documental bounds and allowed to take on the form of process, the complexity (as distinguished from the mere amount) of knowledge makes itself evident."
2. **Isolation.** Shared models make communication possible (see communication.md).
3. **Access.** Any knowledge can become reachable.

The machine's role in thought, in Lick's 1961 list: "the computer will explore consequences of assumptions. It will present complex systems of facts and relations from new points of view, 'cutting the cake another way' ... test proposed plans of action through simulation. It will mediate and facilitate communication among human beings. It will revolutionize their access to information." Its promise is "our first look at unfettered thought", allowing "a decision maker to do almost nothing but decision making, instead of processing data to get into position to make the decision."

## 7. Augment the whole system, not the person alone

Douglas Engelbart's framework, which Lick funded and which grew into the mouse, windows, hypertext and full-screen editing:

- **Definition.** "By 'augmenting man's intellect,' we mean increasing the capability of a man to approach a complex problem situation, to gain comprehension to suit his particular needs, and to derive solutions to problems." He meant not "isolated clever tricks" but "a way of life in an integrated domain where hunches, cut-and-try, intangibles, and the human 'feel for a situation' usefully coexist with powerful concepts, streamlined technology and notation, sophisticated methods, and high-powered electronic aids."
- **The unit of design** is the "system ... comprising a trained human being together with his artifacts, language, and methodology." Capability is a hierarchy of skills and concepts, and intelligence depends on that hierarchy's *organization*. A native of the Amazon arriving in New York differs from residents in "software" (a repertoire of concepts and skills), not in biological "hardware". "Just as the mechanic must know what his tools can do and how to use them, so the intellectual worker must know the capabilities of his tools and have suitable methods, strategies, and rules of thumb for making use of them." Improve tools, language and methods together.
- **Four stages** of symbol manipulation: concept manipulation, symbol manipulation, manual external symbol manipulation (stick and sand, pencil), and automated external symbol manipulation. Ask which stage a task is stuck at.
- **The writing machine** example, the first description of word processing: "trial drafts could rapidly be composed from rearranged excerpts of old drafts", and the "first draft could represent a free outpouring of thoughts in any order."
- **Where to aim.** Engelbart's three flashes: problems' difficulty was outgrowing our ability to cope ("We are in trouble"); boosting that ability is where one can "make the most difference"; and a display console shows the way. His framing question for any proposed aid: "If, in your office, you as an intellectual worker were supplied with a computer display backed up by a computer that was alive for you all day, and that was instantly responsive to every action you had, how much value could you derive from that?"

## 8. Design for the phases of looking things up

From *Libraries of the Future*, a search has three phases. Check that the system serves each:
1. **Negotiation.** The user is unsure what to ask, which is the job of a good reference librarian.
2. **Assimilation.** The user must recognize significance, extract the key ideas and fit them into a mental model, crossing the "brain-desk barrier."
3. **Application.** The user puts the result to work on the task.

The precedent is Vannevar Bush's **Memex**. The means of "threading through the consequent maze to the momentarily important item is the same as was used in the days of square-rigged ships", while "the human mind ... operates by association." Bush built retrieval on **trails** of association, not on rigid indexes. Ask whether the user's system lets people find things the way they think of them.

## 9. Make it a medium people learn in

Alan Kay took Lick's ideas to their next form:
- Engelbart's metaphor was a personal dynamic *vehicle*. Kay wanted "something much more profound: a personal dynamic *medium*."
- The design goal: "simple things would be simple, and complex things would be possible."
- Smalltalk's interface was "a 90-degree rotation of the purpose of the user interface from 'access to functionality' to 'environment in which users learn by doing.'"
- Papert's grounding: learning requires active participation, "curiosity and exploration—and the joy of discovering how each new experience fitted in with the web of memories, ideas, feelings, and sensations already in the mind." The computer is "the Proteus of machines. Its essence is its universality, its power to simulate." Children who are in control of real programs show "attention spans ... measured in hours rather than minutes."
- Kay's corollary: "the most powerful work in any genre is done not by the adults who invent it, but by the first generation of kids who grow up in it."
- Lick's educational version is to build "motivational traps" that can be "more attractive than television."
