# Try It

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

## 1.10. Find the percentage of rainfall that is less than 9.01 inches.

> The table below shows the amount, in inches, of annual rainfall in a sample of towns.

| Rainfall (Inches) | Frequency | Relative Frequency | Cumulative Relative Frequency |
| ----------------- | --------- | ------------------ | ----------------------------- |
| 2.95–4.97         | 6         | 0.12               | 0.12                          |
| 4.97–6.99         | 7         | 0.14               | 0.26                          |
| 6.99–9.01         | 15        | 0.30               | 0.56                          |
| 9.01–11.03        | 8         | 0.16               | 0.72                          |
| 11.03–13.05       | 9         | 0.18               | 0.90                          |
| 13.05–15.07       | 5         | 0.10               | 1.00                          |

Add the relative frequency of all rows till the one will rainfal capped at $9.01$ inches (third row).

$$
0.12 + 0.14 + 0.30 = 0.56 = 56\%
$$

## 1.11. Find the percentage of rainfall that is between 6.99 and 13.05 inches.

> The table below shows the amount, in inches, of annual rainfall in a sample of towns.

| Rainfall (Inches) | Frequency | Relative Frequency | Cumulative Relative Frequency |
| ----------------- | --------- | ------------------ | ----------------------------- |
| 2.95–4.97         | 6         | 0.12               | 0.12                          |
| 4.97–6.99         | 7         | 0.14               | 0.26                          |
| 6.99–9.01         | 15        | 0.30               | 0.56                          |
| 9.01–11.03        | 8         | 0.16               | 0.72                          |
| 11.03–13.05       | 9         | 0.18               | 0.90                          |
| 13.05–15.07       | 5         | 0.10               | 1.00                          |

Add the relative frequencies in rows three, four, and five.

$$
0.30 + 0.16 + 0.18 = 0.64 = 64\%
$$

## 1.12. Find the number of towns that have rainfall between 2.95 and 9.01 inches.

> The table below shows the amount, in inches, of annual rainfall in a sample of towns.

| Rainfall (Inches) | Frequency | Relative Frequency | Cumulative Relative Frequency |
| ----------------- | --------- | ------------------ | ----------------------------- |
| 2.95–4.97         | 6         | 0.12               | 0.12                          |
| 4.97–6.99         | 7         | 0.14               | 0.26                          |
| 6.99–9.01         | 15        | 0.30               | 0.56                          |
| 9.01–11.03        | 8         | 0.16               | 0.72                          |
| 11.03–13.05       | 9         | 0.18               | 0.90                          |
| 13.05–15.07       | 5         | 0.10               | 1.00                          |

Add the frequency of rows one through three.

$$
6 + 7 + 15 = 28
$$

## 1.13. What fraction of towns surveyed get between 11.03 and 13.05 inches of rainfall each year?

> The table below shows the amount, in inches, of annual rainfall in a sample of towns.

| Rainfall (Inches) | Frequency | Relative Frequency | Cumulative Relative Frequency |
| ----------------- | --------- | ------------------ | ----------------------------- |
| 2.95–4.97         | 6         | 0.12               | 0.12                          |
| 4.97–6.99         | 7         | 0.14               | 0.26                          |
| 6.99–9.01         | 15        | 0.30               | 0.56                          |
| 9.01–11.03        | 8         | 0.16               | 0.72                          |
| 11.03–13.05       | 9         | 0.18               | 0.90                          |
| 13.05–15.07       | 5         | 0.10               | 1.00                          |

$$
\begin{aligned}
&\text{Total frequency} = 6 + 7 + 15 + 8 + 9 + 5 = 50 \\[4pt]
&\text{Relative frequency}_{(11.05-13.05)} = \frac{9}{50}
\end{aligned}
$$

## 1.14. Answer the following questions.

> The table contains the total number of fatal motor vehicle traffic crashes in the United States for the period from 1994 to 2011.

| Year      | Total Number of Crashes |
| --------- | ----------------------- |
| 1994      | 36,254                  |
| 1995      | 37,241                  |
| 1996      | 37,494                  |
| 1997      | 37,324                  |
| 1998      | 37,107                  |
| 1999      | 37,140                  |
| 2000      | 37,526                  |
| 2001      | 37,862                  |
| 2002      | 38,491                  |
| 2003      | 38,477                  |
| 2004      | 38,444                  |
| 2005      | 39,252                  |
| 2006      | 38,648                  |
| 2007      | 37,435                  |
| 2008      | 34,172                  |
| 2009      | 30,862                  |
| 2010      | 30,296                  |
| 2011      | 29,757                  |
| **Total** | 653,782                 |

### 1.14.1. What is the frequency of deaths measured from 2000 through 2004?

$$
\text{Frequency}_{2000-2004} = 37526 + 37862 + 38491 + 38477 + 38444 = 190800
$$

### 1.14.2. What percentage of deaths occurred after 2006?

$$
\begin{aligned}
&\text{Frequency}_{2007-2011} = 37435 + 34172 + 30862 + 30296 + 29757 = 162522 \\[4pt]
&\text{Percentage}_{2007-2011} = \frac{162522}{653782} \times 100\% = 24.86\%
\end{aligned}
$$

### 1.14.3. What is the relative frequency of deaths that occurred in 2000 or before?

$$
\begin{aligned}
&\text{Frequency}_{1994-2000} = 36254 + 37241 + 37494 + 37324 + 37107 + 37140 + 37526 = 260086 \\[4pt]
&\text{Relative frequency}_{1994-2000} = \frac{260086}{653782} = 0.3978
\end{aligned}
$$

