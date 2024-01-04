# Distributions_from_U(0-1)

### Outline:
In this project, I sampled from distributions using only stochastic values realized from a continuous uniform distribution. This helped me review the purpose of so-called "name brand" distributions while understanding the relationship between them. It also allowed me to get more experience with NumPy and Matplotlib.

Future plans include exploring the CDF approach in more dimensions.

### Methodology:
1. For the "slow method" <b> Bernoulli , Binomial, Geometric, Negative Binomial, Discrete Uniform, and Multinomial </b> distributions, I cut the number line between 0 and 1 into zones. For example, in a Bernoulli distribution with p = 0.7 there is a 70% chance of success. This is equivalent to the chance of realizing a U(0,1) under 0.7. In this case, values under 0.7 fall into the "success" zone, while values above 0.7 fall into the "fail" zone. Similarly, the uniform distribution has (b-a+1) zones of equal length, and the multinomial has (dim|<b>x</b>|) zones with their respective lengths totaling 1 this processs was O(n), O(n*(a-b+1)) and O(dim|<b>x</b>| * n)
2. For the <b> Exponential, Erlang, Weibull, Pareto1, and Cauchy </b> distributions, I set the CDF equal to the U(0,1) value and solved for x.
3. For the "slow method" <b> Poisson </b> distribution, I summed up exponential wait times until they exceeded 1 and plotted the number of events that occurred before the sum reached 1. This process was Omega(n) and theta(lambda). 
4. For the <b> Standard Normal </b> distribution, I used the CLT and plotted sample means shifting by the overall mean and scaling by the overall sample varience.

### Conclusion
Many distributions can be sampled from by a single U(0,1) number.

Aside from a few exceptions the best method was using the CDF.
1. Plot the CDF
2. Sample a number z from U(0,1)
3. Draw line at y = z
4. For continuous distributions, the result is the x value at the intersection
5. For discrete distributions, the result is the next x value in the support after the intersection
   
Sometimes there are even better ways of solving problems than asking the computer to repeat simple processes many times. 

### Use Cases
Many iid events can be simulated using only one stochastic U(0,1) value.
For example, millions of coinflips can be simulated with just one number, insted of millions.
