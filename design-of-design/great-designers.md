# Great designers and design processes

"Great designs do not come from great processes; they come from talented people doing hard work." Brooks lists products that have fan clubs alongside comparable ones that don't:

| Fan club | No fan club |
|---|---|
| iPhone | cell phone |
| Apple II | PC |
| Macintosh interface | Windows |
| UNIX | Z/OS |
| Pascal | Algol |
| Fortran | Cobol |

Every product without a fan club came from a formal product process, with many inputs and approvals. Every product with one came from outside the normal process. The atomic bomb, the nuclear submarine, the stealth airplane, the Spitfire and penicillin also came from small teams set apart.

## Why product processes stifle

A product process is, by nature:
- **Conservative.** It fits similar things into one framework, and the innovative doesn't fit.
- **Aimed at predictability.** It defines the product by business needs before a great designer has spent time on it. "Predictability and great design are not friends."
- **Fighting the last war.**
- **Veto-oriented.** It demands the consensus of many experts, each watching for a separate cause of failure.

Consensus stifles in several ways:
- Each watchdog is paid to avoid mistakes, and so is biased toward reasons not to proceed.
- Compromises take off the sharp edges. "But the sharp edges are the cutting edges!"
- Consensus with the past is codified as rules. Each mistake begets a new rule; rules are easily born and rarely die, and bureaucracies grow more Byzantine as they succeed.
- Consensus eats the scarce resource, which is the great designers' time.

IBM's Böblingen laboratory had great talent and strong leadership. It had followed the Corporate Product Procedure, a manual of more than 100 pages, conscientiously and scrupulously, and it had never got a product into IBM's main line. Successful project managers in other labs made bold "exceptions" to the rules at the right times. Brooks sent such an experienced procedure manipulator to manage the System/360 Model 20 there, and it became phenomenally successful.

**What process is properly for.** Corporate approval, catching obvious oversights from experience, and agreeing a schedule and budget are all inescapable. "The trick is to hold 'process' off long enough to permit great design to occur, so that the lesser issues can be debated once the great design is on the table—rather than smothering it in the cradle."

**Follow-on products** are what processes suit. After an innovative product:
- use reveals its shortcomings;
- users put it to unexpected uses that enlarge the concept;
- demand grows for a more capable product, with readiness to pay;
- popularity breeds lock-in.

A follow-on is more constrained, and must select among enhancement directions. Cycles of product definition, market forecasting, cost estimation and price estimation do that efficiently, because forecasting depends on experience with similar products. "Thus, product processes are, properly, designed for follow-on products. For innovation, one must step outside of process."

**Process raises the floor.** Measures such as the Capability Maturity Model raise the low end and the average of a community's practice. "No amount of process improvement can raise the ceiling of the community's practice."

## What to do when process and greatness clash

- **Find the great designers.** Talents are unevenly distributed and their range is enormous; no two people share a bundle of talents. "A wise leader organizes by drawing responsibility boxes around the people he has and can get." Do not put people into abstractly ideal boxes. Organizations must "cold-bloodedly recognize" that people who have done great designs are likely to do more if entrusted with the freedom and authority to.
- **Have bold leaders who demand innovation.** The top leader must passionately want innovative products.
- **Make a process that permits great design.** Delegate the pruning of the process to first-class talent with sweeping authority, for a limited task and time.
  - **Constrain only the crown jewels.** The product procedure must explicitly identify the matters of fundamental importance and constrain those, *and those only*. "It must securely protect the crown jewels, but, equally important, it must eschew building high fences around the garbage cans." Protectors' instinct is to overprotect. The TUCC case in `case-studies.md` shows the pattern in a governance design.
  - **Provide easy, swift exceptions**, available at the appeal of any project manager and needing the approval of only one sufficiently high-level boss: "All rules can be broken."
- **Shelter the core.** System/360's core design team was insulated from normal oversight. Bold managers at several levels recruited talent and found enough money. The products went through the standard processes, with word from the top that the processes would bend. That meant a weekly struggle, in which the process people's skills were essential.

## Entrust the design to a chief designer

Conceptual integrity requires one chief designer. Entrusting means four things:
1. **The manager does not second-guess the design.** The manager is apt to be a lesser designer with fragmented attention, and design and management are very different jobs.
2. **The chief designer's authority is crystal clear.** It is complete authority over the design, and the chief designer ranks sociologically equal with the project manager.
3. **The chief designer is shielded** from watchbirds outside the project and protected from diversions of time.
4. **The chief designer is given tools and help** as they see the need.

## Where great designers come from

**Teach them to design by critiqued practice.** Following Schön, Brooks holds that Technical Rationality (learn the science, then apply it) is the wrong model for professional skill. Professional skills are mastered by *critiqued practice*: medicine's clinics, architecture's studio.
- Start critiqued design in the first year, alongside the science.
- Teach style by having students design in a master's style: an architecture in the style of Cray, a fugue in the style of Bach, a building in the style of Wren. A mentor points out the stylistic inconsistencies and critiques how well the work meets its constrained objectives. This needs a mentor bold enough to give subjective criticism.
- "The most effective way for a designer to learn other design styles is to undertake to teach them to other designers."