### 1.14.4. What is the percentage of deaths that occurred in 2011?

$$
\text{Percentage}_{2011} = \frac{29757}{653782} \times 100\% = 4.55\%
$$

### 1.14.5. What is the cumulative relative frequency for 2006? Explain what this number tells you about the data.

| Year | Frequency | Relative frequency | Cumulative relative frequency |
| ---- | --------- | ------------------ | ----------------------------- |
| 1994 | 36254     | 0.0555             | 0.0555                        |
| 1995 | 37241     | 0.0570             | 0.1125                        |
| 1996 | 37494     | 0.0573             | 0.1698                        |
| 1997 | 37324     | 0.0571             | 0.2269                        |
| 1998 | 37107     | 0.0568             | 0.2837                        |
| 1999 | 37140     | 0.0568             | 0.3405                        |
| 2000 | 37526     | 0.0574             | 0.3979                        |
| 2001 | 37862     | 0.0579             | 0.4558                        |
| 2002 | 38491     | 0.0589             | 0.5147                        |
| 2003 | 38477     | 0.0589             | 0.5736                        |
| 2004 | 38444     | 0.0588             | 0.6324                        |
| 2005 | 39252     | 0.0600             | 0.6924                        |
| 2006 | 38648     | 0.0591             | 0.7515                        |

The cumulative relative frequency for 2006 is $0.7515$. This tells us that more than $75\%$ of all the fatal crashes (till 2011) occurred before 2007.

## 1.15. Design a study to test the response time of drivers while texting and while driving only.

> You are concerned about the effects of texting on driving performance. How many seconds does it take for a driver to respond when a leading car hits the brakes?

The researcher invites 10 drivers of age 20 to 30, 10 drivers of age 30 to 40, 10 drivers of age 40 to 50, and 10 drivers of age 50 to 60. Each subject is told to sit in the driver's seat of a dummy car which is parked behind another dummy car. They are told to hit the brakes as soon as they see the car in front press brakes.

The participants are required to text while driving for three trials and focus on driving only for three trials. The participants are assigned at random to text while driving during the first three trials or during the last three trials. For each trial, the time starting from when the leading car hits brake till when the subject hits the brake is recorded.

### 1.15.1. Describe the explanatory and response variables in this study?

The explanatory variable is the driver's current focus, and the response variable is the time it takes to hit the brake when the leading car hits the brake.

### 1.15.2. What are the treatments?

There are two treatments: focus on texting while driving and focus on driving only.

### 1.15.3. What should you consider when selecting participants?

Since human response time degrades with age (young people have a much faster reaction time), it is necessary to consider all age groups. So a stratified sample based on age groups should be considered, and if possible, there should be an equal number of male and female drivers in each age group.

### 1.15.4. Your research partner wants to divide participants randomly into two groups: one to drive without distraction and one to text and driving simultaneously. Is this a good idea? Why or why not?

No, this is not a good idea. The human reaction time is vary random. Some people have a very fast reaction time even when texting and some people are just slow to react. In order to remove the variability of an individual's reaction time as a lurking variable, each participant should be required to act in both cases: drive without distractioon and text while driving.

### 1.15.5. Identify any lurking variables that could interfere with this study.

The human reaction time has a lot of variability and the observed change in the response variable could simply be because the individual just had a very slow or fast reaction time. It is therefore a lurking variable.

### 1.15.6. How can blinding be used in this study?

The participants can not be blinded since they are aware whether they are texting while driving or driving only. However, the researcher who is timing the response time can be blinded. That reseacher will not know whether the participant is texting while driving or driving only.

## 1.16. Describe the unethical behavior, if any, in each example and describe how it could impact the reliability of the resulting data. Explain how the problem should be corrected.

> A study is commissioned to determine the favorite brand of fruit juice among teens in California.

### 1.16.1. The survey is commissioned by the seller of a popular brand of apple juice.

The survey results are prone to be biased in favor of that brand of apple juice. This could happen in many ways; for example, the brand might lobby the researchers to select only those areas where they have done good marketing to ensure that the participants like that apple juice brand, or the brand might require the researchers to highlight the statistics in such a way that favors that brand.

If you do need to get sponsored by a juice brand, it should be made very clear in the agreement that the survey will be neutral and random, and that the payment made is not to make that brand look good. The survey will still be random and the statistics will be fair.

### 1.16.2. There are only two types of juice included in the study: apple juice and cranberry juice.

The survey results will be horribly misleading. This is because when only two juice categories are considered, one of them must be a winner, and the relative frequencies would be meaningless, since the participants are forced to choose one of the two. To fix this, more juice types needs to be added to the survey, so the statistics reflect true popularity.

### 1.16.3. Researchers allow participants to see the brand of juice as samples are poured for a taste test.

The survey is not blinded, and thus the data will be biased. Simply seeing the brand of juice without first tasting it could create an anchor bias. The solution to this is to make the survey double-blinded, where neither the researcher giving taste samples nor the participants know which brand is being poured.

### 1.16.4. Twenty-five percent of participants prefer Brand X, 33% prefer Brand Y, and 42% have no preference between the two brands. Brand X references the study in a commerical saying "Most teens like Brand X as much as or more than Brand Y."

This is clearly incorrect and a fraud. This can be fixed by filing a lawsuit against the Brand X for false advertisement.
