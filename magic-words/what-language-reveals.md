# What language reveals

The second half of language's **dual role**: words don't only influence the people who receive them; they also reflect and reveal the people who produce them. "Language is like a fingerprint." Because similar people use language similarly, and because people leak what they think and will do even when they aren't communicating strategically, a text can be read for who wrote it, what they are like, and what they will do. Aggregated across many texts, language reveals the biases and beliefs of a whole society.

Use this file when the task is to *read* text: infer authorship or traits, predict behavior, audit a body of writing for bias, or apply the book's text-analysis methods.

## Read style words, not just content

Content words (nouns, verbs, adjectives) carry what is said; **style words** (pronouns, articles, prepositions, auxiliary verbs) carry how it is said. Readers skip style words, but they reveal personality, preferences, intelligence and whether someone is lying. Language predicts age, political affiliation, personality (introverts vs extroverts), deception, college performance (from admissions essays), postpartum depression (from Facebook posts), and an approaching romantic breakup (from social posts unrelated to the relationship).

## Linguistic signatures (authorship)

*Double Falsehood* (1727) was claimed by Lewis Theobald to be a restored Shakespeare play. In 2015, researchers settled the question without reading the play:
1. Collect every work known to be by each candidate author.
2. Count, for each work, the words falling in hundreds of categories (pronouns such as "I" and "you", emotion words, long vs short words).
3. Across many works per author, build each author's **linguistic signature**.
4. Compare the disputed text with each signature.

Result: the first three acts were Shakespeare's, the last couple most likely John Fletcher's, with traces of Theobald, who was known for a heavy editorial hand. Signatures differed: Shakespeare used relatively few emotion words, Theobald many, plus lots of prepositions ("of", "in", "from") and articles ("the", "an"); Fletcher used many auxiliary verbs and adverbs.

## Predicting behavior: loan default

Across more than 120,000 peer-to-peer loan requests, the free-text description predicted default on top of financial and demographic data. Adding it would raise lenders' return on investment by almost 6 percent, and the text alone was nearly as predictive as the financial and demographic information.

| Repayers wrote about | Defaulters wrote about |
|---|---|
| Their financial situation ("interest", "tax") | Financial hardship ("payday loan", "refinance") |
| Improving financial ability ("graduate", "promote") | General hardship ("stress", "divorce") |
| Financial literacy ("reinvest", "minimum payment") | Explaining their situation ("explain why") |
| Employment and school, interest-rate reductions, monthly payments | Their work ethic ("hard work", "worker") |
| The longer term (next year) | The near term (next month) |
| Themselves ("I'd", "I'll", "I'm") | Others ("God", "he", "mother"); "we" rather than "I" |
| | Pleas ("need help", "please help"); religion |

Using "reinvest" made a borrower almost 5 times more likely to repay in full; using "God" made them almost 2 times more likely to default. Defaulters' writing resembled the style of liars and extroverts, though there was no evidence of deliberate deception. Of two otherwise identical requests for $2,000 to fix a roof, the one that seems more compelling ("I am a hardworking person, married for 25 years, and have two wonderful boys. Please let me explain why I need help... Thank you, God bless you, and I promise to pay you back.") came from a borrower around 8 times more likely to default than the plain one ("...the roof is now leaking, and I need to borrow $2,000 to cover the cost of the repair. I pay all bills (e.g., car loans, cable, utilities) on time."). Similar signals elsewhere: online shoppers who type their name and shipping address all in lowercase are more than twice as likely not to pay; those whose email address includes their name are less likely to default.

Language predicts membership too: on a beer-rating site, users who adopted fewer community conventions, or adapted for a shorter time, were more likely to leave, and their first few reviews predicted how long they would stay. In company email, employees about to quit had converged on the firm's style early and then started to diverge.

## Reading bias in a body of text

Individual word choices look innocent; the same pattern repeated across thousands of texts shows entrenched ways of seeing groups.

