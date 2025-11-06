# Overview

🎶 Welcome to the Missing Fundamental Puzzle! 

Imagine someone playing a beautiful C4 on a violin…
But then—we delete the actual pitch. Poof! 🪄 Gone! 

Yet somehow, your brain still hears C4.   

So here’s the big question:
Can machines hear a musical note that isn’t there? 

In this challenge, every audio clip is a pitch illusion—the true note is missing in action, and only its spectral echoes remain. Despite this, the human brain can still recover the correct pitch by analyzing the spacing and pattern of the remaining harmonics. 

🎯 Your task: Build a model that classifies the original musical note (e.g., C4, G#5) from the given audio—mimicking the brain’s ability to reconstruct pitch from harmonic structure. 

Think you can teach a machine to listen like a human?
Then dive in—and hear the unheard! 🎼🎶🎵

# Description
This is a single-label multiclass audio classification task. 

**Input:** 

Each sample consists of a mono audio waveform in 16-bit PCM WAV format, sampled at 22050 Hz. The duration of each file is variable but typically between 1 and 4 seconds. The audio has been preprocessed and some of the frequencies have been removed from the signal. 

**Target:**

For each audio file, the target is a discrete musical note label representing the original pitch. The label set comprises 61 distinct classes, corresponding to all MIDI notes that appear in the data. 

**Objective:**

Given the modified audio, predict the true underlying note that was originally played. The model must infer pitch from the spectral and temporal structure of the remaining harmonics, without access to the fundamental frequency or other removed harmonics. 

Submissions are evaluated using **standard classification accuracy**:

$$
\text{Accuracy} = \frac{\text{Number of correct predictions}}{\text{Total number of examples}}
$$

🎯 **The higher the score, the better your recommendations!**

## Submission File
For each audio path in the test set, you must predict a encrypted notes pitch label. The file should contain a header and have the following format:

    Path, Pitch_ID
    path/samle1.wav, 0
    path/samle2.wav,1
    path/samle3.wav,2
    etc.

# Dataset description

🎵 Dataset: TinySOL-MF — Missing Fundamental Edition 

This dataset is a specially curated and preprocessed variant of the [TinySOL](https://www.kaggle.com/datasets/thedevastator/tinysol-isolated-musical-notes-from-14-musical-i) dataset, designed to challenge machine learning models with a core phenomenon in auditory perception: pitch perception in the absence of the fundamental frequency. 

🔍 What is the "Missing Fundamental"? 

When a musical note is played, its sound contains a fundamental frequency (f₀) and a series of harmonics (integer multiples of f₀). Remarkably, even if the fundamental frequency is removed, the human brain can still perceive the correct pitch by analyzing the spacing of the remaining harmonics. This psychoacoustic effect is known as the missing fundamental. 

The goal of this competition is to build models that mimic human auditory intelligence—classifying musical notes without relying on the fundamental frequency. 

📁 Dataset Structure 

- Total files: 2,913 isolated musical notes  
- Instruments: 14 orchestral instruments (strings, woodwinds, brass, and keyboard)  
- Split:  
    - Train: 2,330 files (80%)  
    - Test: 583 files (20%)
- Format: 16-bit PCM WAV, mono, 22.05 kHz sampling rate 
- Duration: ~2–4 seconds per note (sustained tones with natural decay)

Every audio file in this dataset has been algorithmically modified.

## Files

*   **train.csv** - the training set
*   **test.csv** - the test set
*   **sample_submission.csv** - a sample submission file in the correct format


## Columns

*   `Path` - path to the audio file
*   `Pitch_ID` - id of a corresponding pitch


```bash
kaggle competitions download -c missing-fundamental-puzzle
