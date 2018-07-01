[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```python
import scipy.stats
#Set up variables for male height distribution
mht_mu = 178
mht_sigma = 7.7
#Construct distribution
mht_dist = scipy.stats.norm(loc = mht_mu, scale = mht_sigma)
#Qualifying percentage: % 6'1" or below less % 5'10" or below
#Inclusive/exclusive range not specified, defaulted to simplest
bman_perc = (mht_dist.cdf((6*12 + 1)*2.54) - mht_dist.cdf((5*12 + 10)*2.54)) * 100
print(str(bman_perc) + ' percent of the US male population meets the height requiremenets for the Blue Man Group') 
```
