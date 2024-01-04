# Distributions_from_U(0-1)

### Outline:
In this project, I sampled from distributions using only stochastic values realized from a continuous uniform distribution. This helped me review the purpose of so-called "name brand" distributions while understanding the relationship between them. It also allowed me to get more experience with NumPy and Matplotlib.

Future plans for this project include adding more distributions. 

### Methodology:
1. For the <b> Bernoulli , Binomial, Geometric, Negative Binomial, Discrete Uniform, and Multinomial </b> distributions, I cut the number line between 0 and 1 into zones. For example, in a Bernoulli distribution with p = 0.7 there is a 70% chance of success. This is equivalent to the chance of realizing a U(0,1) under 0.7. In this case, values under 0.7 fall into the "success" zone, while values above 0.7 fall into the "fail" zone. Similarly, the uniform distribution has (b-a+1) zones of equal length, and the multinomial has (dim|<b>x</b>|) zones with their respective lengths totaling 1. 
2. For the <b> Exponential, Erlang, Weibull, Pareto1, and Cauchy </b> distributions, I set the CDF equal to the U(0,1) value and solved for x.
3. For the <b> Poisson </b> distribution, I summed up exponential wait times until they exceeded 1 and plotted the number of events that occurred before the sum reached 1. 
4. For the <b> Standard Normal </b> distribution, I used the CLT and plotted sample means shifting by the overall mean and scaling by the overall sample varience.
