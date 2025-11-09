https://contest.yandex.ru/contest/69765/problems/E/

# Text Classification Using Keywords

Senior meteorologist Adilkhan works at Kazhydromet in Almaty and is always striving to stay at the forefront of scientific advancements. He follows the latest discoveries in meteorology and shares interesting articles with his colleagues. One day, Adilkhan assigned his intern Darkhan an important task: to analyze scientific articles and news for the meteorological service.

However, Darkhan, in addition to his love for meteorology, was an avid reader of Medium. He spent hours reading, but instead of climate-related articles, he sent materials about football, space, and robots. Adilkhan was shocked when texts about World Cup tournaments and space missions ended up on his desk.

Thinking it over, Adilkhan realized that Darkhan simply didn’t know how to properly classify articles. So, he decided to help his intern and come up with a way to efficiently sort texts using keywords that would clearly indicate the subject of the article.

Text classification using keywords is a important part of modern conversational systems (chatbots, assistants). This method allows us to accurately, and more importantly, reliably determine user intent and correctly guide them through the system's appropriate response flow. 

The task is to create an algorithm that, based on keywords from a dataset of Medium articles, can accurately match each text to its corresponding Tag. The main dataset required for this is available at: [train_set.csv](https://disk.yandex.ru/d/FXehRMjaXkwUTA).

It contains around 50,000 examples and 95 unique classes/Tags. The dataset is in CSV format, with columns separated by the ``\textbackslash t'' symbol (i.e., four spaces or a Tab).

**Text** — the title and subtitle of the article.  
**Tag** — the label or class of the text.  
**Keywords** — a set of words extracted from multiple texts that belong to a specific tag (for example, for the tag “football,” the keywords could be: 'Football,' 'league of champions,' 'Cristiano,' 'Cristiano Ronaldo,' 'cr7,' 'world cup,' 'Ballon d'Or').  
**Metric** or rule for scoring: percentage (\%) of correctly predicted classes/Tags from the hidden dataset

**Example:**  
*Text* — Brazil wins the World Cup for the fifth time in Japan and South Korea.  
*Tag* — football

## General Steps:

1. Analyze texts in the dataset and tokenize them (split by spaces, into n-grams, etc., at your discretion). This converts the text into a set of keywords/phrases/tokens.
2. For each tag/label, create a set of its most important and relevant keywords/phrases/tokens.
3. Create a rule to match text and tag by intersecting their keyword sets (the rule could be based on majority voting, the highest number of matching words, etc.).
4. Using the algorithm from step 3, assign a Tag to each input text in the “hidden” dataset.

Each row corresponds to a separate text (Title + Subtitle), with the total number of texts denoted by \( N \), where \( 1 \leq N \leq 10,000 \). The format is as follows:

----------------------------------------------------------------------------------------------------------------------------------

***Title***: How do Transformers work? ***Subtitle***: In this section, we will take a high-level look at the architecture of Transformer models.

***Title***: ...

...

...

Row N

----------------------------------------------------------------------------------------------------------------------------------

Code(Python):
```python
import sys
input_data = sys.stdin.read()
lines = input_data.splitlines()
```

A single string where each Tag is separated by ", ": 

"\( \text{ai}, \text{football}, \text{politics}, \ldots, \text{N-th Tag} \)"

All data is in English, and each article has only one unique Tag.
