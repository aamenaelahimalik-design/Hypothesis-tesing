📊 Hypothesis Testing on Cookie Cats Dataset

This repository contains Python code and statistical analysis performed on the Cookie Cats mobile game dataset. The goal is to demonstrate T-Test, Z-Test, and A/B Testing concepts using real data.

📁 Dataset

The dataset used in this analysis is cookie_cats.csv.zip and contains:

Column	Description
userid	Unique player ID
version	A/B test groups: gate_30 or gate_40
sum_gamerounds	Total rounds played
retention_1	Player returned next day (True/False)
retention_7	Player returned after 7 days

Total rows: 90,189

🧼 Data Cleaning

✔ Checked duplicates
✔ Checked missing values
✔ Dataset has no missing or duplicate records

📘 Statistical Tests Performed
1️⃣ One-Sample T-Test

Used when:

Sample size < 30

Population SD unknown

Data is normally distributed

data = df["sum_gamerounds"]
t_stat, p_value = stats.ttest_1samp(data, 50)


Result:

T-statistic: 2.88

p-value: 0.0039
➡ Reject 
𝐻
0
H
0
	​

 — mean is significantly different from 50.

2️⃣ One-Sample Z-Test

Used when:

Sample size > 30

Population SD known / large sample

z_stat, p_value = ztest(data, value=50)


Result:

Z-statistic: 2.88

p-value: 0.0039
➡ Result same as t-test due to large sample size.

3️⃣ Two-Sample T-Test (A/B Test)

Comparing gate_30 vs gate_40:

group_a = df[df["version"] == "gate_30"]["sum_gamerounds"]
group_b = df[df["version"] == "gate_40"]["sum_gamerounds"]
stats.ttest_ind(group_a, group_b)


Result:

t = 0.89

p = 0.372
➡ No significant difference between the two groups.
