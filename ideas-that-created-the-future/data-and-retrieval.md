# Data and retrieval

Papers 32 and 35: Codd's relational model and Spärck Jones's term specificity (inverse document frequency).

## 32. Codd, *A Relational Model of Large Shared Data Banks* (1970)

**Set out to.** Apply elementary relation theory to shared access to large banks of formatted data. Until then, relations had been used mainly in deductive question-answering systems. Codd attacks two problems:
- **Data independence:** "the independence of application programs and terminal activities from growth in data types and changes in data representation".
- **Data inconsistency,** of certain kinds, even in nondeductive systems.

The relational view beats the graph or network model (Bachman, McGee). It describes data "with its natural structure only—that is, without superimposing any additional structure for machine representation purposes". That makes it a basis for a high-level data language with maximal independence between programs and machine representation, and a sound basis for treating derivability, redundancy and consistency. It also clears up network-model confusions such as "mistaking the derivation of connections for the derivation of relations". Implementation is not discussed.

**Data dependencies in present systems.** Data description tables were a major advance, but users still see representational properties. Codd names three dependencies to remove.
1. **Ordering dependence.** A file is stored in one total ordering tied to hardware addresses, such as a parts file in ascending part number. Programs that assume the presentation order equals the stored order fail when the ordering changes. "All the well-known information systems that are marketed today fail to make a clear distinction between order of presentation on the one hand and stored ordering on the other."
2. **Indexing dependence.** An index is purely performance-oriented: it speeds queries, slows insertions and deletions, and is informationally redundant. Indices must come and go as activity changes, so the question is: "Can application programs and terminal activities remain invariant as indices come and go?"
   - TDMS indexes every attribute unconditionally.
   - IMS offers, per file, either no indexing or a primary-key index, and program logic does not depend on the choice.
   - IDS programs refer to indexing chains by name and fail when the chains are removed.
