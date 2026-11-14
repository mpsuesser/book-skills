# Taste, empathy and the intersection

The design judgments behind creative selection: what to select for. Apple "always had a characteristic sense of what to select for," and that sense supplies the selection pressure from demo to demo.

## Taste

The author's working definition (he calls it a carpenter's hammer, not Kant): taste is "*developing a refined sense of judgment and finding the balance that produces a pleasing and integrated whole.*" Philosophy is the wrong tool for practical decisions; a maker turns "less to the theoretical and more to the applied." It has three parts, each seen through empathy.

1. **Developing judgment: the refined-like response.** A knee-jerk like or dislike (ripe strawberries) is fine for breakfast, but in creative work, "persist too long in making choices without justifying them, and an entire creative effort might wander aimlessly. The results might be the sum of wishy-washy half decisions." The **refined-like response** means "evaluating in an active way and finding the self-confidence to form opinions with your gut you can also justify with your head." It needn't be stuffy, "but it does need to be detailed and justifiable." Local examples: "I like this animation since it helps to direct the user's attention appropriately"; "I don't like this color scheme because it fails to provide adequate contrast between these dissimilar elements." Building trust in your own responses takes time, practice and a measuring stick: study great work from the past and decide what you like about it. That catalog of responses later finds its way into present work.
2. **Finding balance.** Local judgments, once built into a system, no longer stand alone. "The small-scale justifications must contribute to a scheme larger than themselves." Multi-letter keys traded away keyboard familiarity for easier tapping. Greg Christie judged that the big keys "weren't contributing as much as they were detracting," so the design was off balance and unlikable.
3. **A pleasing and integrated whole.** The test is not popularity. It is whether people use the thing without thinking about it, whether it can "melt away" and leave "a space for what people really care about." "A properly judged mixture of taste and empathy is the secret formula for making products that are intuitive, easy to use, and easy to live with."

