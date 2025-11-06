# IMU Yoga Repetition Quality — Binary Classification

## Introduction

**Adilkhan** and **Darkhan** are young researchers who decided to explore how technology can improve physical training.  
They equipped participants with **IMU sensors** and recorded multiple yoga pose repetitions.  
Each attempt was carefully labeled as either `correct` or `incorrect`.

Their goal is simple: to train a model that can automatically recognize whether a repetition is done properly.  
Now, it is your mission to continue their work and build an accurate classifier to evaluate unseen yoga repetitions.

## Formal Problem Statement

You are given three CSV files:
- `X_train.csv`: Training set with IMU data segments.
- `y_train.csv`: Labels for the training set (`0` = incorrect, `1` = correct).
- `X_test.csv`: Test set with IMU data segments, without labels. Your model must predict the label for each test example.

**Dataset links:**
- **X_train.csv**: https://drive.google.com/file/d/1wMuHEYsXKt3_IhgAUiUcpPvuctLM9jGL/view?usp=drive_link
- **y_train.csv**: https://drive.google.com/file/d/1F3mUFseTH3mi6bkY13flJTAK4tGTMIzm/view?usp=drive_link
- **X_test.csv**: https://drive.google.com/file/d/1OdlLTsLPyLa7JUmhQcRtP9ixlYE82H7k/view?usp=drive_link

## Input

### Features (X)

Each repetition is represented by time series of IMU readings sampled at **200 Hz**. The following sensor signals are provided:
- `ax`, `ay`, `az` — Linear acceleration (g) along the sensor’s X, Y, Z axes.
- `wx`, `wy`, `wz` — Angular velocity (deg/s) around the sensor’s X, Y, Z axes.

### Labels (y)
- `0` — repetition performed incorrectly.
- `1` — repetition performed correctly.

Each `id` corresponds to one yoga repetition.

## Output

Participants must submit only a CSV file named **solution.csv**, with the following format:

```csv
id,label
0,1
1,0
2,1
...
```

**Important:** Submit only the `solution.csv` file. Source code is not required. The order of `id` values in `solution.csv` must strictly follow the order in `test.csv`, starting from `0` up to the highest ID.

## Evaluation

- Your predictions will be evaluated using the **Accuracy** score.

## Example

**Input (`X_test.csv`):**
```csv
id,ax,ay,az,wx,wy,wz
0,0.12,0.04,0.98,-1.2,0.3,0.1
1,0.01,0.15,1.02,0.8,-0.5,0.0
2,-0.10,0.20,0.95,0.7,0.1,-0.2
```

**Your Output (`solution.csv`):**
```csv
id,label
0,1
1,0
2,1
```
