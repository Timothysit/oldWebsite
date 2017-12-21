---
title: "Finding Spikes"
date: 2017-11-09
---

# Finding Spikes 

Spikes, or action potentials, is the key mechanism by which neurons produce signals. Therefore, if we want to decipher the information transmitted in the brain, we should make sure we can reliably detect spikes. One way of doing this is to make very good devices to measure them, but more often then not there will be noise, and therefore we may want to use more sophisticated methods to separate the spikes from the noise.[^1] Here are some of my notes on spike detection. 

[^1]: Note that GIGO still stands.

## TL; DR 

- threshold method 1: if below[^2] \\ x \\ std, then spike. (Schroeter 2015) 
  + In his Rich Club Topology paper Schroeter used 5 SD 
  + In his Master's thesis Prez used 4 SD
  + one criticism of threshold methods is that it tends to catch noise quite readily 
- another method is called **Nonlinear Energy Operator** (NEO) 
  + based on the idea of making small signals smaller, and big signals bigger
  + note that this is a *preprocessing* method, you still need to find a way to find the peaks after this 
- the refractory period may also need to be considered (to make sure you are catching spikes that are biologically plausible)
  + eg. A 2.0 ms refractory period was set in (Schroter 2015) (ie. if the algorithm detects a spike at 1.0 ms, it won't consider anything as a spike until 3.0ms. (I assume the algorithm runs starting at time point 0 but I am not sure)

[^2]: We used below because spikes represent inflow of positive ions, ie. net flow of negative charge outside of the neuron, I think
  
## Preprocessing 

- before finding peaks / spikes, most will do some preprocessing, such as to remove noise that you definitely know are not spikes (due to a frequencies that are too low or too high) 
- one way is to use a fiter 
  + in Schroeter et al 2015, they used third order Butterworth filter and a frequency window of 600-8000Hz 
  + In Prez's Master's thesis, he used a elliptic filter with frequency window of 300 - 8000Hz

## Standard Deviation

Spikes are named so because they represent a sudden increase in volage/current through the neuron. The two key terms here are therefore *sudden* and *increase*. Let's consider the increase in voltage first. One way to identify this is via ...

## Median or mean 

- Schroeter et al 2015 used mean 
- Prez used median to avoid large amplitudes due to spike


## Refractory Period 

- Schroter et al imposed a refractory period of 2.0ms


## Available package 1: Wave_clus

Wave_clus implements spike detection via the following steps: 

- filters data (How ???)
- calculates optimal amplitude threshold (How ???) 
- calculates a maximum threshold to avoid high amplitude artifacts 
  + this "calculate" seem to little more than setting a paramter (50SD is the default I think)


References: 

- [Gaidica 2015](http://gaidi.ca/weblog/extracting-spikes-from-neural-electrophysiology-in-matlab)
- [Simple summary of the different filters](http://www.rfwireless-world.com/Terminology/Butterworth-filter-vs-Chebyshev-filter-vs-Bessel-filter-vs-Elliptic-filter.html)
- [Wave_clus](https://github.com/csn-le/wave_clus)
- [Tutorial for preprocessing and analysis of spike-train data](http://www.fieldtriptoolbox.org/tutorial/spike)
- [Past, present and future of spike detection techniques](http://www.sciencedirect.com/science/article/pii/S0361923015000684)