**Recruit for design brilliance.** Managers subconsciously ask "Could he do well the job I'm doing?" That favors articulate leaders and overlooks the introverted, slow-spoken and unconventional. Look at portfolios of design work, not oral presentations; Microsoft has candidates write programs.

**Grow them deliberately**, as organizations grow managers and officers: identify them early, track them, give them mentors, rotate them, make them aides to top professionals. Technical organizations rarely do this for nonmanagerial technical leaders.
- **A real, honorable dual ladder.** Matching salaries is easy. Equal prestige needs strong proactive measures: equal offices, equal staff support, and reverse-biased raises when duties change. Managers incline to think their own tasks harder.
- **Planned formal education.** Retool continually, with a short course every year; a good teacher can double learning efficiency. Deepen and broaden by studying good and bad designs. Formal education's advantage is detachment, so seek it outside the organization. Brooks's most productive single act as a manager was sending Ted Codd mid-career to a Michigan PhD. Codd's research led him to the relational database and a Turing Award.
- **Planned varied work experience**: a career designed for variety, depth and spiraling challenge. Include service in user organizations.
- **Sabbaticals outside the organization**: on loan to a customer, teaching, or in a government agency.

**Manage them imaginatively.** John Cocke, whose ideas run through pipelining, global compiler optimization and RISC, couldn't manage and rarely published; he thought and talked. Ralph Gomory treated "*each* of his great minds differently—according to their nature and needs." Cocke was the highest-paid person in IBM Research "because he was the highest contributor."

**Protect them fiercely:**
- **From distraction**, so they can reach and keep the state of *flow* (DeMarco and Lister, *Peopleware*). The enemies of flow are meetings, phone calls, email, rules and constraints, staff and "service" groups that make rules to simplify their own jobs, customers, and professional visitors and journalists.
  - Give designers quiet mornings.
  - Opel closed the Boca Raton PC lab to corporate staffers.
  - Brooks closed System/360 to non-project visitors from January to April 1964.
- **From managers.** A mediocre or insecure manager smothers creativity, fails to recognize jewels, and may resent a better-paid designer. Higher management must raise that manager's vision of their role and train them in encouraging a team.
- **From managing.** Potentially great designers sidetracked into management never reach their potential, and the culture pushes them there. Cray moved his team into seclusion, and each time success pulled him toward management, he left to found a new company.

## Growing yourself as a designer

You alone are responsible for your growth; plan a program.
- **Sketch designs constantly**, and detail some of them fully. "The devil is indeed in the details, and many a grand scheme has foundered on a little submerged rock." Software designers should keep a notebook of patterns they meet and invent.
- **Seek knowledgeable criticism.** Critiqued practice is the method that works, in law, medicine, architecture, the guilds and the PhD dissertation.
- **Study exemplars and precedents.**
  - Follow the lineage back: Adam learned from Wren, Wren from Palladio, Palladio from the Romans.
  - Precedents that survived centuries of criticism have deep excellence; find and master it before going in a different direction.
  - Study commercially produced designs, which passed the real-money test, more than designs that were only published.
  - **Assume competence.** Ask "What led such a smart designer to do that?" rather than "Why did he do such a fool thing as that?" The answer lurks in that designer's objectives and constraints.
  - Write your studies in a common format: common structure, a standard sketch scale, common prose elements, a common formal description language, and a short critique.
- **Do a self-education project.** Brooks's example: a 1,000-square-foot house for two parents, a son of 3 and a daughter of 6, on a somewhat wooded northern Virginia suburban lot 50 ft on the street and 70 ft deep, facing south. Keep a dated journal of questions, decisions and reasons. Then answer:
  - What more detailed program did you build?
  - Which constraints did you deduce?
  - What was the budgeted commodity, and how did you manage it?
  - Which desiderata did you follow?
  - How did you decide which of two alternatives was better?
  - Where did CAD help and where did sketching help, by phase?

  Finally, sketch the design trajectory from the journal and assess the good points and the weaknesses.

**Brooks's recommended reading** on the design process:
- **Blaauw and Brooks, *Computer Architecture: Concepts and Evolution*.** §1.1 distinguishes architecture, implementation and realization; §1.2 formalizes the design tree; §1.4 defines what makes an architecture good.
- **Software design papers.** Boehm's collected papers, and Parnas's (edited by Hoffman and Weiss), are the two indispensable sets.
- **Brooks, *The Mythical Man-Month*.** "No silver bullet" separates the essential from the accidental.
- **Burks, Goldstine and von Neumann, "Preliminary discussion of the logical design of an electronic computing instrument" (1946).** Brooks calls it "The most important computer paper ever written."
- **Cross, Dorst et al., *Research in Design Thinking*.** It contains Cross's devastating critique of Simon.
- **Hales, *An Analysis of the Engineering Design Process in an Industrial Context*.** Probably the most complete published documentation of a real design process.
- **Hennessy and Patterson, *Computer Architecture: A Quantitative Approach*.**
- **Mills, "Top-down programming in large systems."** It argues for incremental design.
- **Royce, "Managing the development of large software systems."** It both describes and decries the Waterfall.
- **Schön, *The Reflective Practitioner*.**
- **Simon, *The Sciences of the Artificial*.** It is the most influential proposal of the Rational Model.
- **DeMarco and Lister, *Peopleware*.**
- **Winograd et al., *Bringing Design to Software*.**
- **Wozniak, *iWoz*.**
