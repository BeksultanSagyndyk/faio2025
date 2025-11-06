# Overview
## 🏆 

Welcome to the **Music Recommendation System Challenge!** 🎶  

Our Team:  
- **Djalil** — Product Owner at **hitter & Izi**, wants every user to discover the perfect soundtrack for their day 🎧  
- **Darkhan** — Data Scientist, tasked with turning mountains of user data into smart, personalized recommendations 💡  
- **Adilkhan** — an active user of the platform, curious and eager for new music discoveries 🎵  

Your mission: **help Darkhan build a recommendation system** that predicts the **top 50 most relevant tracks** for each user based on their listening history and preferences — making sure users like Adilkhan get the songs they love most.

The dataset comes from **real interactions** on hitter and Izi, where users listen, like, and download tracks daily. You can explore **any approach** — from classic machine learning to deep learning or hybrid models.  
Think of it as crafting the ultimate playlist that keeps Adilkhan hitting “play” again and again! 🚀  

---

## 🎯 Goal

Build a model that recommends **50 tracks per user**, aiming to predict which songs each listener will enjoy the most — and **how much** they’ll actually listen.  

Help Darkhan impress Djalil with a model that truly understands users like Adilkhan, turning raw data into a seamless, personalized music experience. 🔥

# Evaluation

## 📊 Evaluating Recommendation Quality

Here’s how we measure who made the best recommendations:

1. **Predict Tracks**  
   For each user (e.g., Adilkhan!), your model predicts a list of **50 tracks** they might like.

2. **Check Listening Fractions**  
   For each recommended track, we record **how much the user actually listened**:  
   - `0.0` — not listened at all  
   - `0.25` — listened a quarter of the track  
   - `0.5` — listened halfway  
   - `0.75` — listened three-quarters  
   - `1.0` — listened fully (replays don’t count extra)

3. **User Score**  
   Sum these fractions across the 50 tracks → this gives a **score for that user** (range: 0 to 50).

4. **Average per User**  
   Compute the mean of all users’ scores → tells us, on average, how many tracks each user actually listened to (range : 0 to 50). 

5. **Final Score**  
    **normalized score** between 0 and 1. 

### 📈 How to Interpret the Metric 

- **Score ≥ 0.25** → Users are starting to engage with your recommendations. **Even a quarter of a track counts as a small win!**  
- **Score ~0.5** → Users listen to about half of your recommendations. **Nice job! Your suggestions are clearly interesting.**  
- **Score ~0.75** → Most tracks are listened to three-quarters of the way. **Great work! Users really like your recommendations.**  
- **Score ~1.0** → Users fully listen to almost all recommended tracks. **Excellent! You’re nailing it.**

# Submission

## Overview
Your submission should contain ranked recommendations for each user in the test set. Each user must have exactly **50 item recommendations** ranked from 1 to 50, where rank 1 is the most recommended item and rank 50 is the least recommended.

## File Format
- **File Type**: CSV file

## Column Specifications

| Column | Type | Description | Constraints |
|--------|------|-------------|-------------|
| `id` | Integer | Unique row identifier | Sequential starting from 0 |
| `user_id` | Integer | User identifier from test set | Must match test set user_ids |
| `item_id` | Integer | Item identifier to recommend | Must be valid item_id |
| `rank` | Integer | Recommendation rank | 1-50 (1 = highest, 50 = lowest) |

## Requirements
- **All columns are mandatory** - missing any column will result in submission error
- Each user in the test set must have **exactly 50 recommendations**
- Ranks must be unique per user-item (1 through 50)
- No duplicate item recommendations for the same user
- Colum `id` is mandatory 

## Example , how to create id column:
`recos.insert(0, 'id', range(len(recos)))`


## Sample Submission

| id  | user_id | item_id   | rank |
|-----|---------|-----------|------|
| 0   | 1       | 123       | 1    |
| 1   | 1       | 3123      | 2    |
| 2   | 1       | 3213123   | 3    |
| 3   | 1       | 123312312 | 4    |
| 4   | 1       | 112       | 5    |
| 5   | 1       | 1         | 6    |
| 6   | 1       | 73        | 7    |
| 7   | 1       | 99        | 8    |
| ... | ...     | ...       | ...  |
| 49  | 1       | 705       | 50   |

# Dataset Description

