BIST8130_hw2
================

# Question 1

## Part b

What is the probability that at least 40 of these individuals will have
at least one dental checkup?

``` r
#assigning variables for number of trials, probability of success, and probability of failure
n = 56
p = 0.73
q_1 = 0.27
```

``` r
#probability of x less than 40, P(X < 40)
P_X_less_40 = pbinom(39, n, p)
```

``` r
#probability of x greater than or equal to 40, P(X >= 40)
P_X_ge_40 = 1 - P_X_less_40
```

The probability that at least 40 of these individuals will have at least
one dental checkup is 0.6678734.

## Part d

How many individuals do you expect to have at least one dental checkup?

``` r
#calculating the number of individuals expected to have at least one dental checkup
expected_number = n * p
expected_rounded = floor(expected_number)
```

The expected number of individuals to have at least one dental checkup
is 40.88 or 40 individuals.

## Part e

What is the standard deviation of the number of individuals who will
have at least one dental checkup?

``` r
#calculating the standard deviation of individuals who will have at least one dental checkup
sd_e = sqrt(n * p * q_1)
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
