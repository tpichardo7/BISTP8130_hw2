BIST8130_hw2
================

# Question 1

## Part b

What is the probability that at least 40 of these individuals will have
at least one dental checkup?

``` r
#assigning variables for number of trials, probability of success, and probability of failure
n_1 = 56
p_1 = 0.73
q_1 = 0.27
```

``` r
#probability of x less than 40, P(X < 40)
P_X_less_40 = pbinom(39, n_1, p_1)
```

``` r
#probability of x greater than or equal to 40, P(X >= 40)
P_X_ge_40 = 1 - P_X_less_40
```

The probability that at least 40 of these individuals will have at least
one dental checkup is 0.6678734.

## Part c

``` r
#calculating mean and standard deviation for normal approximation
mean_1 = n_1 * p_1
sd_1c = sqrt (n_1 * p_1 * q_1)
```

``` r
#z-scores for continuity correction
z_39.5 = (39.5 - mean_1) / sd_1c
z_40.5 = (40.5 - mean_1) / sd_1c
```

``` r
#approximation for exactly 40 individuals that will have at least one dental checkup
P_X_40_approx = pnorm(z_40.5) - pnorm(z_39.5)
```

``` r
#appriximation for at least 40 individuals that will have at least one dental
P_X_ge40_approx = 1 - pnorm(z_39.5)
```

## Part d

How many individuals do you expect to have at least one dental checkup?

``` r
#calculating the number of individuals expected to have at least one dental checkup
expected_number = n_1 * p_1
expected_rounded = floor(expected_number)
```

The expected number of individuals to have at least one dental checkup
is 40.88 or 40 individuals.

## Part e

What is the standard deviation of the number of individuals who will
have at least one dental checkup?

``` r
#calculating the standard deviation of individuals who will have at least one dental checkup
sd_1e = sqrt(n_1 * p_1 * q_1)
```

The standard deviation of the number of individuals who will have at
least one dental checkup is 3.3222884.

# Question 2

## Part a

What is the probability of having fewer than 3 tornadoes in the United
States next year?

``` r
#parameters for average number of tornadoes and threshold for fewer than 3 tornadoes
lambda = 6
q_2a = 2
```

``` r
#calculating the probability of having fewer than 3 tornadoes in the United States next year
P_less_3 = ppois(q_2a, lambda)
```

## Part b

What is the probability of having exactly 3 tornadoes in the United
States next year?

``` r
#number of tornadoes
x = 3
```

``` r
#calculating the probability of having exactly 3 tornadoes in the United States next year
P_exact_3 = dpois(x, lambda)
```

The probability of having exactly 3 tornadoes in the United States next
year is 0.0892351.

## Part c

What is the probability of having more than 3 tornadoes in the United
States?

``` r
#threshold for more than 3 tornadoes
q_2c = 3
```

``` r
#calculating the probability of having more than 3 tornadoes in the United States
P_greater_3 = 1 - ppois(q_2c, lambda)
```

The probability of having more than 3 tornadoes in the United States is
0.8487961.

# Question 3

## Part a

What is the probability that a randomly selected American male between
20 and 29 years old has a systolic blood pressure above 137.0?

``` r
#parameters for population mean, population standard deviation, and systolic blood pressure threshold
mean_3 = 128.0
sd_3 = 10.2
sbp_3a = 137.0
```

``` r
z_3a = (sbp_3a - mean_3) / sd_3
```

``` r
#calculating the probability of systolic blood pressure > 137.0
P_above_137 = 1 - pnorm(z_3a)
```

The probability that a randomly selected American male between 20 and 29
years old has a systolic blood pressure above 137.0 is 0.188793.

## Part b

What is the probability that the sample mean for blood pressure of 50
males between 20 and 29 years old will be less than 125.0?

``` r
#sample size and sample mean
n_3b = 50
smean_3b = 125.0
```

``` r
#calculating standard error of the mean
se_3b = sd_3 / sqrt(n_3b)
```

``` r
#calculating z-score
zscore_3b = (smean_3b - mean_3) / se_3b
```

``` r
#calculating the probability of sample mean < 125.0
P_smean_less_125 = pnorm(zscore_3b)
```

The probability that the sample mean for blood pressure of 50 males
between 20 and 29 years old will be less than 125.0 is 0.0187753.

## Part c

What is the 90th percentile of the sampling distribution of the sample
mean X for a sample size of 40?

``` r
#sample size
n_3c = 40
```

``` r
#calculating standard error of the mean
se_3c = sd_3 / sqrt(n_3c)
```

``` r
#calculating the 90th percentile
percentile_90 = qnorm(0.90, mean_3, se_3c)
```

The 90th percentile of the sampling distribution of the sample size mean
X for a sample size of 40 is 130.0668372.

# Question 4

## Part a

Compute the 95% confidence interval for the population mean pulse rate
of young females suffering from fibromyalgia.

``` r
#given data
n_4 = 40
smean_4 = 80
sd_4 = 10
```

``` r
#calculating standard error of the mean
se_4a = sd_4 / sqrt(n_4)
```

``` r
#calculating the t-score for the 95% confidence interval
alpha_4a = 0.05
tscore_4a = qt(1 - alpha_4a / 2, df = n_4 - 1)
```

``` r
#calculating margin of error
margin_error_4a = tscore_4a * se_4a
```

``` r
#calculating confidence interval
CI_lower_4a = smean_4 - margin_error_4a
CI_upper_4a = smean_4 + margin_error_4a
```

The 95% confidence interval for the population mean pulse rate of young
females suffering from fibromyalgia is 76.8018448 to 83.1981552.

## Part b

We are 95% confident that the true population mean lies between the
lower limit of 76.8018448 and the upper limit of 83.1981552 of the
interval.

## Part c

Conduct the hypothesis testing and interpret the results.

``` r
#given data
null_mean = 70
alpha_4c = 0.01
```

``` r
#calculating standard error
se_4c = sd_4 / sqrt(n_4)
```

``` r
#calculating t-statistic
tstat_4c = (smean_4 - null_mean) / se_4c
```

``` r
#calculating critical t-value
tcritical = qt(1 - alpha_4c / 2, df = n_4 - 1)
```

``` r
#calculating p-value
pvalue_4c = 2 * (1 - pt(abs(tstat_4c), df = n_4 - 1))
```

The p-value is 1.8350062^{-7}.

Since the p-value of 1.8350062^{-7} is greater than the 0.01
significance level, we do not reject the null hypothesis as this
indicates weak evidence against the null. The p-value indicates that the
data would occur 43.40% of the time if the null is true, so not enough
evidence to reject.
