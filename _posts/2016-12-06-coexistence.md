---
title: "Lotka-Volterra Competition Models"
layout: default
---



Let's start by writing the two-species Lotka-Volterra competition equations with absolute competition coefficients (Chesson 2000):

$$\frac{1}{N_{i}} \cdot \frac{dN_{i}}{dt} = r_{i}(1 - \alpha_{ii}N_{i} - \alpha_{ij}N_{j}),\quad  i=1,2,\ j \neq i$$

Written in this way, species _i_ can increase from low density in the presence of competitor _j_ if $\alpha_{ii}>\alpha{ij}$; that is, if intraspecific competition is stronger than interspeciic competition. This is written by Chesson as "species _j_ cannot competitively exclude species _i_ if the effect that species _j_ has on itself is more than the effect that spevcies _j_ has on species _i_."

Note that in Lotka-Volterra models, per capita growth rates are linear functions of density. Nonlinear per capita growth rates can be incorporated into a model of the kind above by making  competition coefficients a function of density [$\alpha_{ij}=f_{ij}(N_{i},N_{j})$]. The results will remain true if the competition coefficients are evaluated for a resident at equilibrium and the invader at zero.

A special linear form of the resource limitation model (related to R*, I believe) advances this idea. To start, consider a model with a single resource as the limiting factor. The long-term low-density growth rate of an invader _i_ that competes with a resident _s_ is: 

$$\overline{r}_{i} = b_{i} \left( \frac{\mu_{i}}{b_{i}} - \frac{\mu_{s}}{b_{s}} \right)$$

Here, the $\mu$s represent the mean per capita growth rate in the absence of resource limitation, and the _b_s represent the rates at which per the per capita growth rate declines as resources decline in abundance. Formulated this way, the ratio $\mu/b$ is an estimate of the average fitness of the species in this environment, and thus has the property of predicting the outcome of competition. The species with the larger $\mu/b$ is the winner and has the smaller _R_*. Different species may have similar values of $\mu/b$ because of tradeoffs; however, this equivalence does not lead to stable coexistence. Any pair of species has opposite signs in the equation above, meaning that only one can increase from low density in the presence of the other. 

While the model above has just a single resource as the limiting factor, a model with resource partitioning provides different insight. Chesson (2000) uses MacArthur's mechanistic derivation of a Lotka-Volterra competition to derive a model with resource partitioning. The per capita growth rate of an invader _i_ can be written as:

$$\begin{aligned} \overline{r}_{i} = \frac{1}{N_{i}} \cdot \frac{dN_{i}}{dt} &= b_{i} (k_{i}-k_{s}) + b_{i}(1-\rho)k_{s} \\ &= b_{i} (\frac{\mu_{i}}{b_{i}}-\frac{\mu_{s}}{b_{s}}) + b_{i}(1-\rho)\frac{\mu_{s}}{b_{s}}\\ \end{aligned}$$

Note that the _k_s are equivalent to the $\mu/b$s and $\rho$ is a measure of resource-use overlap. [Important references here include MacArthur (1970), Armstrong and McGehee (1980), Chesson (1990), Chesson and Huntly (1997)] The first term of this equation is the *average fitness comparison* from a model with a single limiting resource (thus has opposite sign for the two species). When $\rho<1$ (resource overlap is <100%), the last term in the equation is positive for both species. This term is a *stabilizing term* that counters differences in average fitness expressed in the first term. Coexistence is thus achieved in this model if the stabilizing term is greater in magnitude than the fitness difference term. 

To start linking this to an resource model, equation 10 in Chesson and Huntly (1997) showed that the long term low density growth rate is:

$$\begin{aligned} \\ \overline{r}_{i} &\approx \mu_{i} - \mu_{j}(\frac{b_{i}}{b_{j}}) \\ &=\mu_{i}(\frac{b_{i}}{b_{i}}) - \mu_{j}(\frac{b_{i}}{b_{j}}) \\ &=b_{i}(\frac{\mu_{i}}{b_{i}}-\frac{\mu_{j}}{b_{j}})  \end{aligned}$$

This can then be extended to multiple resources. In the formulation of Chesson and Huntly (1997), we get there by using three quantitites: the proportionality of resource use ($\rho$), the maximum resource harvest rate ($h_{i}$), and the maintenance requirement ($m_{i}$). Resource overlap is such that $0<\rho<1$. The maintenance requirement is the amount of resource needed to maintain zero populution growth. The difference $h_{i}-m_{i}$ is the net maximum harvest rate. Coexistence thus occurrs when (also see p. 77 of Tilman (1982)):

$$\rho<\frac{h_{i}-m_{i}}{h_{j}-m_{j}}<1/\rho$$

