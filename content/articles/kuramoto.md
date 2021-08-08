Title: The Kuramoto Model
Date: 2021-08-07 18:00
Slug: the_kuramoto_model
Author: username
Summary: Coupled oscillators and the Kuramoto model.

> Written with [StackEdit](https://stackedit.io/).
# The Kuramoto Model
This post was inspired by Steven Strogatz's talk [here](https://www.youtube.com/watch?v=e5xxdNeNkmE&t=2787s).
## Oscillators
Oscillation plays a very important role in physics and how we understand the world. From simple harmonic motion, to chemical reactions, to neuroscience, to Josephson junctions, they appear everywhere. One phenomenon which has gained a lot of attention over the years is that of  **coupled oscillators**. An intricate system of individual oscillators, if coupled properly, can produce synchronous behavior. One instance of this is found in [fireflies](https://www.youtube.com/watch?v=ZGvtnE1Wy6U). 
![Fireflies sychronizing in the Great Smoky Mountains.](https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/gettyimages-690410254-594x594-1583518830.jpg)
##  The Kuramoto Model
How does this complex phenomenon occur and how can we model it? Perhaps the most well known model is the **[Kuramoto model](https://en.wikipedia.org/wiki/Kuramoto_model)** developed by physicist Yoshiki Kuramoto in the early 70s. The basic idea of the Kuramoto model is this: assume we have a group of similar oscillators that are weakly coupled. Each oscillator will change its phase based on the sine of the phase difference between each of the oscillators it is connected to. It is helpful to think of a pair of runners. If one runner is fast while the other is slow, then the faster runner can slow down while the slower runner speeds up. Note here that if the coupling was too strong or too weak, then the runners may overshot or undershot their targets. 

How do we capture this idea in mathematical symbols? Assume we have $N$ oscillators. Each oscillator has a natural frequency $\omega_i$. Let $A$ be an $N \times N$ matrix with elements $a_{ij}$ that is one if oscillator $i$ is connected to oscillator $j$. This matrix is symmetric. The rate of change of a given oscillator is given by the sum of the sine of the phase difference between coupled oscillators. We obtain the system below.

$$\frac{d\theta_i}{dt} = \omega_i + \sum_{j=1}^N a_{ij}\sin(\theta_j-\theta_i),  \quad (1 \leq i \leq n) $$

One assumption that is made quite often is that all oscillators have the same natural frequency. This means we can do a change of variable $\hat{\theta_i} = \theta_i - \omega_i t$$ to yield the following simplification,

$$\frac{d\hat{\theta_i}}{dt} = \sum_{j=1}^N a_{ij}\sin(\hat{\theta_j}-\hat{\theta_i}),  \quad (1 \leq i \leq n)  .$$ 

There are plenty of modifications that can be made to this system. For example, heterogeneous weights, noise,  different natural frequencies, etc. These modifications have been studied, but generally make things harder to analyze. 

## When does synchronization happen?
In the model described in the last section, **synchronization** occurs when the oscillators reach similar phases after a sufficiently long time. In our $\hat{\theta}$ representation, this means they all go to the same value modulo $2\pi$. If this occurs for all initial conditions, then the graph associated with the system is said to be **globally synchronizing**. The question we are interested in is then, "when is a graph globally synchronizing?" 
![Kuramoto model network.](https://lh3.googleusercontent.com/MUhfq_IlCzmiTs4VlXvjan4D4p7cZHUflwQqM8pZ-IoVvT5u5wX_aHxfogTDrce1V9ZsR1v3aHwi5Mm2lQfYrpi8MDpj2DktMqHXAwSWbgvw76AuFe8ykl86rP88TMiCdtjgag4RUZyHcEDyhRooeM9jxCRjGaQi1JLB_i8VPQFActLjR571RfpyTQht7f5bmYAX2j49QULjhpV8_PonN7qYidj7X-zO5IBGHM2bzHtzdAviaH7DU8Gwes6js4YwAL0fes2ifVxEdCeQUGKd2POCJOcjWpXpv5kJN3egUw9_DQGKTTxYjoYYsbpMKUC8nCcSajcJDgHCjPqueHsLkIX06Dp6eHMjTbp-3ygxRz-jCCZo_A0WMP9uyEJrRwr-4Y0aDMkeH6npR-cl4CMshScNtXPC94YwQtWEDUb_GCfJsuPZ9xdZESd28dWvV3SCHRREFilGKokVgV1CbjBuUEKanU6C9rY3ObGaMWifr97fUkyxbS7kivLEKvmY4n4e_xb4-UmNSM2TmWH6BflqqlEnF2Pg6rfB3vY2dFcoEcOMo-AAjeI-rUndZF2ob5DXdauuYAsebI52Fy0MDfOSW6gdg1oAX3aH6qeSVHSFVbRMwS03bj7IBhY5-UBHtsiYuTFWy2yC_V2y6fzj-cooJRUFaw_K18igVIL_hP_NUEC37Cy_ID5DhR1UwKKyyHlCRrR3A49ns-vncBFy0DOS9AGG=w512-h288-no?authuser=0)

## Dynamics
A globally synchronizing system must then have all of its fixed points attracting. The fixed points satisfy,
$$\frac{d\hat{\theta_i}}{dt} = \sum_{j=1}^N a_{ij}\sin(\hat{\theta_j}-\hat{\theta_i}) = 0,  \quad (1 \leq i \leq n)  .$$ 
Now note that this system is a gradient system, which means every initial condition will end up at a fixed point. However, we need to ensure every fixed point is attracting and not a saddle to ensure global synchronicity. This often involves analysis of the Jacobian.
$$J_{jk} = \begin{cases} \quad \quad \quad a_{jk}\cos(\hat{\theta_k}) & , j \not= k \\
-\sum_{s=1}^N a_{js} \cos(\hat{\theta_s}-\hat{\theta_j}) & , j=k \end{cases} $$
The Jacobian is symmetric, which means the eigenvalues are all real. Thus, we do not get any oscillation in the $\hat{\theta}$ representation of the system. 

## Global Synchronization
As mentioned before, we are interested on what conditions we can impose to ensure a graph is globally synchronizing. Generally speaking, if a graph $G$ is sufficiently dense, then it is globally synchronizing. How dense does it have to be? In 2012, Richard Taylor proved that if the degree $\delta(G) > 0.93(|G|-1)$, then the graph globally syncronizes. This upper bound was improved by Ling, Xu, and Bandeira in 2018 to $\delta(G) > 0.7929(|G|-1)$. What about the lower end? In 2006, Wiley, Strogatz, and Girvan proved that there exists a sequence of regular graphs that do not globally synchronize such that
$$\lim_{n \to \infty} \frac{\text{degree of vertices}}{n-1} = 0.6809 \dots .$$

This means there is a sort of unknown middle ground. After the upper bound, you are guaranteed to synchronize and below the lower bound there exists graphs that do not synchronize, but the in-between area presents a lot of difficulties. 

## Conclusion
Oscillators are incredibly important in the sciences, and we still have so much to learn. They appear in our nervous system, physical systems, and even nature. Coupled oscillators are also interesting from a mathematical point of view, because they test our ability to make sense of larger high dimensional systems.

Lastly, I think it is fun to actually look at these systems and play around with them. I have coded up a basic animation of the Kuramoto model that can be viewed [here](https://youtu.be/0hwj-PcWod0) and downloaded via [Github](https://github.com/Nightwing52/dynamical_systems). 
