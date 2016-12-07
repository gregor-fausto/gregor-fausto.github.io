---
title: "Additive Partitioning of Biodiversity Effects"
output: html_document
---
$\frac{1}{N}_{i}\frac{dN}_{i}{dt} / \frac{b_1}{b_2}$

$1\divided{N}_{i}$

  $\frac{a_1}{a_2} \Big/ \frac{b_1}{b_2}$

The equation(s) that Hector and Loreau (Nature 2001) use to partition sampling and complementarity effects are:

$\Delta{Y} = {Y}_{O} - {Y}_{E}  \\ \Delta{Y} = \displaystyle \sum_{i} {R}{Y}_{Oi}{M}_{i} - \displaystyle \sum_{i} {R}{Y}_{Ei}{M}_{i} = \displaystyle \sum_{i} \Delta{R}{Y}_{i}{M}_{i} \\ \Delta{Y} =  {N}\times\overline{\Delta{RY}}\times\overline{M} + {N}\times\mathrm{Cov}{(\Delta{RY,M})}$

Hector and Loreau (2001) write "selection [sampling]" is measured by a covariance function" and <span style="color:red">"occurs when changes in the relative yields of species in a mixture are non-randomly related to their traits (yields) in monoculture."</span> On the other hand, "complementarity...measures any change in the average relative yield in the mixture."

*Note*: I'm not yet convinced. The null hypothesis is basically that there's no change through time, or that the change through time is independent of how many species are present. Question: can diversity promote or constrain drift? Likewise, I agree with Zuppinger-Dingley that it should really be called a sampling effect rather than a selection effect because this muddies the water too much.

The net biodiversity effect, $\Delta{Y}$, is the difference between the observed yield, ${Y}_{O}$, of a mixture and its expected yield, ${Y}_{E}$. Note here that *yield* can be defined as any measureable ecosystem property.

$\Delta{Y} = {Y}_{O} - {Y}_{E}$

The expected yield is calculated from the 'null hypothesis' that there is no sampling (*sensu* Zuppinger-Dingley et al. 2014, also called the "selection effect" by Hector and Loreau) nor complementarity effect.

We can rewrite these components. Write the observed yield as:

${Y}_{O} = \displaystyle \sum_{i} {R}{Y}_{Oi}{M}_{i}$

Here, ${Y}_{Oi}$ is the observed yield of species *i* in the mixture, which means ${Y}_{O} = \displaystyle \sum_{i} {Y}_{Oi}$. This is the total observed yield, summed over all species in the mixture. We can also write this in terms of relative yield ${R}{Y}_{Oi}$, which is the ratio of a species' yield in mixture to its yield in monoculture, such that ${R}{Y}_{Oi} = {Y}_{Oi}{M}_{i}$.

Now, write the expected yield as:

${Y}_{E} = \displaystyle \sum_{i} {R}{Y}_{Ei}{M}_{i}$

Here, ${Y}_{Ei}$ is the expected yield of species *i* in the mixture, which means ${Y}_{E} = \displaystyle \sum_{i} {Y}_{Ei}$. This is the total expected yield, summed over all species in the mixture. We can also write this in terms of the relative yield ${R}{Y}_{Ei}$, which is the proportion at which species *i* was seeded or planted. As a result, ${Y}_{Ei}$ is the product of the expected relative yield of species *i* and its yield in monoculture [${Y}_{Ei}={R}{Y}_{Ei}{M}_{i}$].

All this gets us to the point where we can say that,

$\Delta{Y} = \displaystyle \sum_{i} \Delta{R}{Y}_{i}{M}_{i}$

which is then partitioned using Price's general theory of selection (a mathematical fact, a theorem).

$\displaystyle \sum_{i} \Delta{R}{Y}_{i }{M}_{i} =  {N}\times\overline{\Delta{RY}}\times\overline{M} + {N}\times\mathrm{Cov}{(\Delta{RY,M})}$
