# Distributions_from_U(0-1)

### Outline:
In this project, I sampled from distributions using only stochastic values realized from a continuous uniform distribution. This helped me review the purpose of so-called "name brand" distributions while understanding the relationship between them. It also allowed me to get more experience with NumPy and Matplotlib.

Future plans include exploring the CDF approach in more dimensions. This would allow dependent simulations from multiple distributions concurrently. Similarly, it would allow many numbers from a single distribution to be sampled concurrently, albeit in a predetermined way.

### Methodology:
1. For the "slow methods" <b> Bernoulli, Binomial, Geometric, Negative Binomial, Discrete Uniform, and Multinomial </b> distributions, I cut the number line between 0 and 1 into zones. For example, in a Bernoulli distribution with p = 0.7, there is a 70% chance of success. This is equivalent to the chance of realizing a U(0,1) under 0.7. In this case, values under 0.7 fall into the "success" zone, while values above 0.7 fall into the "fail" zone. Similarly, the uniform distribution has (b-a+1) zones of equal length, and the multinomial has (dim|<b>x</b>|) zones with their respective lengths totaling 1. This process was O(n), O(n*x), O(n*(a-b+1)), and O(dim|<b>x</b>| * n).
2. For the "fast methods," I stored values of the CDF in an array and used binary search to find the x value from the realization. O(n*log(n))
3. For the <b> Exponential, Erlang, Weibull, Pareto1, and Cauchy </b> distributions, I set the CDF equal to the U(0,1) value and solved for x.
4. For the "slow method" <b> Poisson </b> distribution, I summed up exponential wait times until they exceeded 1 and plotted the number of events that occurred before the sum reached 1. This process was Omega(n) and Theta(lambda). 
5. For the <b> Standard Normal </b> distribution, I used the CLT and plotted sample means shifting by the overall mean and scaling by the overall sample variance.

### Conclusion
#### Many distributions can be sampled from by a single U(0,1) number.

Aside from a few exceptions, the best method was using the CDF.
Steps:
   1. Plot the CDF.
   2. Sample a number z from U(0,1).
   3. Draw line at y = z
   4. For continuous distributions, the result is the x value at the intersection.
   5. For discrete distributions, the result is the next x value in the support after the intersection.
   
#### Sometimes, knowlegde of statistics can increase efficiency of programs for simulations and random number generation.

### Use Cases and Examples
Many IID events can be simulated using only one stochastic U(0,1) value.
This provides a very efficient way for computers to sample from the whole gamut of distributions using the simplest form of RNG.
For example, the amount of heads in 1,000 coin flips can be determined with one random number and binary search, instead of 1,000 random numbers being compared to p and summed up.
