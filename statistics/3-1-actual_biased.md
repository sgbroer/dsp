[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

The code below generates the following plot of the actual vs biased distributions of children per family:
![Biased v Actual Distributions](/img/biased_v_actual.png)  
As is clear on the chart, families with no children are excluded entirely, while families with more children are majorly overrepresented.
This is shown also by the difference in means; the biased mean of ~2.4 is over double actual mean ~1. 

```python
import numpy as np
import nsfg
import thinkstats2
import thinkplot

#Read in data
resp = nsfg.ReadFemResp()
#Construct Pmf of number of children/family
actual_pmf = thinkstats2.Pmf(resp.numkdhh, label = 'actual')
#Define function for biasing distribution
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    print(pmf.Items())
    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
#Construct Pmf of reports from children
biased_pmf = BiasPmf(actual_pmf, label='observed')
#Plot Pmfs
thinkplot.PrePlot(2)
thinkplot.pmfs([actual_pmf, biased_pmf])
thinkplot.show(xlabel = 'Number of Children', ylabel = 'PMF')
#Compute means
print(actual_pmf.Mean())
print(biased_pmf.Mean())
```