I'm thinking about this in the following way. As niche overlap increases, the ratio of average fitness differences ($(h_{i}-m_{i})/(h_{j}-m_{j})$) that permit coexistence decrease. In particular, $\rho$ and $1/\rho$ both tend to 1; this means that coexistence under high niche overlap is only possible with fitness equivalence. The formulation in Chesson and Huntly (1997) explicitly shows that fitness is the net maximum harvest rate. I could be wrong but this means that the average fitness difference can depend on the environment if different environments have different effects on different species. 
The shaded region of the graphs below show the regions of coexistence, as a function of either niche overlap ($\rho$) or stabilizing niche difference ($1-\rho$). As niche overlap increases, the range of average fitness differences that permit coexistence decreases until coexistence with complete niche overlap is only possible with fitness equivalence. The inverse is true when coexistence conditions are plotted as a function of stablizing niche differences.

![plot of chunk unnamed-chunk-2]({{ site.url }}/images/coexistence-unnamed-chunk-2-1.png)

![plot of chunk unnamed-chunk-3]({{ site.url }}/images/coexistence-unnamed-chunk-3-1.png)

I'm at three alternative formulations of coexistence conditions.

$$\rho<\frac{h_{i}-m_{i}}{h_{j}-m_{j}}<1/\rho \\ \rho<\frac{\mu_{i}}{\mu_{j}} \cdot \frac{b_{j}}{b_{i}}<1/\rho \\ \rho<\frac{\kappa_{i}}{\kappa_{j}}<1/\rho$$

which means:

$$\frac{h_{i}-m_{i}}{h_{j}-m_{j}} = \frac{\mu_{i}}{\mu_{j}} \cdot \frac{b_{j}}{b_{i}} = \frac{\kappa_{i}}{\kappa_{j}} = \left( \frac{\eta_{i}-1}{\eta_{j}-1} \right) \sqrt{\frac{\alpha_{jj}\alpha_{ji}}{\alpha_{ii}\alpha_{ij}}}$$

Chesson and Kuang (2008) explicitly modeled three trophic levels (predator, focal species, prey). I think this can be thought of as an extension of approaches that have used consumer-resource models to look at species interactions (eg. MacArthur (1970), Tilman (1982), Chesson and Huntly (1997)). They derive equations for niche overlap ($\rho$), sensitivity to predation and competition (_s_), and fitness measures ($\kappa$). These can be combined to provide measures of intraspecific and interspecific density dependence.

$$\alpha_{jj}=s_{j}/\kappa_{j}, \quad \alpha_{ij}=\rho s_{j}/\kappa_{i}$$

Intraspecific density dependence is strong (large values of $\alpha_{jj}$) if species _j_ is sensitive to competition (large $s_{j}$) or has low fitness (small $\kappa_{j}$). I'm trying to make sense of the latter: low per capita growth rates at low densities (at a given level of sensitivity) increases intraspecific density dependence - is that correct? Interspecific density dependence is strong (large values of $\alpha_{ij}$) if niche overlap is high ($\rho$ approaching 1), if _j_ is sensitive to competition (large $s_{j}$), or  if _i_ has low fitness (small $\kappa_{i}$). I think the Chesson and Kuang (2008) formulation might actually make things more complicated than necessary, at least to start. The text of their paper reads like you could get the same result using MacArthur's formulation of Lotka-Volterra as a resource competition model, though I'm not sure if it took Chesson-math to extend the logic. In any case, this packages itself into neat relationships between interaction coefficients, niche overlap, and ecological fitness:

$$\frac{\alpha_{ij}}{{\alpha}_{jj}} = \frac{\kappa_{j}}{\kappa_{i}}\rho$$

and the flip side of the relationship:

$$\frac{\alpha_{ji}}{{\alpha}_{ii}} = \frac{\kappa_{i}}{\kappa_{j}}\rho$$

These can be combined into a single equation, providing a symmetric measure of the ratio of interspecific to intraspecific density dependence for any pair of species _i_ and _j_. Substitute the $\kappa$ terms from one equation into the other, and take the square root to get:

$$\rho = \sqrt{\frac{\alpha_{ij}}{{\alpha}_{jj}} \cdot \frac{\alpha_{ji}}{{\alpha}_{ii}}}$$

With Chesson's assistance, Godoy and Levine (2014a) then rescaled an annual plant population growth model that accounts for intraspecific and interspecific density dependence to be able to calculate terms relating competition to components of equalizing and stabilizing fitness. The starting model is:

$$ N_{i,t+1} = (1-g_{i})(s_{i})N_{i,t} + \frac{\lambda_{i}g_{i}N_{i,t}}{1 + \alpha_{ii}g_{i}N_{i,t} + \alpha_{ij}g_{j}N_{j,t}} $$