Beauty is left out on purpose: "Design is how it works." If one sentence about making products were to survive a cataclysm (Feynman's test for the atomic hypothesis), it would be that one. The appearance of a product should tell you what it is and how to use it. QWERTY "unequivocally says 'keyboard.'" Familiar conventions are cultural inheritance. QWERTY used decades of a typist's muscle memory, and no other layout could make "better use of the knowledge I could expect him to have." The legend that QWERTY was designed to slow typists "focuses on the wrong thing": it solved key jams, so it actually helped people type faster. Ditching a familiar convention assumes the convention is bad. Check that assumption first.

## Empathy

Empathy runs through both the first impression and long use. People react to how a thing looks before they use it, and its look communicates what it is. Living on the in-progress product exposes "breakdowns in empathy, where the person felt at odds with software attempting to provide assistance." Since you cannot try everything, taste whittles down the unbounded possibilities.

- **Prevent negative experiences.** "Designing an excellent user experience was as much about preventing negative experiences as facilitating positive ones. It couldn't be an even trade-off either. Great products make people happy almost all the time and do the opposite rarely, if at all." The keyboard had to deliver "Arrr!" on Talk Like a Pirate Day, not make people give up with "Argh!" A single memorable failure can define a product: the Newton's handwriting recognition "drowns out all other memories of the product."
- **Design for the range of people.** Scott Forstall's precise, spidery fingers and Greg Christie's shaky hands bracketed the population, and Greg's frustrated sigh at a too-small target was right. Products must "come to the user."
- **Give a result for the intent.** If a typist taps inside the keyboard, "the goal was to type, so I always gave a result" (the **Can't Miss** rule: a tap between keys activates the nearest key). Give people "what they meant rather than what they did."

## Working at the intersection

Working at the intersection is not honing an icon, animation or sound to an ideal in isolation. "Liberal arts elements and state-of-the-art technology must combine." The goal is "comfortable technology and computer-enabled liberal arts." Comfort levels, smoothness and reduced mental load are the "ergonomic, perceptual, and psychological effects" to aim for, and "honing and tuning technology to a high level became the means to achieve people-centered results." Two habits put it into practice. Make technology-to-people links: Scott Forstall heard that the touch system could now tell a quick swipe from a slow pan and saw swipe-to-delete on an email in a list. Accept the hard path when it makes the product easier: Greg Christie often saw that "some difficult development path was the best way to make our products easier to use." Keep a wide view while making: "you have to make sure each individual demo feedback and response cycle eventually adds up to something more."

## Heuristics and algorithms

Both are procedures (take input, apply an operation, produce output), "two sides of the same coin," with different purposes. They are "the left and right sides of our collective product development brain."

- **Algorithms are objective.** They "produce quantifiable results, where progress is defined by measurements moving in a predetermined direction." Page load time should go down. A space typed mid-line must insert a space and advance the insertion point; otherwise it is a bug.
- **Heuristics are subjective.** They have values (an animation duration, an RGB color) but no "arrow of improvement" that always points the same way. How fast should a flicked list glide to a stop? How long should an app icon take to zoom to full screen (say 0.35 seconds)? How far must a finger drag to count as a swipe (say 30 pixels)? How far should a pinch zoom (say 4x)? "The number was never the point." The values are "sensible defaults, or pleasing effects, or a way to give people what they meant rather than what they did." "Heuristic" shares its root with *eureka*, "to find." Good heuristics come "only after patient searches," and final decisions come "only with judgment and time."
- **How to find a heuristic:** sit down with a designer to make preliminary choices in a demo, review them in larger groups, then have the whole team live on the results over time.
- **Choose the right tool for the question.** "It's crucial to make the right call about whether to use an algorithm or a heuristic." A color is a heuristic. Apple "never considered the notion of an algorithmically correct color." At the same time, don't be "overly touchy-feely about everything": optimized algorithms were a large part of the work.
- **Heuristics temper algorithms.** A closest-match algorithm will always find some word. "oooorr" geometrically matches "polite," but people don't accept that the way they accept "rhe" to "the." The aim is "to give you the word you meant, given what you did, not unconditionally conform your typing to the dictionary." Where to make the algorithm back off can be found "only by asking people," and then you pick a cut-off.
- **Chain them.** Swiping in Photos runs heuristic, algorithm, algorithm, heuristic: a judgment whether the swipe goes to the next photo, then geometric centering, then a starting speed from your finger's speed, then an ease to a stop on a designed timing. So "you can't 'engineer' a product in one phase and then slap on 'look and feel' in another." The work is like a jigsaw puzzle whose final picture is unknown and whose pieces keep changing shape. "No single A/B test was possible," and the full implications only show by living on the product over time.

## Against A/B testing for taste

Douglas Bowman left Google because, without a design leader, a company "eventually runs out of reasons for design decisions." Data becomes "a crutch," as when a team tested 41 shades of blue. The author's critique: in an A/B test the choices are already laid out, and the range between best and worst is small. Its opportunity cost is the time not spent dreaming up a design people might like "two, or three, or ten times more." It cannot produce a pleasing and integrated whole; it has no refined-like responses and no balancing. "Google factored out taste." Apple staged no A/B tests for any iPhone software. "When it came to choosing a color, we picked one," using taste plus knowledge of color-perception accessibility, and moved on. Small details got quick choices that were always open to reconsideration. Bigger questions got more time, "but never too much."

## Lightening the load

Working memory has hard limits: about seven items, per George Miller's 1956 paper "The Magical Number Seven, Plus or Minus Two." Past that we must chunk ("groups of items that go together"; 984–313–552 is easier than 847620475), or we overload and make more errors and worse judgments. New or tricky technology loads the mind the same way. "Designers must lighten the load on people trying to use the things they make. Even small simplifications make a difference," and "it's almost always possible to streamline tasks." What to drop isn't always obvious. You are looking for the removal that triggers "a genuine less-is-more response."

- **Count the places to look.** Six weeks before the iPhone announcement, Forstall had the keyboard's suggestion bar removed. The typist already watched two places, the insertion point and their thumbs. The bar was a third, "one too many." Autocorrections moved to a bubble right under the word. Removing the bar ended a source of pixel flashing, freed screen space, and produced "a small but statistically significant *increase* in typing speed." Cutting a year of the author's work didn't make him grumpy: "we edited for less."
- **Remove the choice.** Jobs's "We only need one of these" removed a decision from every iPad typist's mind.

## Direct manipulation and smoothness

**Direct manipulation** means "giving software objects some of the same attributes and behaviors as physical objects, enabling people to interact with digital bits as if they were real-world items." Ben Shneiderman invented it in 1982. The Mac's mouse popularized it, against command lines like `mv paper.txt folder` ("Yech!"), and it set the Apple tradition of using new technology to solve age-old interaction problems. Multitouch took it a level further: see it, touch it. Imran Chaudhri's standard: pixels stay pinned under the finger like a sheet of paper slid around a desk. "Since the real sheet of paper never paused or stuttered ... why should the pixels?" Then "you would forget about the technology and focus on the experiences."

## Interaction details from the iPhone

Each is a heuristic tuned until the product fit the person:

- **Tap-target size.** The test was Scott Herz's game: tap boxes of random size at random places, about twenty per round, then see your score. Everyone played it, and within days the data showed that a **57-pixel-square** target could go anywhere on screen and be tapped with near 100 percent accuracy. Original home-screen icons used that size. A fun game is a good way to gather usability data.
- **Warp.** A curved fingertip actually meets the glass lower than people perceive, so touch points are shifted upward and targeting feels right on.
- **Charged buttons.** The Back button's active area is larger than its visual area.
- **Child's Play.** Slide-to-unlock prevented accidental activation in a pocket, and it explained itself so well that Imran's three-year-old daughter unlocked a phone unprompted.
- **Tap spiral.** On tiny full-page web views, a tap searched outward from the touch point and activated the nearest link.
- **Backchannel.** Key pop-ups showed what the keyboard saw, like the nods and "uh-huh"s of a listener, so the typist knew it was following along.
- **Escape hatch and app model.** The home button was an always-present way out for people who got lost. Animations explained the app model: launching zoomed in and out, and going deeper slid side to side.
- **Sound.** The key click was a pencil struck on a desk edge, processed into two variants, *tick* and *tock*. Jobs chose *tock*.
- **Elastic edge.** When there were no more apps to swipe to, the app stretched like rubber and snapped back, telling you so at a glance.

Patent language for this work (the '949 "heuristics" patent) fails to convey the good feelings put in. The feelings come from the tuned values, not the mechanism.
