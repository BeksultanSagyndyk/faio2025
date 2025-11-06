# Overview

Adilkhan ⚾ and Darkhan 🧢 were two friends who loved sports, especially baseball.  
They started a public website — **BaseballAndMath.com** — where fans could write posts, ask questions, and share thoughts about games.  
It quickly became a lively community for discussing scores, players, and baseball trivia from around the world.

At first, things went well—people wrote about their favorite teams and players, and the community grew.  
But soon Adilkhan and Darkhan noticed a big problem:  
users wanted **real-time answers** to sports statistics questions like:

- *“How many home runs did Ohtani hit this season?”*  
- *“Who scored for the Yankees yesterday?”*  

They tried popular AI tools like **ChatGPT**, **Gemini**, and others. While these models were impressive, they quickly realized something:  

❌ The AI agents **couldn’t handle real-time sports data.**  
❌ They gave outdated or incorrect answers about recent events and statistics.  

That’s when the two friends decided:  

> *“If no tool can do it, let’s build our own!”*  

So Adilkhan and Darkhan set out to create an **AI agent for sports Q&A**—one that would rely not just on static knowledge, but on **live, real-world data** from trusted sources.  

Their mission became clear:  
⚾ Build an **LLM-powered agent** that can accurately answer questions about Major League Baseball (MLB), even as new games and stats are being updated every second.  

---

## Why This Approach Works: RAG

The solution they chose is based on **Retrieval-Augmented Generation (RAG).**

### What is RAG?  
RAG combines the strengths of two worlds:  
1. **Retrieval** – fetching the most relevant, up-to-date information from a database, API, or knowledge source.  
2. **Generation** – using a large language model (LLM) to understand the question and generate a natural, useful answer based on the retrieved facts.  

Instead of relying only on the LLM’s memory (which might be outdated), RAG ensures answers are:  
✅ **Accurate** – grounded in real statistics and live data  
✅ **Fresh** – reflecting the most recent sports events  
✅ **Useful** – presented in natural, human-like explanations  

---

## Your Challenge  

✨ The competition challenge is:  
**Help Adilkhan and Darkhan build their RAG-powered sports agent for MLB fans!**

# Description

This competition challenges you to build a question-answering agent for MLB that reasons over large, structured JSON datasets aggregated from multiple endpoints.

What you’ll build
- Ingestion & parsing: Efficiently load and normalize large JSON files (multiple endpoints, heterogeneous schemas).
- Knowledge access layer: Design lookups/indexes to retrieve the minimal relevant facts per query.
- Reasoning & answering: Produce accurate, well-formatted answers to user questions about MLB (teams, players, games, seasons, records, etc.).
- Generalization: Perform reliably on a hidden validation set of questions.

# Evaluation

Submissions are evaluated based on **accuracy**, calculated as the number of correct answers divided by the total number of questions.  

$$
\text{Accuracy} = \frac{\text{Number of correct predictions}}{\text{Total number of examples}}
$$

## Submission File  
For each ID in the test set, you must provide the predicted answer. The file should include a header and follow this format:

    ID,ANSWER
    1,"Paris"
    2,"42"
    3,"blue"
    etc.

- `ID` corresponds to the question identifier.  
- `ANSWER`  string 


The ANSWER field must always be a string.
	•	Even if the original value in the JSON file was a number (integer or float), it should be stored as a string.
	•	Examples:
	•	1 → "1"
	•	1.00 → "1.00"
	•	Exact Match:
Be careful not to transform or reformat the value.
The ANSWER should exactly match the original value from the JSON file.
	•	Do not round, truncate, or change formatting.
	•	Example:
	•	JSON value: 123.4500
	•	✅ Correct ANSWER: "123.4500"
	•	❌ Incorrect ANSWER: "123.45" or "123.45 (approx.)"

# Dataset description

This dataset contains aggregated endpoint dumps in JSON format for Major League Baseball (MLB). Each JSON file corresponds to a specific type of entity, with consistent key structures across entities.  

## Files

* **players.json** – aggregated player-level data  
* **teams.json** – aggregated team-level data  
* **league.json** – aggregated league-level data  

## Format and Structure

Each file is stored in **JSON format**. The root-level keys are entity names (e.g., player name or team name). Under each root key, the entity has a consistent set of attributes.  

### Example Structures

- **players.json**  
  - Root key: player’s name  
  - Value: dictionary containing the same set of attributes for every player  

- **teams.json**  
  - Root key: team’s name  
  - Value: dictionary containing the same set of attributes for every team  
- **league.json**
  - Top-level (no league root): metadata, teams, standings, leaders

## Evaluation Files

### `test.csv`
- **Columns:** `ID`, `question`
- **Description:** Each `question` is generated based on data from `players.json`, `teams.json`, and `league.json`.
- **Goal:** For each `ID`, generate an **ANSWER** using your inference algorithm applied to these JSON sources.

### `submission.csv`
- **Columns:** `ID`, `ANSWER`
- **Details:**
  - Must contain one row per `ID` from `test.csv`.
  - Exactly **5 random rows** contain the correct `ANSWER`.
  - All other rows contain the literal string **"no answer"**.
  - Submitting this baseline file guarantees **a non-zero score**, ensuring your inference pipeline is working.

```bash
kaggle competitions download -c who-s-the-best-pitcher-v2
