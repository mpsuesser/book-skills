# Craft, diligence and the people doing the work

How ideas become products once a demo has shown the potential: rules that connect words to actions, measurement, the grind, hard problems, ownership, convergence, and the small teams that carry the culture.

## One simple rule: connect words to actions

Jobs judged Safari on one thing, speed, "much faster than Microsoft Internet Explorer." The goal gave the team a purpose and became "our definition for greatness." Don Melton turned it into a rule and a means:

- **The means: the Page Load Test (PLT).** An automated tool loaded a suite of forty pages, chosen "as punishing as possible" to cover every important attribute of loading and rendering (text-heavy pages, graphics-heavy pages, the most visited sites). It timed each page until it was fully loaded and rendered, and averaged the results into one number.
- **The rule: "No more code changes without running the PLT."** Reject any change that makes the browser slower, and only two things can happen: it stays the same speed or gets faster. The browser "would become faster by never getting slower." No exceptions. The PLT added a quantitative, independent check to the qualitative code review (summary of the change, a teammate's review, rounds of re-review, commit only after passing). "Correctness and speed now went hand in hand."
- **Use it daily**, even hourly, including to compare two equivalent versions of the same code. Happy accidents happen: removing lingering FIXMEs sped things up, because "higher-quality code often performs faster."

Clear words that drive specific actions are what separate this from slogans. Postgame clichés like "taking it one game at a time" explain little and predict nothing. Vince Lombardi took over a Packers team that had won one game of twelve. He promised to "relentlessly chase perfection" so as to "catch excellence," then named one thing to perfect: the Power Sweep, a single running play, run "again, and again, and again." Opponents knew it was coming and couldn't stop it. The Packers won five championships in seven years. "Communicating a well-articulated vision" is the starting point. The harder part is completing the circuit, idea to plan to high-standard execution, without bogging down, changing direction, or failing. Safari's chain ran "inspiration to proposal to plan to process to product," so when Jobs told the world Safari loaded pages three times faster, it was a description of what the team had done, not marketing cherry-picking.

## Optimization: measure, then pay for slowdowns

Knuth: "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil." The author explains it with kitchen instructions. "Take a jar of mustard out of my refrigerator" and "Go to the supermarket to buy a jar of mustard" are the same length but take very different times, because cost hides in dependencies. You can't tell how fast code runs just by looking at it. Adding "Use as few armloads as possible" to a fridge-emptying task invites bugs (dropped jars), hides the real goal, and may not even be faster.

- **The PLT is the 3 percent escape hatch.** Measurement shows exactly when and where slowness enters, so you optimize "when we knew what we were doing, in direct response to measuring," at the moment the slowness is found.
- **Spread optimization through the project.** The usual practice of features first and performance later fails when the schedule slips and performance work gets dropped.
- **Look sideways.** Fetch a box from the garage so everything comes out of the fridge in one trip.
- **Trading scheme.** When an essential feature can't avoid a slowdown (keeping the previous page ready for the Back button slowed every load), find speedups elsewhere to "pay for" it. Target code you know well and that is stable, and tune it until the net impact is nil or positive.

## Inspiration and perspiration

Edison: "one per cent inspiration and ninety-nine per cent perspiration." The author tallied the Safari ratio as the **Browser Project Edison Ratio**:

| Phase | Calculation | Hours |
|---|---|---|
| Inspiration: nothing to Richard's demo | 1 engineer × 8 hours/day × 2 days | 16 |
| Perspiration: Richard's demo to the Black Slab | 3 engineers × 8 hours/day × 5 days/week × 10 weeks | 1200 |
| Ratio | | 1:75 |

That was 1:75 at a first milestone, a year before the product was finished, so for finished work Edison "grossly underestimated." "Ideas are nothing without the hard work to make them real." Without the grind that followed, Richard's demo would have been "little more than a programming curiosity." The 99 percent has a shape: "I make trial after trial until it comes." Edison tested bamboo variety after variety and crossed items off a list. That differs from trudging across a desert hoping the next dune hides an oasis. Define the work so each trial is an item crossed off. "Hard work is hard. Inspiration does not pay off without diligence."

## Porting and bootstrapping a large codebase

The Safari port of Konqueror (about 120,000 lines in 300 files) went like this:

1. **Size it.** Count lines as a rough measure of the porting effort, since every line may need work. Konqueror was under a tenth of Mozilla's roughly million and a half lines. Mozilla's snap-together component scheme demanded reams of boilerplate, "the Hemingway to Mozilla's Faulkner." Quick early successes give the "confidence to commit."
2. **Uncut the demo's corners.** Separate the needed code from its surroundings and get it building natively.
3. **Honor the license.** Keep the borrowed code separate, use it by reference, and publish your changes to it (the LGPL terms). Neither obsess over licenses nor ignore them.
4. **Fix every broken cross-reference.** Point each one at an existing local equivalent (colors, fonts) or write a new one (bookmarks). Expect changes on both sides.
5. **Annotate with FIXMEs.** Wherever you have doubts while editing, leave a FIXME and keep the discipline of always doing so. Each one is a to-do item. Make the code generate a FIXME report at runtime, keep it beside the app window, and work the loop: "Try to load a page, inspect the report, change the source code to patch up the most glaring problem the FIXMEs seemed to show, then try again." Entries go from "not implemented" to "partially implemented" to removed.
6. **Estimate and grind.** The estimate was more than a month and less than two, and two months was about right. The same people who conceived the project did the tedious work. Apple didn't hand grunt work to juniors and didn't separate research from implementation. Every hour of tedium "was a contribution" and a chance to learn the adopted code.
7. **Watch for the first visible result.** Until then progress is measured only indirectly (files built, references fixed, FIXMEs retired). The first page render (the **Black Slab**) ends weeks without visible evidence, and after that improvement is visible almost daily. Treat it as a beginning, not an end.

Don't write a fifty-step document to coax a behemoth into building with no plan beyond that (*Building the Lizard*). It was never repeated.

## Hard problems

- **When software behavior is mysterious, get more organized.** The author's insertion-point **heisenbugs** (bugs that don't recur when you retrace your steps) survived months of special cases, pattern analysis and nights and weekends. Darin Adler and Trey Matteson found the root in half an hour: "too much time thinking about data and not enough thinking about the visuals." The code had no single authority for an operation as the user sees it ("Move the insertion point one position to the right starting from where it is now"), only loosely coordinated pieces, like "a pad of sticky notes" for cake orders. The fix: gather the scattered special cases into one class (VisiblePosition) that works like a well-designed **order form**, with a specific space for every piece of information, and explicit steps that guarantee the visible outcome (the insertion point never disappears, just as a bakery never has a finished cake with no record of who ordered it).
- **Learn the unwritten rules by experiment.** No handbook explains word processor behavior. A simple rule says the insertion point stops blinking while you type. A complicated one says a line end can hold infinite spaces, which keeps left-aligned text from going ragged. Poke existing tools until you know "the letter and spirit" of every rule.
- **Skip what you can't solve in favor of what you can.** Lacking the math for Markov chains or graph matching, the author found a simple stand-in (summed "nudges," a Manhattan distance) that did the job.
- **Ask for help, and make it work socially.** When stuck, lay everything out: diagrams, every case you can't handle, how the bugs come and go. Say plainly that you are stuck. Being desperately stuck made the author open rather than defensive. Monotone droning, crossed arms, a helper attending only because a manager asked, or a grudge would each have sunk the meeting. Then act "directly and unequivocally" on the advice, and come back with demos showing their advice fixing specific bugs. The helpers became invested: "It was now *our* project." "People matter more than programming."

