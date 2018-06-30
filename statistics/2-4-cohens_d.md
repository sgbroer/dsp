[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)


From the output of the code below, first babies appear to be ~.09 of a standard deviation lighter than children not born first.
While it is a larger effect than the one seen for pregnancy length, it is still under 1/10 a deviation and so quite small overall.

'''python
import numpy as np
import nsfg

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

def Cohens_D(group1, group2):
    mean1 = group1.mean()
    mean2 = group2.mean()
    
    var1 = group1.var()
    var2 = group2.var()
    
    n1 = len(group1)
    n2 = len(group2)
    
    std_pooled = np.sqrt((var1 * n1 + var2 * n2) / (n1 + n2))
    
    D = (mean1 - mean2) / std_pooled
    return D

print(Cohens_D(firsts.totalwgt_lb, others.totalwgt_lb))
'''
