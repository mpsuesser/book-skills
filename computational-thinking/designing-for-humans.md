# Designing for humans

The design dimension. *Design* is "a process of creating and shaping artifacts that address human concerns. In software, design means crafting software that does jobs users want done." Designers do far more than meet functional specifications: they intentionally support the practices, worlds, contexts and identities of the software's users. The iPhone succeeded on the identities and fashion statements its users project, not only on technical prowess. Aircraft panel displays that hid the most needed information in emergencies failed by design. "Design CT guides us to ways of building computing systems whose behaviors are useful and meaningful in their user communities."

Epigraphs worth carrying. Brooks: "Good judgment comes from experience, and experience comes from bad judgment." Alexander: design seeks harmony between "a form which we have not yet designed and a context which we cannot properly describe." Simulations of what you will build help when their feedback tells you where you went wrong.

## Capabilities, not a body of knowledge

Parnas holds that software engineering curricula fail because they teach a "software engineering body of knowledge" and structural rules rather than the capabilities of proficient designers. His capabilities of software developers, all oriented toward user communities:
- Design human-computer interfaces
- Design and maintain multi-version, reusable software
- Ensure that software products meet quality and security standards
- Create and use models in system development
- Specify, predict, analyze, and evaluate performance
- Be disciplined in development and maintenance
- Use metrics in system development
- Manage complex projects

## Why the engineering process breaks down

The software engineering approach to design is "a semiformal methodology to craft a set of modules and interfaces to achieve a stated functional purpose." The purpose is captured as requirements, each a specific, testable statement, and the traditional process runs:
1. Requirements
2. Formal specifications
3. System construction
4. Acceptance testing
5. Delivery to the customer

It can be run in private, with no user contact between requirements and delivery. With complex systems it breaks down: roughly a third of software projects deliver on time and within budget, a third deliver late or over budget, and the rest never deliver. One cause is the sheer number of modules and interfaces; modern operating systems have hundreds of thousands. The other is getting requirements right. Many projects meet their formal requirements and are still judged deficient. The engineer sees a requirement that was left out; the users see something obvious to any member of the community. The disconnect is *unstated user context*.

Engineers improved the process: interview methods to elicit requirements, codified design patterns, and *agile methods* that involve customers through all stages with many rapidly iterated prototypes reviewed by teams that include customer representatives. These slowed but did not stem the failures.

**Winograd's shift.** The constructor's view, that software "works" when it is robust, reliable and meets its specification, matters, and ignoring it risks disaster. But it is one-sided. Move "from a constructor's-eye view to a designer's-eye view, taking the system, the users, and the context all together as a starting point." "Good design produces an object that works for people in a context of values and needs, to produce quality results and a satisfying experience."

## Virtual worlds

"Software creates a world—a context in which a user of the software perceives, acts, and responds to experiences." A user who enters it and behaves by its rules and logic is an *inhabitant*. "the virtual world is not a mental construct of user or designer, it is an experience that seems real." Online games build their worlds from a definite purpose, a playing field and equipment, norms and values, rules for allowable and unallowable behavior, and strategies for winning or advancing. Social networks, Uber, Airbnb and eBay look like multi-player games in which your possibilities shift with others' choices. Spreadsheets, word processors and drawing programs also create worlds, each with its playing field, rules and strategies. Design a product by naming the world it creates and those elements of it.

## Quality: measured property or user assessment

In the 1970s software engineers set out to make quality measurable, "on the time-honored premise that we get more of what we measure." The ISO standard lists 20 factors: correctness, reliability, integrity, usability, efficiency, maintainability, testability, interoperability, flexibility, reusability, portability, clarity, modifiability, documentation, resilience, understandability, validity, functionality, generality and economy. Scoring high on all 20 is very hard. Security and safety, two of the five DRUSS objectives, are missing because no one knew how to measure them. In the app market, quality is an assessment by users rather than a property of the software: "Quality is in the eye of the beholder."

## The quality ladder

Six levels at which customers assess software quality and satisfaction. Each needs a higher level of CT skill; climbing the ladder, CT's sensibilities extend from formal requirements to customer concerns and futures.

| | Quality level | Skill level of CT |
|---|---|---|
| 4 | Software delights | Design software to anticipate evolution of customer practices and concerns after using the software |
| 3 | Software produces no negative consequences | Design software to avoid potential customer breakdowns |
| 2 | Software fits environment | Design software to align seamlessly with customer practices and social norms |
| 1 | Software fulfills all basic promises | Design software to meet all customer requirements via disciplined use of programming and software engineering CT |
| 0 | Some trust, begrudging use, cynical satisfaction | Design software with indifference toward the customer, modest CT discipline |
| −1 | No trust | Exploit the customer, little CT discipline |

