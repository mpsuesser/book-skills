# Demos and reviews

Apple used demos to "highlight the potential, explore the concepts, show the progress, prompt the discussion, and drive the decisions." Every major iPhone feature started as a demo. This file covers making one, presenting one, and judging one.

## Making a demo: Richard's model

When Richard Williamson joined the Safari project, Don Melton and the author had spent six weeks on Mozilla and had no working code. Two days later Richard had the open source Konqueror browser loading pages on a Mac. That is about a 30x gap (two person-days against twelve person-weeks). For early-stage work with a small team still hunting for ideas, a 10x productivity gap "is a conservative upper limit on the possible." Brooks's limit (a task that cannot be partitioned gains nothing from more effort) governs large projects, where coordination overhead swamps individuals.

The gap was a matter of thinking, not just coding skill. Richard's shim (a translation layer between the Linux browser and the Mac) was "one last link in a chain of inspiration, intuition, reasoning, and estimation"; it was "a consequence of his overall plan." His sequence:

1. Hear the analysis done so far, and discard the effort unlikely to bear fruit. Skip any deference to seniority.
2. Resolve to produce a result on the shortest possible schedule.
3. Choose a starting point with genuine promise, one that could serve as the long-term basis.
4. Make "the closest possible approximation" of the real thing feasible on that schedule. For a browser that meant three features (loading pages, clicking links, going back), enough to be a compelling proof of concept.
5. Take shortcuts, and let them define **nongoals**: no perfect font rendering, no native graphics integration, no trimming down the surrounding code. Judge that these won't detract from seeing the core thing work.
6. Draw the strands into a single demo that shows the potential.
7. Only then work the technical details, building whatever one piece still stands between you and the plan.

Disclose the caveats when you show it. Unease about shortcuts "would melt away in the minds of the demo viewer" once they see the core thing working.

The model as the author absorbed it: "Look for ways to make quick progress. Watch for project stalls that might indicate a lack of potential. Cut corners to skip unnecessary effort. Remove distractions to focus attention where it needs to be. Start approximating your end goal as soon as possible. Maximize the impact of your most difficult effort. Combine inspiration, decisiveness, and craft to make demos."

## The Hollywood backlot and the ring

A backlot convinces only when "we must see the correct amount of replicated reality onscreen." In *Singin' in the Rain*, the hat shop Gene Kelly dances past can be a flat with nothing behind it. The lamppost he leaps onto has to bear his weight, "because the choreography called for it." Demos are choreographed the same way, so it is clear what must be included and what can be left out. Supporting elements are built "at the correct level of detail so they contribute to the whole rather than detract from the vision."

The procedure:

1. Think about the intended audience and decide which features to include.
2. Draw a conceptual ring around the key details, using "a thick imaginary marker." Build what is inside at the highest fidelity (the lamppost).
3. Leave less important details outside the ring. Pay them as little attention as possible, and omit them if you can (the inside of the hat shop).
4. Take extra care at the boundary. Some elements set the scene and get the audience to suspend disbelief. For an early app's preferences screen, a screenshot from another app's preferences can stand in for a working interface, like a few hats in the shop window.

Sort features as **important / passable / ignorable**. Richard's browser had loading, links and back (important). Its fonts were jaggy but legible (passable: no more effort spent). Keyboard shortcuts and an app icon were ignorable. The point is "to maximize impact, minimize distractions, and fit the work schedule." The illusion of a real product is essential "to maintain the vision" and so that colleagues "can begin responding and giving feedback as if the demo was the product." Demos, like backlot scenes, belong to a larger narrative, and each one advances the story.

Fidelity matters to the medium. Bas Ording's Adobe Director demos were pictures and animation, quick and good for showing how something would feel, but with "no direct engineering path" to a product. The author's iPad keyboard demo was real code that worked in any app. Paper prototypes were never used on the iPhone: their low fidelity made it too hard to judge a multitouch interaction. The one meaningful paper demo was Imran Chaudhri sliding a sheet of paper under his finger to show how direct manipulation should feel.

## Concrete and specific, and the brainstorm trap

Making demos is hard. It means committing time to an idea you aren't sure of, exposing it to sharp critics, and knowing "most demos—almost all of them—fail in the absolute, dead-end sense of the word." That makes a coffee break or a whiteboard gab session tempting. The Purple team "rarely had brainstorming sessions." When whiteboard planning was needed (the Safari porting strategy), they sketched and decided as fast as they could. "Whiteboard discussions feel like work, but often they're not, since it's too difficult to talk productively about ideas in the abstract."

