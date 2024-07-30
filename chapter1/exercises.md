# Exercises

## 1.1. Determine what the key terms refer to in the following study.

> We want to know the average (mean) amount of money spent on school uniforms each year by families with children at Knoll Academy. We randomly survey 100 families with children in the school. Three of the families spent $65, $75, and $95, respectively.

- The **population** is the entirety of the families with children at Knoll Academy.
- The **sample** is the collection of the randomly selected 100 families with children in the school.
- The **parameter** is the average amount of money spent by this population on school uniforms each year.
- The **statistic** is the average amount of money spent by this sample on school uniforms each year.
- The **variable** is the amount of money spent on schools uniforms each year.
- The **data** are the monetary values collected for this variable.

## 1.2. What type of data is this?

> The data are the number of machines in a gym. You sample five gyms. One gym has 12 machines, one gym has 15 machines, one gym has ten machines, one gym has 22 machines, and the other gym has 20 machines.

This is a quantitative discrete data, since the data are numbers produced by counting.

## 1.3. What type of data is this?

> The data are the areas of lawns in square feet. You sample five houses. The areas of the lawns are 144 sq. feet, 160 sq. feet, 190 sq. feet, 180 sq. feet, and 210 sq. feet.

This is a quantitative continuous data, since the data are numbers produced by measuring. Although, these values look discrete, area is a continuous variable (unless we limit ourself to areas rounded off to the nearest integer).

## 1.4. What type of data is this?

> The data are the colors of houses. You sample five houses. The colors of the houses are white, yellow, white, red, and white.

This is a qualitative data, since the data is categorical in nature.

## 1.5. Determine the correct data type (quantitative or qualitative) for the number of cars in a parking lot. Indicate whether quantitative data are continuous or discrete.

The number of cars in a parking lot is a quantitative discrete data, since the data are numbers produced by counting.

## 1.6. What type of data does this graph show?

> The registrar at State University keeps records of the number of credit hours students complete each semester. The data he collects are summarized in the histogram. The class boundaries are 10 to less than 13, 13 to less than 16, 16 to less than 19, 19 to less than 22, and 22 to less than 25.

<img src="data/1-4.png" width=512>

The number of credit hours students complete each semester is a quantitative discrete data, since the data are numbers produced by counting.

## 1.7. You are going to use the random number generator to generate different types of samples from the data.

> This table displays six sets of quiz scores (each quiz counts 10 points) for an elementary statistics class.

| #1  | #2  | #3  | #4  | #5  | #6  |
| --- | --- | --- | --- | --- | --- |
| 5   | 7   | 10  | 9   | 8   | 3   |
| 10  | 5   | 9   | 8   | 7   | 6   |
| 9   | 10  | 8   | 6   | 7   | 9   |
| 9   | 10  | 10  | 9   | 8   | 9   |
| 7   | 8   | 9   | 5   | 7   | 4   |
| 9   | 9   | 9   | 10  | 8   | 7   |
| 7   | 7   | 10  | 9   | 8   | 8   |
| 8   | 8   | 9   | 10  | 8   | 8   |
| 9   | 7   | 8   | 7   | 7   | 8   |
| 8   | 8   | 10  | 9   | 8   | 7   |

```py
scores = np.array([
  5, 7, 10, 9, 8, 3,
  10, 5, 9, 8, 7, 6,
  9, 10, 8, 6, 7, 9,
  9, 10, 10, 9, 8, 9,
  7, 8, 9, 5, 7, 4,
  9, 9, 9, 10, 8, 7,
  7, 7, 10, 9, 8, 8,
  8, 8, 9, 10, 8, 8,
  9, 7, 8, 7, 7, 8,
  8, 8, 10, 9, 8, 7
])

categories = np.array([
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6,
  1, 2, 3, 4, 5, 6
])
```

### 1.7.1. Create a stratified sample by column. Pick three quiz scores randomly from each column.

```py
sss = StratifiedShuffleSplit(n_splits=1, train_size=18, random_state=42)
for sample_index, nonsample_index in sss.split(scores, categories):
    sample, sample_categories = scores[sample_index], categories[sample_index]
print(sample)
# [ 7  8  7  5  7 10  9  8  9  9  8  8 10  7  9  7 10 10]
```

### 1.7.2. Create a cluster sample by picking two of the columns. Use the column numbers: one through six.

```py
clusters = np.random.choice([1, 2, 3, 4, 5, 6], size=2, replace=False)
indices = np.isin(categories, clusters)
sample = scores[indices]
print(sample)
# [ 7 10  5  9 10  8 10 10  8  9  9  9  7 10  8  9  7  8  8 10]
```

### 1.7.3. Create a simple random sample of 15 quiz scores.

```py
sample = np.random.choice(scores, size=15, replace=False)
print(sample)
# [ 9  9  8  9  7  5  9  8  7  7  4  8  5 10  8]
```

### 1.7.4. Create a systematic sample of 12 quiz scores. Use the numbering one thrugh 60.

```py
sample = scores[:60]
print(sample)
# [ 5  7 10  9  8  3 10  5  9  8  7  6  9 10  8  6  7  9  9 10 10  9  8  9
#  7  8  9  5  7  4  9  9  9 10  8  7  7  7 10  9  8  8  8  8  9 10  8  8
#  9  7  8  7  7  8  8  8 10  9  8  7]
```

## 1.8. Determine the type of sampling used (simple random, stratified, systematic, cluster, or convenience).

> A high schoool principal polls 50 freshmen, 50 sophomores, 50 juniors, and 50 seniors regarding policy changes for after school activities.

This is stratified sampling, since the sample contain the same strata distribution as existent in the overall population (all high school students, assuming there are equal number of freshmen, sophomores, juniors, and seniors in the high schoool).

## 1.9. Do you think that this sample is representative of (or is characteristic of) the entire 20,000 listener population?

> A local radio station has a fan base of 20,000 listeners. The station wants to know if its audience would prefer more music or more talk shows. Asking all 20,000 listeners is an almost impossible task.
>
> The station uses convenience sampling and surveys the first 200 people they meet at one of the station's music concert events. 24 people said they had prefer more talk shows, and 176 said they had prefer more music.

No, this sample is biased, since it surveyed people at a music concert. Being present in a music concert already shows that the individual prefers music.