- **−1, No trust.** The software is buggy, crashes systems, holds data for ransom or carries malware. Customers use it anyway, lured by fraudulent pitches, phishing, compromised websites or a craving for convenience. It is cobbled together without regard to DRUSS, often to exploit customer weaknesses.
- **0, Cynical satisfaction.** Customers trust some of the maker's claims. The software ships with bugs and vulnerabilities fixed only after complaints, and user forums fill with workarounds while the developers are nowhere to be seen. Developers tolerate a haphazard process under pressure to beat competitors to market, believing customers will tolerate bugs, and evading liability with no-responsibility licenses. The many bugs are also security vulnerabilities, and cynical customers have no loyalty.
- **1, Fulfills all basic promises.** The producer delivered exactly what was promised and agreed. This is basic integrity, the level the ISO standard addresses well, reached by standards-oriented developers through disciplined programming and software engineering CT.
- **2, Fits environment.** The design goes beyond stated requirements to align with existing customer practices, cultural sensibilities and social norms. The bank ATM implements familiar transactions, so customers use it at once without learning anything new. The customer feels better able to get work done.
- **3, No negative consequences.** The designer has examined the ways the software could produce breakdowns for customers and built in operating rules and checks against them, so customers meet no unforeseen disruptions or losses. The breakdowns avoided include vulnerability to hackers and malware, and to user mistakes with no way to cancel or back out to a previous good state. They also include interference with the organization's practices, wasted effort for marginal productivity gains, and frustration. The designer adds functions nobody asked for that spare future frustration: continuous backup that can retrieve any previous version and move a whole file system quickly, utilities that rebuild damaged files or directories, and internal management controls that let the designer keep modifying the software with the customer after installation. Anticipating breakdowns and offering repair after delivery are essential here. "Programming and software engineering CT do not orient software developers to this direction; design-oriented CT is required."
- **4, Delights.** The software goes well beyond expectations, producing new, unexpected, sometimes surprising positive effects; users promote it to others. The customer judges that the producer "understands the customer's world and contributes to the customer's well-being." Programming and software engineering CT cannot reach this level "because delight cannot be stated as formal requirements."
  - Delightful systems: UNIX (elegant, powerful operations with simple commands), the Apple Macintosh (an easy bitmapped desktop), DEC VAX VMS (amazingly stable, kept previous file versions for fast recovery), VisiCalc (the first automated spreadsheet), Lotus 1-2-3 (arbitrary formulas in cells, a new programming paradigm), Microsoft Word (easy professional formatting), and smartphones that safely download apps customizing the device to its user's taste and identity.
  - Delightful apps let customers do previously impossible things: direct access to an airline's or newspaper's content; Kindle's instant purchase and reading on any device; maps that aggregate phones' locations to detect congestion and reroute; World of Warcraft (as many as 10 million subscribers for its rich complexity, easy entry and detailed graphics); Uber's rides to your exact location within minutes.
  - Many of these failed ISO metrics such as portability, speed, efficiency or reliability, and customers stayed avid and loyal anyway.
  - "delight is ephemeral if based only on the software itself." Once customers master the new environment they expect more, and few would find the original UNIX or VisiCalc delightful today. Producers invest in knowing their customers and anticipating the next delight.

## Two ways of CT

- **The software engineering way** emphasizes correct implementation of clearly stated functional requirements. Its success measures are properties observable in the software or its usage data. It is especially needed for large systems that must perform reliably in safety-critical settings: air traffic control, nuclear plant control, Mars rovers.
- **The design way** emphasizes building virtual worlds that users inhabit to achieve a purpose meaningful to them. Its success measures are users' assessments of satisfaction and quality. It is especially needed for software that must fit customer communities, facilitate adoption and deliver great value.

"Design CT does not abandon software engineering CT; it listens for opportunities to include delightful functions customers have not yet asked for." Program correctness is essential, but it produces satisfaction only at level 1. Delight arises in the relationship between customer and developer. The delighted customer says the developer took the trouble to understand the customer's work and business, is available to help with problems and seize opportunities, may share risks on new ventures, and cares for the customer.

Design in this sense is "an ongoing interaction between designers and users, watching their reactions to prototype software, evaluating what works and what does not work, and adapting the software accordingly." That is broader than the "blueprint", "plan" or "setup of an experiment" views of early programming. It combines sensibilities to the moods and histories of communities with deep knowledge of existing technologies and components: "Design requires understanding humans in their communities as much as it requires understanding technology."
