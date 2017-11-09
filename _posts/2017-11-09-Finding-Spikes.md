# Finding Spikes 

Spikes, or action potentials, is the key mechanism by which neurons produce signals. Therefore, if we want to decipher the information transmitted in the brain, we should make sure we can reliably detect spikes. One way of doing this is to make very good devices to measure them, but more often then not there will be noise, and therefore we may want to use more sophisticated methods to separate the spikes from the noise.^[Note that GIGO still stands.] Here are some of my notes on spike detection. 

## TL; DR 

- threshold method 1: if below^[We used below because spikes represent inflow of positive ions, ie. net flow of negative charge outside of the neuron, I think] $x$ std, then spike. (Schroeter 2015) 
  + In his Rich Club Topology paper Schroeter used 5 SD 
  + In his Master's thesis Prez used 4 SD
  + one criticism of threshold methods is that it tends to catch noise quite readily 
- another method is called **Nonlinear Energy Operator** (NEO) 
  + based on the idea of making small signals smaller, and big signals bigger
- the refractory period may also need to be considered (to make sure you are catching spikes that are biologically plausible)
  + eg. A 2.0 ms refractory period was set in (Schroter 2015) (ie. if the algorithm detects a spike at 1.0 ms, it won't consider anything as a spike until 3.0ms. (I assume the algorithm runs starting at time point 0 but I am not sure)

## Standard Deviation

Spikes are named so because they represent a sudden increase in volage/current through the neuron. The two key terms here are therefore *sudden* and *increase*. Let's consider the increase in voltage first. One way to identify this is via ...



## Median 


References: 

[Gaidica 2015](http://gaidi.ca/weblog/extracting-spikes-from-neural-electrophysiology-in-matlab)


