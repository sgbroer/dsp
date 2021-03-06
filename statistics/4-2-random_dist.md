[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

The PMF distribution from the code below doesn't give us much information:  
![random.random() PMF](/img/random_pmf.png)  
However, the CDF distribution looks to be linear suggesting random.random() does indeed generate random numbers:  
![random.random() CDF](/img/random_cdf.png)   

```python
import random
import thinkstats2
import thinkplot


rand_nums = []
i = 0
while i < 1000:
    rand_nums.append(random.random())
    i += 1

rand_pmf = thinkstats2.Pmf(rand_nums, label = '# generated by random.random()')
rand_cdf = thinkstats2.Cdf(rand_nums, label = '# generated by random.random()')

thinkplot.Pmf(rand_pmf)
thinkplot.Show(xlabel = 'number', 
               ylabel = 'PMF', 
              ylim = [.0009, .0011])

thinkplot.Cdf(rand_cdf)
thinkplot.Show(xlabel = 'number', ylabel = 'CDF')
```
