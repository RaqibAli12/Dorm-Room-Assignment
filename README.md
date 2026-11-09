Assigns students to dorm rooms in Python using a deferred acceptance algorithm. Mutually requested roommates are matched as a single group, and every assignment respects hard constraints. We compared two priority policies across 7 student datasets and 5,330 rooms.

## Parts
- **Part A** (`part-a/Dorms_Submission.ipynb`): the initial matching and analysis.
- **Part B** (`part-b/Dorms_Errors.ipynb`): adjusting the match after new information became available.

## Approach
**Hard constraints**
- Graduate students only in graduate halls (JA and BA), and undergraduates never there
- Students with accessibility needs only in accessible rooms
- A room's price never exceeds the student's maximum budget
- A roommate group is placed in a room that fits all of its members

**Preferences** (used to rank room types): preferred hall, residence type, single room or not, and roommate. Cheaper rooms rank higher as a tiebreaker. Only mutual roommate requests are honored.

**Algorithm.** Students (or roommate groups) apply to their highest-ranked room type. Each room type keeps its highest-priority applicants until its beds run out and rejects the rest. A group rejected everywhere is split, and its members re-enter individually.

**Policies compared**
- **Budget priority:** students with accessibility needs first, then lower budgets first, then a random draw
- **Lottery:** students with accessibility needs first, then a random draw

## Results
- No constraint violations across all 42 runs (2 policies x 7 datasets x 3 random seeds).
- On six of the seven datasets, the budget priority housed 81.5-87.7% of students versus 74.0-79.2% under the lottery. Dataset 2 was much lower under both (62.8% and 59.9%) because over half its students can only afford the cheapest beds.
- The budget priority housed more students on every dataset but gave students their top-choice hall less often.
- Roommate requests were the weakest result: only about half of students with a mutual request were housed with that roommate.
- Students with a $6,000-$7,500 budget gained almost nothing from the budget priority.