## Ownership: signing up and the DRI

Leaders offer project opportunities, and "someone had to 'sign up' for the work and get it done" (Tracy Kidder's term from *The Soul of a New Machine*). Apple's term was **DRI**, directly responsible individual, "the person with their butt on the line." Once you have signed up, "unsigning up" isn't done. Take roles for the right reasons. The author took a management job to make up for a missed promotion and was miserable within months: meetings and politics replaced the coding that made him feel productive. Leaders keep good people by finding what makes them tick. Scott Forstall saw the author liked "projects much more than politics" and gave him projects. Notice what the organization values: marketing's "we don't market sync" meant sync was something Apple needed to do, not something it wanted to do. When something works, "go do something else wonderful, not dwell on it for too long. Just figure out what's next" (Jobs). The advice works after a failure too.

## Convergence

**Convergence** is "the final phase of making an Apple product, after the features had been locked down and the programming and design teams spent the last three or four months fixing bugs and polishing details." It is driven by two opposing forces, an unmovable ship date and an ever-changing bug count.

- Track everything in one flexible bug tracker (Radar), holding defects, to-dos, enhancement requests, features with subfeatures, and executive priorities.
- Send a daily graph of open bugs against dates, ending at the ship date. Spikes after big demos aren't worrying, since demo bugs fix quickly. A stubborn flat line over many days is real trouble: incoming bugs match the fix rate and convergence has stalled.
- Ship at Netscape's "zarro boogs": finished on the ship date, never truly defect-free.
- Know its limits. "Bug squashing might help to make a decent product, but it's not the secret for making a great one." In a sense the team was always converging, toward the next demo. They "habitually converged on demos, then we allowed demo feedback to cause a fresh divergence," which they immediately sought to close.
- Pace yourself. Regular hours made the stress bearable. The team kept "the rate of our progress above the level of our stress," helped by having few roadblocks that wouldn't give way to a good idea.

## Small teams and culture

Ten people edited Safari's code before its beta. Twenty-five are named inventors on the iPhone's '949 patent. Leaders wanted high-quality results and wanted to deal directly with the people doing the work, and that set a limit on team size. Small teams brought personal empowerment, cohesion, and communication paths worn "like ruts in a road," with "a minimum of dithering and delay." Habitual, rich interactions (a daily team lunch where everyone waits to take the first bite together) build a culture, and "the culture we created is inseparable from the products we created." When the people change, the culture changes. Managers can buffer their teams: Henri Lamiraux edited the expletives out of executives' bug reports and projected calm, knowing pressure wouldn't make a fix come faster but that the engineer would drop everything for it. The first lesson Apple taught the author: results can come far faster than you think.

Some contrasts from the book:

- Eazel failed largely by "failing to conceive of our software as a single product instead of as a set of separate projects." It never tried its software in integrated form until days before running out of money.
- Free software is a candy store of reusable code. "Free as in freedom" (Stallman) differs from "free as in beer" (Netscape's open source bet); Apple management's position was "closed source as in money."
- New systems don't follow old ones' paths. The first iPhone shipped without cut, copy and paste, a feature of the first Mac in 1984, and went nearly two years without it.
- A name should fit the genre without being "a slavish knock-off." Safari had the world-traveler feel of Navigator, Explorer and Konqueror, and "it was fresh."

The author's advice to anyone starting out: "Get busy. Decide what it means to do great work, and then try to make it happen."