**Warmth versus competence.** "Mike is really capable and experienced, and Susan is superfriendly and helpful." Both are praise, but men tend to be described by competence (smart, strategic, successful) and women by warmth (friendly, caring, supportive). Since hiring and promotion, especially for leadership, depend on perceived competence, warmth-only praise is a disadvantage. In more than a quarter of a million songs from 1965 to 2018, lyrics in the 1970s and early 1980s were clearly less likely to call women intelligent, clever, ambitious or brave. They became more equitable through the late 1980s and early 1990s, then grew more biased again from the late 1990s. The shifts were driven by male musicians; female musicians described men and women similarly throughout. Hip-hop alone does not explain it: country, R&B and dance shifted too. Elsewhere: animals in children's books are three times more likely to be male; three-quarters of people in textbooks are male; 30 percent of speaking film characters are women; 11 percent of business-school case protagonists are female; newspapers give men occupations like captain or boss and women homemaker or receptionist; female tennis players are twice as likely to be asked questions unrelated to tennis.

**Respect in policing.** Body-camera footage of thousands of routine traffic stops in Oakland showed officers' language toward Black drivers was less polite, less friendly and less respectful. With White drivers, officers more often used formal titles ("sir", "ma'am"), the last name, reassurance ("It's okay", "Don't worry", "No problem"), agency ("You can...", "You could..."), safety talk and positive words. With Black drivers they more often used informal titles ("Dude", "Bud", "Champ"), questions, and orders to keep hands on the wheel. The gap held after controlling for age, gender, location, offense, officer race and searches, and across hundreds of officers of every race; officers' words alone predicted the driver's race about two-thirds of the time. Officers' tone was also more negative, and hearing it reduced trust in the department. Because the pattern is mostly unintentional and widespread rather than a few bad apples, language analysis is a way to locate where treatment differs so it can be improved.

## Methods for analyzing text

- **Dictionary word counts.** Count words in predefined categories (emotion, pronouns, environmental terms) as LIWC (Linguistic Inquiry and Word Count) does. Consistent, tireless and scalable where human coders drift.
- **Classification.** Train an algorithm on labeled examples (this is a cow, this isn't) so it can label new texts: hate speech, newspaper section, author.
- **Topic modeling.** Infer themes from word co-occurrence without specifying them in advance, the way a new student infers cliques from who hangs out together. Texts mix several topics in different strengths. Song-lyric topics included fiery love (burn, feel, fire, heart, love), uncertain love (ain't, can't, love, need, never), body movement, dance moves, girls and cars, street cred, family, positivity, spiritual, and anger and violence; comparing a song's topics with its genre's average measures its **atypicality**.
- **Word embeddings.** "You shall know a word by the company it keeps" (J. R. Firth). Words are placed in a space of hundreds of dimensions so that related words sit close together, and distance measures similarity (grapefruit is closer to orange than to kiwi, and far from tiger). Applied to sentences or passages, the distance between consecutive chunks measures a story's **speed**; the space a whole story spans measures its **volume**; how directly it moves measures its **circuitousness**.
- **Emotional trajectory.** Split a script into chunks of a few hundred words, average the positivity of each chunk's words ("laughter", "love" vs "funeral", "cruel"), and plot the story's shape. Single words mislead ("kill" appears when the hero kills the villain and when the villain kills a friend), but in aggregate the scores track human judgment.

## Applications for organizations

- **Customer analytics.** Route complaints by their words; predict who will cancel and intervene; target ads from social-media language; **look-alike targeting** to find prospects similar to current customers.
- **Social listening.** Comb social media for how people talk about a product (a hotel learns guests complain about the beds; a drug maker spots emerging side effects); use it, and search data, for new-product development.
- **Legal cases.** Replace dueling expert opinions with aggregate evidence. For a greenwashing claim, count environmental words across all of a brand's ads and posts and how prevalent they are over time and place. Better, train a classifier on brands known to pitch themselves as eco-friendly (Seventh Generation, Tide purclean) and known not to (Gain, regular Tide), then score the accused brand. The same approach can test whether alcohol advertising targets youth, or whether a politician talks like a Democrat or a Republican.
- **Time travel.** Surveys today can't show how people reacted to an ad two years ago. Posts and reviews from before and after the ad ran can, including whether consumers mentioned the claimed attribute (a laptop "light as a feather"), and press coverage shows whether media picked the claim up. Digitized language works as "a new type of archaeology".

Accessible tools: https://liwc.app/ (scores texts on psychological dimensions) and http://textanalyzer.org/ (scores other dimensions, including concreteness, and extracts basic topics).
