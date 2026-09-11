# Interview Test Questions: Chat Agent Evaluation

Thank you for interviewing with Brightmine! We appreciate you taking the time to complete this exercise. We expect this assessment to take between one to four hours, but you're welcome to take all the time you need. We encourage you to use all the tools you'd reach for in your day-to-day work, including LLM coding assistants, external models, data enrichment tools, and any libraries you find helpful.

---

## Data Files

- **Reference data:** `interview_reference_data.json`
- **Agent answers:** `interview_answer_data.json`

Both files are serialized using pandas with `orient="table"`.

---

## Schemas

### Reference Data (`reference_df`)

| Column | Type | Description |
|--------|------|-------------|
| *index:* `Question` | `str` | The user question posed to the HR chatbot agent. |
| `optimal_search_results` | `Set[str]` | Unordered set of Brightmine Article IDs that a well-functioning retrieval system should return for the given question. These represent the ground-truth relevant documents as determined by Brightmine editors. There may be multiple articles that can equally-well answer the question.|
| `gold_standard_text` | `str` | A comprehensive, expert-authored reference answer for the question. Represents the ideal response an agent should produce, covering all key legal requirements, thresholds, and nuances. |

### Answer Data (`answer_df`)

| Column | Type | Description |
|--------|------|-------------|
| *index:* `Question` | `str` | The user question posed to the HR chatbot agent. Matches the index of the reference dataset. |
| `cited_articles` | `List[str]` | Brightmine Article IDs that the agent explicitly cited in its response. These are the articles the agent used as sources when composing its answer and presented as sources to the end user. |
| `agent_answers` | `str` | The full text answer returned by the agent for the given question. This is the response presented to the end user. |
| `search_results` | `List[str]` | Ordered list of Brightmine Article IDs returned by the retrieval/search step, ranked by relevance. The first element is the top-ranked result. |

---

## Questions

### 1. Import the data

Import both datasets into pandas DataFrames. 

### 2. Evaluate the quality of the answer text

Write code to evaluate the quality of `answer_df["agent_answers"]`.

### 3. Evaluate the quality of the cited articles

Write code to evaluate the citations in `answer_df["cited_articles"]`.

### 4. Evaluate the quality of the search retrieval

Write code to evaluate `answer_df["search_results"]`.