This dataset is derived from **real user interactions** on the **hitter** and **Izi** music platforms. It includes **user-track interactions**, **track metadata**, and **user metadata**.  

The **training set** covers **production-level user behavior** from **2025-02-28 to 2025-08-30** (a 6-month period).  
The **test set** represents **user interactions** from **2025-09-01 to 2025-09-15**, used to evaluate recommendation performance.  It only includes users who appear in the training interactions (**no cold-start users**).  

> ⚠️ Note: `interactions.csv` may contain noise, duplicates, or minor bugs reflective of real-world data.  
> ⚠️ Note: `item_metadata.csv`, `user_metadata.csv` may have missing or incomplete records.

---

### Files
- **interactions.csv** — Records of user interactions with tracks  
- **item_metadata.csv** — Metadata about tracks  
- **user_metadata.csv** — Metadata about users  
- **test.csv** — List of users for whom predictions must be made  

---

### **interactions.csv**
| Column | Description | Data Type | Notes |
|:--|:--|:--|:--|
| user_id | Unique identifier for the user. | Integer | References users in `user_metadata.csv`. |
| item_id | Unique identifier for the track (item). | Integer | References tracks in `item_metadata.csv`. |
| listened_duration | Duration (in seconds) the user listened to the track in this interaction. | Integer | May be partial or noisy; includes skips/outliers. |
| listened_datetime | Timestamp of when the interaction occurred. | Datetime | Format: `YYYY-MM-DD HH:MM:SS.ssssss`.  |

> 🕒 **Time Range:** `2025-02-28` → `2025-08-30` (6 months of production-level data)

---

### **item_metadata.csv**
| Column | Description | Data Type | Notes |
|:--|:--|:--|:--|
| item_id | Unique identifier for the track. | Integer | Primary key for tracks. |
| track_name | Name/title of the track. | String | May include special characters or non-English text. |
| artist_name | Name of the artist(s) or performer(s). | String | Can include collaborations (e.g., “Artist feat. Other”). |
| track_duration | Full duration of the track in seconds. | Integer | Total length of track. |
| track_genres_list | Comma-separated list of genres associated with the track. | String | Example: `['Genre1', 'Genre2']`; may include non-English genres. |
| track_dislike_count | Total dislikes received by the track. | Integer | Aggregate metric; starts at 0 for new tracks. |
| track_like_count | Total likes received by the track. | Integer | Aggregate metric; starts at 0 for new tracks. |
| track_download_count | Total downloads of the track. | Integer | Aggregate metric; starts at 0 for new tracks. |

---

### **user_metadata.csv**
| Column | Description | Data Type | Notes |
|:--|:--|:--|:--|
| user_id | Unique identifier for the user. | Integer | Primary key for users. |
| age_bin | Binned age group of the user  (based on the ML model). | String | Examples: `'18_29'`, `'30_44'`, `'45_60'`, `'61_inf'`. |
| children | Number of children the user has (based on the ML model). | Integer | `0–1` |
| gender | Gender of the user  (based on the ML model). | String | `'M'` for male, `'F'` for female. |
| top_genre | User's preferred or inferred top genre. | String | Examples: `'Поп'`, `'Джаз'`, `'Chill'`; may be in non-English. |
| user_disliked_track_count | Total number of tracks disliked by the user. | Integer | Aggregate user-level metric. |
| user_liked_track_count | Total number of tracks liked by the user. | Integer | Aggregate user-level metric. |
| user_downloaded_track_count | Total number of tracks downloaded by the user. | Integer | Aggregate user-level metric. |

---

### **test.csv**
| Column | Description | Data Type | Notes |
|:--|:--|:--|:--|
| user_id | Unique identifier for the user. | Integer | All users exist in the training interactions; no cold-start users. |

> 🧭 **Time Range:** `2025-09-01` → `2025-09-15` (interactions period for evaluation)

---

### **Prediction Format**
The submission file must contain **recommendations for each user** in the test set, ranked by relevance or preference.

| Column | Description | Data Type |
|:--|:--|:--|
| id | Sequence of id . | Integer |
| user_id | User identifier (matches `test.csv`). | Integer |
| item_id | Recommended track identifier. | Integer |
| rank | Rank of the recommendation (starting from 1 to 50). | Integer |


```bash
kaggle competitions download -c hear-me-personalized-music-recommender