3. **Access path dependence.** In tree-structured or network files, programs are impaired when the structure changes.
   - The example has parts (part number, name, description, quantity on hand, quantity on order), projects (number, name, description), and the quantity of each part committed to each project. It can be structured five ways (Figs 32.1–32.5):
     1. projects subordinate to parts;
     2. parts subordinate to projects;
     3. parts and projects as peers, with commitments subordinate to projects;
     4. the same, with commitments subordinate to parts;
     5. parts, projects and COMMIT (part #, project #, quantity committed) all as peers.
   - The query is the part number, part name and quantity committed for every part used in project "alpha". A program written for one structure fails on at least three of the others, by referring to a file that does not exist or missing one it needs.
   - Never obsoleting an access path until every program using it is obsolete is impractical, because the paths grow excessively large.

**Construct: the relational view.**
- **Relation,** in the accepted mathematical sense: given sets S₁, S₂, …, S_n, not necessarily distinct, R is a relation on them if it is a set of n-tuples whose first element is from S₁, second from S₂, and so on. S_j is the jth **domain**, and n is the **degree** (unary, binary, ternary, n-ary).
- **The array representation,** which is not essential:
  1. each row is an n-tuple;
  2. the order of rows is immaterial;
  3. all rows are distinct;
  4. the order of columns is significant;
  5. columns are labeled with domain names.
- **Fig 32.6, supply** (supplier, part, project, quantity), degree 4: (1, 2, 5, 17), (1, 3, 5, 23), (2, 3, 7, 9), (2, 7, 5, 4), (4, 1, 1, 12).
- **Fig 32.7, component** (part, part, quantity): component(x, y, z) means part x is an immediate component of part y, with z units of x per unit of y. This is the parts explosion problem, and it shows why column order matters. Its rows are (1, 5, 9), (2, 5, 7), (3, 5, 2), (2, 6, 12), (3, 6, 3), (4, 7, 1), (6, 7, 1). Tree-structured systems such as IMS/360 cannot represent a relation with two identical domains.
- **Data bank:** a collection of time-varying relations of assorted degrees.
- **Relationship:** the domain-unordered counterpart of a relation (its equivalence class under permutation of domains). Codd needs it because degree 30 is not uncommon and users should not have to remember domain order. Identical domains are qualified by a **role name**, as in component (sub.part, super.part, quantity). Users then need know only a relationship's name and its domain names.
- **Active domain:** the set of a domain's values represented at an instant.
- **Primary key:** a domain or combination whose values uniquely identify each n-tuple. Part number qualifies; part color does not. A key is **nonredundant** if it is simple or none of its simple domains is superfluous. If there are several nonredundant keys, one is arbitrarily chosen as "the" primary key.
- **Foreign key:** a domain or combination of R that is not its primary key but whose values are values of the primary key of some relation S, possibly R itself. In supply, (supplier, part, project) is the primary key, and each component separately is a foreign key.
- **Simple and nonsimple domains.** A simple domain has atomic values. A nonsimple domain has relations as elements, such as an employee's salary history, a binary relation on date and salary. "Attribute" and "repeating group" roughly correspond to them.

**Normal form.** A relation whose domains are all simple can be stored as a two-dimensional, column-homogeneous array, so eliminate nonsimple domains by **normalization**.
- **Fig 32.8, unnormalized.** employee (man#, name, birthdate, jobhistory, children), with jobhistory (jobdate, title, salaryhistory), salaryhistory (salarydate, salary) and children (childname, birthyear).
- **The procedure.** Start at the top of the tree. Expand each immediately subordinate relation by inserting the parent's primary key; the expanded relation's key is its own key augmented by the parent's. Strike the nonsimple domains from the parent, remove the top node, and repeat on each subtree.
- **Fig 32.9, normalized.** employee′ (man#, name, birthdate), jobhistory′ (man#, jobdate, title), salaryhistory′ (man#, jobdate, salarydate, salary), children′ (man#, childname, birthyear).
- **Conditions.** (1) The graph of interrelationships of the nonsimple domains is a collection of trees. (2) No primary key has a nonsimple component domain. "The writer knows of no application which would require any relaxation of these conditions."
- **Bulk communication.** The normalized array is simple for storage and for exchange between systems: a compressed array with no pointers, no hash addressing, and no indices or ordering lists.
- **Names** take the form R(g).r.d: relation name, optional generation, optional role, domain. Often this is just R.d.

**Linguistic aspects.**
- **Data sublanguage.** Codd proposes a universal data sublanguage R based on the applied predicate calculus; first order suffices if the relations are in normal form. It is a yardstick for the power of other data languages and is embeddable in a host language H.
  - R declares relations, domains and primary keys, retrieves any subset subject to security, inserts and deletes. H declares storage representations and supplies arithmetic functions.
  - "The universality of the data sublanguage lies in its descriptive ability (not its computing ability)."
- **Symmetric exploitation.** Any combination of a relation's arguments can serve as knowns and the rest as unknowns, "because the information (like Everest) is there". Equal performance in every direction is not expected.
- **Path proliferation.** A network needs two directed paths for a binary relation and n! named paths for degree n. A nested binary notation such as Feldman's LEAP needs 2n − 1 names against n + 1 for n-ary. For supply, P(supplier, Q(part, R(project, quantity))) uses 7 names against 5, and its asymmetry makes some queries awkward.
- **Named and expressible relations.** The **named** set is the relations identified by simple names. The **expressible** set is every relation designable in the data language, from names, generations, roles, domains, logical connectives, quantifiers and constant relation symbols such as = and >. The named set is usually a very small subset of the expressible one. The designer picks a class of stored representations "just adequate to cover the spectrum of performance requirements", and the system translates requests into efficient actions on whatever representation is current. With concurrent access, responsibility for efficient response shifts from the user to the data system.

**Operations on relations.** Set operations apply, but the result may not be a relation, as with the union of a binary and a ternary relation.
- **Permutation** interchanges columns: the converse of a binary relation, or any of the 4! = 24 permutations of supply. It is irrelevant to the user's domain-unordered model but matters for stored representations.
- **Projection** selects columns, strikes the others and removes duplicate rows. With L = i₁, i₂, …, i_k and R n-ary (n ≥ k), π_L(R) is the k-ary relation whose jth column is column i_j of R. Fig 32.10: π₃₁(supply), on (project, supplier), is (5, 1), (5, 2), (1, 4), (7, 2).
- **Join.**
  - R is **joinable** with S if there is a ternary U with π₁₂(U) = R and π₂₃(U) = S; U is then a join of R with S. If π₂(R) = π₁(S), they are joinable.
  - The **natural join** is R ∗ S = {(a, b, c) : R(a, b) ∧ S(b, c)}.
  - Fig 32.11: R (supplier, part) = (1, 1), (2, 1), (2, 2) and S (part, project) = (1, 1), (1, 2), (2, 1). Fig 32.12: R ∗ S = (1, 1, 1), (1, 1, 2), (2, 1, 1), (2, 1, 2), (2, 2, 1). Fig 32.13 shows another join, U = (1, 1, 2), (2, 1, 1), (2, 2, 1).
  - Part 1 has more than one relative under R and under S, a **point of ambiguity**, so there are several joins. If π₂₁(R) or S is a function, there is no point of ambiguity and the natural join is the only join.

The book omits the sections on redundancy and consistency. The summary says the model protects users from disruptive changes in representation, defines a normal form, and defines two types of redundancy for maintaining a consistent state. That last problem is "bound to become a serious practical problem as more and more different types of data are integrated together into common data banks."

**Led to.** In academia computing seemed to be about algorithms, but in business it was always about data. One database scientist put it: "data was the ocean, deep, eternal, and mysterious, and algorithms were just boats skimming its surface." Early computing was about numbers, such as the Mark I's tables (7), and Turing's codebreaking was combinatorial search on very small data. Bush (11) foresaw large-scale data manipulation, and Aiken (7) and Hopper (16) anticipated business use. IBM grew out of tabulating machines for the U.S. Census. In the mid-1960s it built IMS to manage the Apollo inventory, drawing on graph theory, since parts with sub-parts shared among assemblies form a directed graph.

Codd's insight parallels the compiler's: describe and query data with formal clarity and leave physical organization to the system. He frames data as relations, depicted as tables whose row order is semantically irrelevant, and, "most importantly", gives a relational algebra for combining them. IBM was tepid, since the model competed with its own products, and Codd left to start his own firm. Research systems followed in the later 1970s: IBM's System R, and Ingres, built by Stonebraker at Berkeley. Commercial systems from Oracle, Tandem, Stonebraker's Relational Technology Inc. and IBM (1979–1981) made the model the de facto standard. SQL is now ubiquitous, and Codd won the Turing Award.

## 35. Spärck Jones, *A Statistical Interpretation of Term Specificity and Its Application in Retrieval* (1972)

**Set out to.** Show that the specificity of an index term should be interpreted statistically, "as a function of term use rather than of term meaning". Exhaustivity of document descriptions and specificity of terms were usually treated as independent. Experiments with three test collections show two things:
- Frequently occurring terms are required for good overall performance.
- Weighting terms by collection frequency, so that matches on less frequent, more specific terms count for more, gives considerable improvements by a very simple procedure.

**Exhaustivity and specificity.** **Exhaustivity** is a property of a document description: how fully its terms cover the document's topics. **Specificity** is a property of an index term: the level of detail at which it represents a concept.
- More terms give more matches. The optimum exhaustivity maximizes relevant matches while avoiding too many false drops, and requests have an exhaustivity too.
- In vocabulary construction, specificity is semantic: "beverage" against "tea", "coffee", "cocoa". The general term applies to more documents.
- Actual use diverges from prediction. Some documents "cry out for 'beverage'", others cannot take it, and many could go either way. As a collection grows at fixed exhaustivity, some terms become heavily used and stop discriminating, whatever they mean.
- "A frequently used term thus functions in retrieval as a nonspecific term, even though its meaning may be quite specific in the ordinary sense."

**Construct: statistical specificity.** "The exhaustivity of a document description is the number of terms it contains, and the specificity of a term is the number of documents to which it pertains."
- Longer descriptions make existing terms more frequent more often than they add new ones.
- Formal optimizations exist (Zunde and Slamecka; Salton), but they do not select terms, collections are not static, and requests are hard to control.
- In practice there are always some "disagreeably non-specific terms" that retrieve many documents, few of them relevant. They are more of a nuisance than rare, over-specific terms that retrieve nothing.

The test collections are Cranfield (aeronautics), INSPEC, and Keen's from the College of Librarianship Wales, all indexed by extracted keyword stems.
- **Most frequent terms:** Cranfield, one term in 144 of 200 documents; INSPEC, 112 of 541; Keen, 199 of 797.
- **Frequent stems** are not necessarily central or general:
  - Keen: "index-", "librar-", "inform-", "comput-";
  - INSPEC: "theor-", "measur-", "method-";
  - Cranfield: "flow-", "pressur-", "distribut-", "bound-".
- **Rare stems:**
  - Keen: "purchas-", "xerograph-";
  - INSPEC: "parallel-", "silver-";
  - Cranfield: "logarithm-", "seri-".

**Fig 35.1**

| | Cranfield | INSPEC | Keen |
|---|---|---|---|
| **A.** documents | 200 | 541 | 797 |
| terms | 712 | 1,341 | 939 |
| terms per document | 32 | 12.2 | 7.9 |
| documents per term | 9 | 4.9 | 6.1 |
| **B.** requests | 42 | 97 | 63 |
| terms represented | 166 | 248 | 183 |
| terms per request | 6.9 | 5.6 | 5.3 |
| documents per request term | 31.6 | 11.5 | 44.8 |
| **C.** retrieving terms per request | 5 | 3.2 | 3.3 |
| retrieving terms per document | 1.8 | 1.2 | 1.2 |
| retrieving terms per relevant document | 3.6 | 2 | 1.8 |
| **D.** frequent terms | 96 | 73 | 50 |
| frequent terms per request | 4 | 2.5 | 2.3 |

Requests are phrased in better-known, more frequent terms. Cranfield's vocabulary averages 9 postings per term, but its request terms average 31.6; Keen's, 6.1 against 44.8.

**Specificity and matching.**
- **Conjunction.** Combining terms narrows matches: Cranfield's "bound-", "layer-" and "flow-" occur in 73, 62 and 144 documents, but only 50 have all three. Requests start with 5.3 to 6.9 terms, yet relevant retrieved documents match on only 1.8 to 3.6 of them, and all retrieved documents, mostly non-relevant, on 1.2 to 1.8.
- **Dropping frequent terms.** "While frequent terms cause noise, they are also required for reasonably high recall." For INSPEC, a threshold of 20 or more documents removes 73 of 1,341 terms. In Fig 35.2 (Cranfield recall/precision, curves for all terms, frequent terms and non-frequent terms), matching on non-frequent terms alone keeps precision but lowers the recall ceiling by at least 30 percent; for Keen it falls from 75 percent to 25 percent.
  - The reason: request terms are more frequent than average, and a few very frequent terms do much of the work. "Flow-" appears in 12 of the 42 Cranfield requests, and about half of all request terms are very frequent (Fig 35.1 D).
  - "Throwing very frequent terms away is throwing the baby out with the bath water."
- **The conclusion:** "allow some merit in frequent term matches, while allowing rather more in non-frequent ones", and maximize the number of matching terms.

**Weighting by specificity (collection-frequency weighting).** In simple coordination matching a frequent term counts as much as a rare one. Instead, correlate a term's matching value with its collection frequency, whose distribution has the familiar Zipf shape.

  f(n) = m such that 2^(m−1) < n ≤ 2^m

  weight of a term occurring in n of N documents = f(N) − f(n) + 1

- **Weights.** For Cranfield, N = 200: a term in 90 documents has weight 2, and one in 3 documents has weight 7.
- **Scoring.** A document's retrieval level is the sum of the weights of its matching terms, which turns coordination levels into a **quasi-ranking**. Matching on terms of frequency 15 and 43 gives 5 + 3 = 8; on 3 and 7, 7 + 6 = 13. The range is "stretched", so documents are discriminated more finely.
- **Other kinds of weight.** Weighting by importance to the document, or by within-document frequency (Artandi and Wolf; Salton and Lesk), indicates content. Collection-frequency weighting is "quite different": it measures a term's value for distinguishing one document from another. A term may be common in a document and rare in the collection, or the reverse.
- **Prior use.** It had been used only informally, for example in an operational interactive system at A. D. Little with automatically extracted keywords and a changing vocabulary. It suits automatic indexing better than manual.

**Results.** On all three collections, weighting gives a substantial improvement over simple term matching. In Figs 35.3 (Cranfield), 35.4 (INSPEC) and 35.5 (Keen), the weighted curve lies above and to the right of the unweighted one throughout, and the difference in enclosed area is fully significant.
- The improvement is "as good an improvement over simple unweighted keyword stem matching as has been obtained by any other means, including carefully constructed thesauri." "Insofar as anything can be called a solid result in information retrieval research, this is one."
- It is extremely simple. It works with automatically stemmed keywords, needs only a term-frequency list, and adjusts naturally as the collection grows and changes.

**Led to.** The method is still at the heart of retrieval, with two components:
1. The more often a term appears in a document, the more relevant the document probably is: repeated "zebra" means a document about zebras. But "the" repeats too, so frequency alone is unreliable.
2. Temper that by how common the term is across the collection. The rarer it is, the more significant it is for the few documents containing it. This is **inverse document frequency (IDF)**, and most web search engines use some form of it.

It was carefully tuned with mathematical statistics, and it makes no attempt to extract meaning, analyze sentence structure or cluster words. It showed that "simple text statistics could be extremely powerful tools in the analysis of natural language". Spärck Jones worked at Cambridge from the 1950s until 2002 and was president of the Association for Computational Linguistics in 1994, but received the title of professor only in 1999.