When an open field has no existing answers, everyone with a concept makes a demo of it. People try each other's demos, say what they like and don't, and suggest improvements. That leads to more demos: a "virtuous collaborative cycle." Programmers and designers were in and out of each other's offices all the time, and everyone fielded questions on their own area.

## Presenting a demo

- **Be minimal.** In Diplomacy, the room where Jobs saw demos, Scott Forstall's introduction used just enough words to say what was next on the agenda, where to look, and who was presenting. The presenter added "the minimum number of words necessary to direct Steve's attention further, so he knew exactly what to look at." The author's whole pitch: "Right, there are two designs. One has more keys, like a laptop keyboard, and the other has bigger keys, like a scaled-up iPhone. We're thinking of offering both. Try the zoom key to switch between them."
- **Tell the story through the software.** Bas's zoom animation carried the iPad keyboard demo through its pre-Steve review: one keyboard "was becoming the other."
- **Have an opinion.** Jobs asked, "We only need one of these, right?" and then, "Which one do you think we should use?" The question was a test of whether you could make the work better. Answer from experience: the author had been using both layouts for days, so he could say why he preferred the bigger keys. Passing such tests is "the difference between writing software and influencing what software got written." Admission to the top room came from "your ability to make the products better," not your place on the org chart.
- **Know it inside and out.** After Scott Forstall typed his name on the derby keyboard, his questions came in rapid succession (why multiple letters per key, how the software knew the word, how the dictionary was built). Interviews with him felt like the same fusillade.
- **Read a cold reaction as customer data.** Phil Schiller spent two minutes on the keyboard and was "confused rather than convinced." He had no emotional connection to the work and "expected the software to win him over," just like a prospective customer seeing the product fresh.
- **Rehearse like Jobs.** Jobs began rehearsing a keynote three weeks to a month ahead and built it up day by day. "He practiced. A lot." On stage he went fully into his keynote persona. To get feedback he stepped out of character, lowered his voice and asked front-row executives about a phrase or the flow. Then he paused and went back into character. When a line didn't run right, he backed up and redid it, three or four times, "like takes on a movie set." He did full dress rehearsals twice a day on the two days before the show.

## Running a review as the decider

- **Every review has a decider**, with sole authority to approve and to say what happens next. Peers decide on their own portions and whether a refinement is worth the hours. A team's manager decides at team reviews, and so on up. During busy periods, extra review layers formed below Scott Forstall (Henri Lamiraux's reviews for all of iOS engineering).
- **Judge two things before passing work up:** will the design pass muster, and can the team build it "in a high-performance, bug-free manner given the remaining time"? Showing work at the top "carried the promise that we could deliver," so most demos went through several rounds over weeks before they reached Jobs.
- **Gatekeep on quality.** Pass work up only when it is good enough. A weak demo excused by the hours spent on it, or one Thoroughbred among old nags, gets seen through. A gatekeeper is judged partly by whom they bring into the room.
- **Push for simpler, then let the cascade run.** Jobs found the two-keyboard demo "unnecessarily complicated" and unpacked it. Dropping one keyboard also removed the zoom animation, the zoom button, and the unanswerable question of which keyboard to remember for which app. Stripping nonessential features makes products easier to learn from the start and to use over time. Nobody will be standing over a new user's shoulder explaining every feature, so software should speak for itself. Picture a busy person (the book's example is a mother with a sick son at home, a report due and one more email to send) rather than an enthusiast.
- **Decide quickly, and close the loop.** Once a verdict is given, arguing would mean "speaking up in favor of adding back complexity." Good reviewers have "a well-tuned sense of when it was best to say nothing." Seeing good work cut "was part of the job." A productive meeting is a pattern to repeat: Jobs settled the iPad keyboard in four sentences.
- **Feedback is an open forum.** At Forstall's demo tours, held once or twice a week, "everyone spoke up." Good demos and poor ones drew the same stream of comment. There was "never any finger-pointing," only the expectation of progress next time. Feedback is specific ("Add more space between these two elements," "Replace the green in this graphic with blue," "None of this is working. Show me more options next time"), and the cycle repeats until final approval.
- **Surrender your own idea to one that works.** Jobs walked into the iPad multitasking demo with his own "shoo-away" flick for returning to the home screen. When the five-finger scrunch worked, he accepted it. He also loved a rubbery bounce animation Forstall disliked, because it said "no more apps this way" at a glance: "This animation … this is Apple."
- **Keep the room small.** Meetings and teams stayed small "to maintain efficiency and to reinforce the principle of doing the most with the least." Each Diplomacy regular had earned the place "by consistently providing feedback that helped make the products better."
