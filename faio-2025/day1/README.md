<!-- DOCTOC SKIP -->

<h1 align="center">
  🏁 FAIO 2025 — 1st Round
</h1>

<p align="center">
  <strong>All translations to Kazakh (Қазақша) and Russian (Русский) for the problems are in</strong>
  <a href="./1st-round-FAIO-2025-KZ-RU.pdf">HERE</a>
</p>

---

🎓 **Welcome to the 1st Round of FAIO 2025!**

Dear participant, congratulations on reaching the first stage of our Olympiad!  
In this round, you'll need to solve **3 problems** covering different areas of artificial intelligence.  
Each task is worth **1 point**. The maximum score for this round is **3 points**.

---

### 🧩 Problem 1 — Qaz-letters
- 📄 **Task Description:** You need to build a machine learning model for automatic Kazakh letter classification. The dataset contains only numerical features extracted from images: statistical, geometric, projection, and transform-based features — not raw images.
- 🔧 **What to do:** Train a classification model that predicts the correct Kazakh letter based on the given features.
- 📊 **Metric:** Performance is evaluated using Accuracy, which measures the proportion of correctly classified letters. The metric ranges from 0 to 1 (1 means all letters are classified correctly, 0 means none are correct).
- 🔗 **Kaggle:** [Click here](https://www.kaggle.com/t/23291ce18385cab3fab6ff5f45f1b0ba)
- 📝 **Task:** [Click here](./qaz_letters.md)

### 🧩 Problem 2 — Who is the best pitcher?
- 📄 **Task Description:** Build a RAG-powered question-answering agent for Major League Baseball (MLB). The goal is to answer baseball-related questions using large, structured JSON datasets about teams, players, games, seasons, and records.
- 🔧 **What to do:** Develop a system that ingests and parses JSON data, organizes it for knowledge retrieval, and uses a retrieval-augmented generation (RAG) architecture to generate accurate answers to MLB questions.
- 📊 **Metric:** Accuracy is the evaluation metric — the number of correct answers divided by total questions. The metric ranges from 0 to 1 (1 means all answers are correct, 0 means none are correct).
- 🔗 **Kaggle:** [Click here](https://www.kaggle.com/t/96bfb8a3431c91d7479308df476fc0ee)
- 📝 **Task:** [Click here](./Who_is_the_best_pitcher.md)
- 🥇 **Baseline:** [Click here](./host-author-s-baseline.ipynb)

### 🧩 Problem 3 — Misssing fundamental puzzle
- 📄 **Task Description:** Build a pitch classification model for musical audio illusions. The goal is to identify the original musical note (e.g., C4, G#5) from audio samples in which the fundamental frequency and several harmonics have been removed.
- 🔧 **What to do:** Develop a system that analyzes mono WAV files (22050 Hz). Each file is a musical excerpt with missing frequencies—your model must reconstruct the pitch label from the spectral pattern of the remaining harmonics.
- 📊 **Metric:** Accuracy is the evaluation metric — the number of correct predictions divided by the total number of examples. The metric ranges from 0 to 1 (1 means all answers are correct, 0 means none are correct).
- 🔗 **Kaggle:** [Click here](https://www.kaggle.com/t/fbaef0197897255be8710f080fd1b4ae)
- 📝 **Task:** [Click here](.//Missing_Fundamental_Puzzle.md)

---

<p align="center">
  🎉 <strong>Good luck and enjoy the challenge!</strong>
</p>