Variables in the equation are population size ($N_{i}$), germination ($g_{i}$), seed survival ($s_{i}$), per germinant fecundity ($\lambda_{i}$), and competition coefficients. They rescaled model terms so that they had a variable for the probability of seed loss:

$$ \beta_{i} = 1 - (1 - g_{i})(s_{i}) $$

as well as for 'productivity' or the annual seed production per seed lost:

$$ \eta_{i} = \frac{\lambda_{i}g_{i}}{\beta_{i}} $$

Then, to match the Lotka-Volterra competition coefficients and achieve a proportional reduction in $r_{i}$, they divide the $\alpha$s by the potential productivity of the responding species _i_ and multiply by the germination fraction of the competitor species (because seeds must germinate to have a competitive effect):

$$ \alpha_{ij}^{\prime} = \frac{g_{j}\alpha_{ij}}{\eta_{i}-1} $$

Substituting terms back into the plant population model gets us:

$$ \frac{N_{i,t+1}}{N_{i,t}} = (1-\beta_{i}) + \beta_{i} \left(\frac{\eta_{i}}{1+(\eta-1)(\alpha_{ii}^{\prime}N_{i}+\alpha_{ij}^{\prime}N_{j})}\right) $$

Taking the natural log of the second term (the first doesn't change population growth rate), algebra and a first-order Taylor approximation take us to:

$$ (\eta_{i}-1)(1-(\alpha_{ii}^{\prime}N_{i}+\alpha_{ij}^{\prime}N_{j})) $$

Godoy and Levine (2014a) take this to be equivalent to the Lotka-Volterra model, with seeds produced per seeds lost roughly equivalent to $r_{i}$. These competition coefficients are defined by life history parameters that can be estimated, hence the magic of this particular piece of math.

Kraft _et al_ (PNAS 2015) quantify stabilizing niche differences ($1-\rho$) and the average fitness difference between competitors ($\kappa_{j}/\kappa_{i}$). The stabilizing niche difference between a pair of annual plants can be expressed (Chesson 2012, Godoy et al 2014a, Godoy et al 2014b) as:

$$1-\rho = 1 - \sqrt{\frac{\alpha_{ij}\alpha_{ji}}{\alpha_{jj}\alpha_{ii}}}$$

In this case, $\alpha_{ij}$ "describes the per capita effect of species _j_ on _i_". Put another way, it is related to how much intraspecific competition ($\alpha_{jj}\alpha_{ii}$) is stronger than interspecific competition ($\alpha_{ij}\alpha_{ji}$).

The average fitness differences between competitors is expressed (Godoy et al 2014a) as:

$$\frac{\kappa_{j}}{\kappa_{i}} = \left( \frac{\eta_{j}-1}{\eta_{i}-1} \right) \sqrt{\frac{\alpha_{ij}\alpha_{ii}}{\alpha_{jj}\alpha_{ji}}}$$

In this case, $\eta_{j}$ "describes the seeds produced per seed lost from the seed bank for plant species _i_. Larger ratios of $\kappa_{j}/\kappa_{i}$ indicate increasing fitness advantages of species _j_ over species _i_. Written in this way, there are two components to average fitness differences between competitors: a "demographic response ratio" ($({\eta_{j}-1})/({\eta_{i}-1})$) and "competitive response ratio" ($\sqrt{({\alpha_{ij}\alpha_{ii}})/({\alpha_{jj}\alpha_{ji}})}$). The "competitive response ratio" describes [...how much species _i_ is more sensitive to intra- and interspecific competition than species _j_...].

###References
MacArthur R (1970) Species packing and competitive equilibrium for many species. _Theor Pop Bio_ 1:1-11.  
Armstrong RA, McGehee R (1980) Competitive exclustion. _Am Nat_ 115:151-170.  
Tilman D (1982) Resource Competition and Community Structure. _Monographs in Population Biology_ (Princeton University Press, Princeton).  
Chesson P (1990) MacArthur's consumer-resource model. _Theor Pop Bio_ 37:26-38.  
Chesson P, Huntly N (1997) The rules of harsh and fluctuating conditions in the dynamics of ecological communities. _Am Nat_ 150:519-553.  
Chesson P (2000) Mechanisms of Maintenance of Species Diversity. _Annu Rev Ecol Syst_ 31:343-366.  
Chesson P, Kuang JJ (2008) The interaction between predation and competition. _Nature_ 456:235-238.  
Chesson P (2012) Species Competition and Predation. _Encyclopedia of Sustainability and Science and Technology_, ed Meyers R (Springer, Berlin).  
Godoy O, Levine JM (2014a) Phenology effects on invasion success: Insights from coupling field experiments to coexistence theory. _Ecology_ 92(5):1157-1165.  
Godoy O, Kraft NJB, Levine JM (2014b) Phylogenetic relatedness and the determinants of competitive outcomes. _Ecol Lett_ 17(7):836-844.  
