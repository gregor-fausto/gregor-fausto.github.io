---
title: "teaching as research conference"
layout: default
---

Parameter estimates for belowground transitions {#parameter-estimates-for-belowground-transitions .unnumbered}
-----------------------------------------------

The figure below illustrates the transitions in the first year the seed
bags are buried. There are two boxes: one for the seed bag experiment
and one for the viability trials. In the seed bag experiment, I split
January into two steps, one for just before germination and one for just
after. Solid arrows represent transitions and are labeled with
corresponding vital rates. In the models, I have adopted $s_1 = \phi$,
$g_1=\gamma$, $s_2 = \rho$, and $v_1 = \upsilon$.\

In the seed bag experiment, the parameter $s_1$ is the proportion of
seeds from the start of the experiment that remain intact in January. In
January, the remaining seeds are in one possible state: intact (this
includes viable and non-viable seeds). We assume that there is no decay
during germination (seed loss happens over extended periods of time, not
instantaneously in January) so that the number of seeds before
germination is equal to the number of seeds and seedlings after
germination. At this point, the seeds have transitioned into one of four
possible states. Intact and viable seeds may have (1) germinated or (2)
not germinated and thus remain dormant. Because non-viable seeds could
not have germinated (forbidden state 3), all other intact seeds would
have been non-viable (4).\
I represent two transitions between pre-germination seeds in January and
post-germination seeds and seedlings in January. The first is for seeds
that are viable and germinate; these become seedlings. The second is for
seeds that do not germinate; these remain seeds and include both viable
and non-viable seeds (the sum of
$(1-g_1)v_1^{\frac{1}{3}} and (1-g_1)(1-v_1^{\frac{1}{3}})$. For the
purposes of parameter estimation, we only represent the number of
seedlings viability is estimated separately.\
We want to incorporate the loss of viability into our model. We assume
that the rate of loss of viability is constant, and that germination
removes some number of seeds from the pool of viable seeds but does not
change the rate of decay. Some fraction of the total seeds in January
pre-germination is viable ($v_1^{\frac{1}{3}}$) and some of those viable
seeds germinate. We include viability in our estimates of germination
rate so as to not overestimate the true germination rate. The number of
seeds that remain intact are those that do not germinate ($1-g_1$),
which includes both viable ($v_1^{\frac{1}{3}}$) and non-viable
($1-v_1^{\frac{1}{3}}$) seeds. Seeds that germinate must be viable.\
Here, we use viability in our germination estimates. For the full life
cycle, this would model the rates of intact seeds and only incorporate
viability in the germination transition.

Viability trials {#viability-trials .unnumbered}
----------------

In October (year $t+1$), we first removed the bags and counted the
number of ungerminated, intact seeds. In the lab, we conducted
germination trials and viability assays on subsets of the seeds from
each bag to estimate the viability of the ungerminated, intact seeds. We
collected the following data:

-   $n_{_{\mathrm{germ}} ijt}$ = observed count of seeds at the start of
    the germination trial for the $i^{th}$ bag, from the $j^{th}$ site,
    in the $t^{th}$ year, assumed to be measured perfectly

-   $y_{_{\mathrm{germ}} ijt}$ = observed count of germinated seedlings
    in the $i^{th}$ bag, from the $j^{th}$ site, in the $t^{th}$ year,
    assumed to be measured perfectly

-   $n_{_{\mathrm{viab}} ijt}$ = observed count of seeds at the start of
    the viability trial for the $i^{th}$ bag, from the $j^{th}$ site, in
    the $t^{th}$ year, assumed to be measured perfectly

-   $y_{_{\mathrm{viab}} ijt}$ = observed count of viable seedlings in
    the $i^{th}$ bag, from the $j^{th}$ site, in the $t^{th}$ year,
    assumed to be measured perfectly

We use a conditional probability tree to graphically represent how to
compose the estimates from the germination and viability experiments.

We assume that (1) any seed that germinates is viable, P($V|G)$=1, and
that (2) any seed that germinates can not be not viable, P($V^C|G$)=0.
We used experiments to estimate the probability of germinating, P($G$),
and the probability of being viable conditional on not germinating,
P($V|G^C$). We use these probabilities to calculate the total
probability of being viable, P($V$) = P($G$) +
P($V|G^C$)$\times$(1-P($G^C$)).\
We use the experiments to estimate:

-   $\gamma_{i}$ = the true, unobserved proportion of seeds that
    germinate in the October germination trials in the $i^{th}$ bag

-   $\upsilon_{i}$ = the true, unobserved proportion of intact seeds
    that are viable given that they did not germinate in the October
    germination trials in the $i^{th}$ bag

The germination experiment and viability experiment can each be modeled
as binomial trials.

$$\begin{aligned}
 [ \bm{\gamma} | \bm{n_{\mathrm{germ}}}, \bm{y_{\mathrm{germ}}} ] \propto 
 &
  \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{_{\mathrm{germ}} i} | n_{_{\mathrm{germ}} i}, \gamma_{i} )  \times \mathrm{beta} ( \gamma_{i} | 1,1 )\end{aligned}$$

$$\begin{aligned}
 [ \bm{\upsilon} | \bm{n_{\mathrm{viab}}}, \bm{y_{\mathrm{viab}}} ] \propto 
 &
  \prod_{i=1}^{I} 
    \mathrm{binomial} ( y_{_{\mathrm{viab}} i} | n_{_{\mathrm{viab}} i}, \upsilon_{i} )  \times \mathrm{beta} ( \upsilon_{i} | 1,1 )\end{aligned}$$

The binomial and beta distributions are conjugate distributions, so we
can obtain a closed form for each posterior. These are given as beta
distributions,
$\mathrm{beta}(\phi | \alpha_{posterior} , \beta_{posterior}),$ where
$\alpha_{posterior} = \alpha_{prior} + y$ and
$\beta_{posterior} = \beta_{prior} + n - y$.\
Eckhart et al. (2011) previously analyzed these data by obtaining point
estimates for the proportion of seeds that germinate, P($G$), and the
proportion of seeds that do not germinate that are viable, P($V|G^C$).
These estimates were then used to calculate the proportion of seeds that
were viable, P($V$) = P($G$) + P($V|G^C$)$\times$(1-P($G^C$)).\
The point estimates for germination and viability in Eckhart et al.
(2011) are equivalent to the maximum a posteriori (MAP) of the posterior
distribution for each experiment. The MAP is the mode of the posterior
distribution. The mode of a beta distribution is given by:

$$...$$

Obtaining the point estimate for germination and viability probability
by the method in Eckhart et al. (2011) and from the MAP of the beta
posteriors gives identical results. Intuitively, this makes sense: the
proportion of successes out of trials should be the same as the
probability at which the distribution is maximized. So far so good. This
establishes that the two approaches are equivalent. In both cases, we
obtain point estimates for the probability that seeds in a bag are
viable but this is estimate is not a parameter with a distribution but
rather a point estimate.\
This is a bit unsatisfying because it means that this term scales the
binomial model for germination up or down, but only by a constant rather
than a full probability distribution.\
A possible approximation would be the following. The successes is the
number of seeds that germinate plus the number of seeds that stain in
viability trials. The number of trials is the number of seeds that
started the viability trial plus those that germinated in the
germination trial. So the effect is to supplement the data from the
viability trial with additional successes. This would be appropriate if
all the ungerminated seeds were tested for viability (this wasn't
usually met). We can get closer if we discard any of the data for which
fewer than 50% of ungerminated seeds were tested.\
The benefit of having viability be a parameter with a distribution is
that it would be comparable to other parameters in the model. Our
estimates of germination and dormancy from the seed bags are incorporate
estimates of viability. If germination probability is a parameter with a
distribution but viability is not, all the uncertainty in our estimate
of germination is the result of uncertainty in germination rather than
combined uncertainty in germination and viability. The same holds for
dormancy.\
I consider the following approximation. First, I discard the data for
which fewer than 50% of ungerminated seeds were tested. This results in
losing some data but means that we retain viability trials in which more
than half the seeds that didn't germinate were tested for viability.
\[explain \...\] The successes is the number of seeds that germinate
plus the number of seeds that stain in viability trials. This is the
total number of seeds that we identified as viable across both sets of
experiments. The number of trials is the number of seeds that started
the viability trial plus those that germinated in the germination trial.
The effect is to supplement the data from the viability trials with
additional successes and associated trials from the germination trials.
Although this is a compromise between the two datasets, it would be
appropriate if all the ungerminated seeds were tested for viability.
Quantify this in some way\...x% of seed bags had more than 50% of bags
tested?\
I also show that this is a reasonable approximation for this dataset by
plotting the MAP of the posterior from the combined dataset against the
viability probability obtained by point estimates. In Figure X, a 1:1
relationship between the two estimation methods suggests that the
estimates are comparable. I show the relationship between the two
estimates for all data, with only data \>50% tested for viability (loss
of x% of dataset), and with only data \>75% tested for viability (loss
of x% of dataset). The plots show the correlation and R2. Given that
these estimates are relatively comparable, we proceed with the analysis
using the combined dataset to estimate viability.\
This would be a parameter in a joint posterior, and thus have an
associated probability distribution. One problem: the two experiments
are sequently and not truly independent. If a seed germinates in the
first experiment, it isn't tested for viability. So when I considered
modeling the germination and viability experiments with a shared
viability parameter, but this didn't seem to make sense if germination
and viability were nested responses. I considered obtaining a posterior
from the first experiment in the form of a beta distribution, and then
using this as a prior to analyze the second experiment. Again, this
didn't really make sense because the responses were on the same seeds. I
also thought about multiplying and summing the beta posteriors. The
product and sum of betas looks pretty ugly so I didn't go down this
rabbit hole yet. But maybe this is the way to go? It seems messy and I
guess I'm not sure what I get by pulling out this closed form. In
particular, the closed form involves hypergeometric functions that are
unlikely to be useful in writing up a mathematical expression for the
joint posterior.\
Next, I considered using a model with partial pooling for binary
repeated trials. In the model above, the closed form neatly represents
the per-bag viability. First, I wasn't sure how to use the per-bag
viability in the joint posterior with the germination data. Should the
germination model include the bag-level viability estimate or the
site-level viability estimate? Germination itself was going to be a
site-level estimate, but maybe it made sense to account for differences
in viability among different bags. Thinking about this also had me
wondering how I would calculate dormancy as a derived quantity. If
dormancy involves the product of germination and viability, then these
two terms must be calculated at the same level. The best way I could
think of doing this involved rewriting the models with a log-odds
parameterization. This makes it possible to estimate a mean for
different levels (bag- and site-level means) with separate variances.
I've coded the model to run for one population but need to get it up for
multiple populations (issues with indexing). The other extension would
be a non-centered parameterization.\
I started with the following parameterization. I took one site $k$, and
ignored bags $j$, so that I only modeled trials $i$ as coming from a
population of trials: $$\begin{aligned}
\begin{split}
 [ \bm{\alpha}, \mu, \sigma,  | \bm{n}, \bm{y} ] \propto 
 & 
  \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{i} | n_{i}, \mathrm{logit}^{-1}(\alpha_{i}) ) 
 \\ & \times \mathrm{normal} ( \alpha_{i}  | \mu, \sigma )
  \\ & \times \mathrm{normal} ( \mu | 0 , 100 ) \mathrm{uniform} ( \sigma | 0,100).
  \end{split}\end{aligned}$$

I then tried to ignore site and give each bag at a single site $k$ its
own prior. I don't know if I coded this incorrectly but this model **did
not fit well**. In any case this amounted to modeling trial $i$ in bag
$j$ as: $$\begin{aligned}
\begin{split}
 [ \bm{\alpha}, \bm{\mu}, \bm{\sigma},  | \bm{n}, \bm{y} ] \propto 
 & \prod_{j=1}^{J}   
  \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{ij} | n_{ij}, \mathrm{logit}^{-1}(\alpha_{ij}) ) 
 \\ & \times \mathrm{normal} ( \alpha_{ij}  | \mu_{j}, \sigma_{j} )
  \\ & \times \mathrm{normal} ( \mu_{j} | 0 , 100 ) \mathrm{uniform} ( \sigma_{j} | 0,100).
  \end{split}\end{aligned}$$

I then tried to change the data that I worked with. Rather than using
individual trials, I summed all $n$ attempts and $y$ successes across
all trial for a bag. This gave me one data point per bag. I first
modeled one site $k$ with bags $j$ (now equal to trials $i$):
$$\begin{aligned}
\begin{split}
 [ \bm{\alpha}, \mu, \sigma,  | \bm{n}, \bm{y} ] \propto 
 & 
  \prod_{j=1}^{J} 
   \mathrm{binomial} ( y_{j} | n_{j}, \mathrm{logit}^{-1}(\alpha_{j}) ) 
 \\ & \times \mathrm{normal} ( \alpha_{j}  | \mu, \sigma )
  \\ & \times \mathrm{normal} ( \mu | 0 , 100 ) \mathrm{uniform} ( \sigma | 0,100).
  \end{split}\end{aligned}$$

I then added multiple sites to the model. This meant giving each site
its own prior distribution defined by $\mu_k$ and $\sigma_k$ and is
written as: $$\begin{aligned}
  \begin{split}
 [ \bm{\alpha}, \bm{\mu}, \bm{\sigma},  | \bm{n}, \bm{y} ] \propto 
 &  \prod_{K=1}^{K} 
  \prod_{j=1}^{J} 
   \mathrm{binomial} ( y_{jk} | n_{jk}, \mathrm{logit}^{-1}(\alpha_{jk}) ) 
 \\ & \times \mathrm{normal} ( \alpha_{jk}  | \mu_{k}, \sigma_{k} )
  \\ & \times \mathrm{normal} ( \mu_{k} | 0 , 100 ) \mathrm{uniform} ( \sigma_{k} | 0,100).
  \end{split}\end{aligned}$$

Seed bag experiments {#seed-bag-experiments .unnumbered}
--------------------

In October (year $t$), we buried 10 5 $\times$ 5-cm nylon mesh bags at
each site, each containing 100 seeds collected at the site in June-July.
In January (year $t+1$), we removed these 10 bags and counted the number
of germinated seedlings and the number of ungerminated, intact seeds in
each bag. We then returned the ungerminated, intact seeds to the
resealed bag and returned the bag to the field. In October (year $t+1$),
we removed these bags and counted the number of ungerminated, intact
seeds. We collected the following data:

-   $n_{ijt}$ = observed count of seeds in the seed bags at the start of
    the experiment in October in the $i^{th}$ bag, from the $j^{th}$
    site, in the $t^{th}$ year, assumed to be measured perfectly

-   $y_{_{\mathrm{intact}} ijt}$ = observed count of ungerminated,
    intact seeds in the seed bags in January in the $i^{th}$ bag, from
    the $j^{th}$ site, in the $t^{th}$ year, assumed to be measured
    perfectly

-   $y_{_{\mathrm{germ}} ijt}$ = observed count of germinated seedlings
    in the seed bags in January in the $i^{th}$ bag, from the $j^{th}$
    site, in the $t^{th}$ year, assumed to be measured perfectly

-   $y_{_{\mathrm{total}} ijt}$= observed count of ungerminated, intact
    seeds plus germinated seedlings in the seed bags in January in the
    $i^{th}$ bag, from the $j^{th}$ site, in the $t^{th}$ year, assumed
    to be measured perfectly

-   $y_{_{\mathrm{surv}} ijt}$ = observed count of ungerminated, intact
    seeds in the seed bags in October in the $i^{th}$ bag, from the
    $j^{th}$ site, in the $t^{th}$ year, assumed to be measured
    perfectly

The proportion of seeds that germinate is given by P($G|V$) $\times$
P($V$). Probability of being viable is estimated separately (see section
on viability trials) which means that the estimate for $\gamma$ is the
probability of seeds that germinate given that they're viable. The seeds
that are viable but do not germinate P($G^C|V$) $\times$ P($V$) are
dormant, which is then the product of not germinating and being viable.\
We modeled\* seed survival and germination in the seed bags as:

$$\begin{aligned}
  \begin{split}
 [ \bm{\phi}, \bm{\gamma}, \bm{\rho} | \bm{n}, \bm{y_{\mathrm{total}}},  \bm{y_{\mathrm{germ}}},  \bm{y_{\mathrm{surv}}} ] \propto 
 & \prod_{t=1}^{T}
  \prod_{j=1}^{J}   
  \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{_{\mathrm{total}} ijt} | n_{ijt}, \phi_{jt} ) 
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{germ}} ijt}  | y_{_{\mathrm{total}} ijt} , \gamma_{jt} )
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{surv}} ijt}  | y_{_{\mathrm{total}} ijt} - y_{_{\mathrm{germ}} ijt}  , \rho_{jt} )
 \\ & \times \mathrm{beta} ( \phi_{jt} | 1,1 ) \mathrm{beta} ( \gamma_{jt} | 1,1) \mathrm{beta} ( \rho_{jt} | 1,1 )
  \end{split}\end{aligned}$$

where

-   $\phi_{j}$ = the true, unobserved proportion of seeds that remain
    intact in January (the probability of a seed remaining intact) at
    the $j^{th}$ site, in the $t^{th}$ year

-   $\gamma_{jt}$ = the true, unobserved proportion of seeds that
    germinate (the probability of an intact seed germinating) at the
    $j^{th}$ site, in the $t^{th}$ year

-   $\rho_{jt}$ = the true, unobserved proportion of seeds that remain
    intact in October (the probability of a seed remaining intact) at
    the $j^{th}$ site, in the $t^{th}$ year

We add the viability trials to the joint posterior in the following way,
for bags $i$ at a single site $j$: $$\begin{aligned}
  \begin{split}
 [ \phi, \gamma, \rho, \bm{\alpha} | \bm{n}, \bm{n_{\mathrm{viab}}}, \bm{y_{\mathrm{total}}},  \bm{y_{\mathrm{germ}}},  \bm{y_{\mathrm{surv}}}, \bm{y_{\mathrm{viab}}} ] \propto 
 & \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{_{\mathrm{tot}} i} | n_{i}, \phi ) 
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{germ}} i}  | y_{_{\mathrm{tot}} i} , \mathrm{f}( \gamma , \alpha) )
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{surv}} i}  | y_{_{\mathrm{tot}} i} - y_{_{\mathrm{germ}} i}  , \rho )
 \\ & \times  \mathrm{binomial} ( y_{_{\mathrm{viab}} i} | n_{_{\mathrm{viab}} i}, \mathrm{logit}^{-1}(\alpha_{i}) ) 
 \\ & \times \mathrm{beta} ( \phi | 1,1 ) \mathrm{beta} ( \gamma | 1,1)  \mathrm{beta} ( \rho | 1,1 ) 
  \\ & \times \mathrm{normal} ( \alpha_{i}  | \mu, \sigma )
  \\ & \times \mathrm{normal} ( \mu | 0 , 100 ) \mathrm{uniform} ( \sigma | 0,100).
  \end{split}\end{aligned}$$

where
$\mathrm{f}( \gamma , \alpha) = \gamma \times ( \mathrm{logit}^{-1}(\alpha_{i}))^\frac{1}{3}$.\
We fit this models with JAGS. In order to evaluate the effect of the
prior, we obtained estimates for all parameters with a noninformative
beta(1,1) prior and the informative prior on the logit transformed
$\alpha$ parameter. In the derived quantities block, we calculated the
dormancy for each bag $(1-g)*v$. Question is how to get dormancy for the
site because viability is bag level. We simulate data from this model
and calculate test statistics.\
Model runs for 2 sites with no missing data. Problems: how to deal with
missing data (e.g. no viability trials), whether to take bag-level or
site-level viability, which test statistics to use, how/whether to
evaluate how much the posterior for viability changes after joint
estimation.

Correlation {#correlation .unnumbered}
-----------

Venable (2007) estimated the fraction of seeds germinating $G = N/(N+S)$
as follows. The density of seeds germinating ($N$) was estimated by
mapping germinants in 72 1 m$^2$ plots. The density of seeds not
germinating ($S$) was determined from 180 23 cm$^2$ seed cores. Venable
states that the soil cores sample **viable non-germinating seeds**, as
they are collected each year after the germination season but before new
seeds fall.\
Venable (2007) estimated per capita reproductive success associated with
germination using data on per capita survival from germination to
reproduction and per capita fecundity of survivors. This meant
multiplying the per capita probability of survival from germination to
reproduction by the average per capita reproduction of survivors.\
Venable (2007) estimated the risk associated with germination as the
geometric standard deviation of per capita reproductive success
(exp(SD\[ln(per capita reproductive success)\])), which he states is the
standard deviation of proportional changes.\
The first step would be to get site-level estimates for (1) dormancy or
germination fraction and (2) per capita reproductive success. The
straightforward thing to do would be to put everything in one model and
get posteriors for individual parameters before multiplying them to get
estimates with a distribution. We could then take the correlation of
these distributions. Alternatively we could get the correlation in the
MCMC sampling, calculating the correlation at each iteration in the
sampler.\
Monica and I discussed three potential measures for germination:

-   $g_1$: the probability that a seed that is intact in January
    germinates

-   $s_1g_1$: effective emergence

-   $s_1(1-g_1)s_2$: effective survival of seeds

-   Venable's germination fraction $N/(N+S)$ would be the probability of
    a seed emerging in January. This would be equivalent to
    $g_1v_1^{1/3}$

-   true dormancy would be entering the seed bank, not germinating but
    being viable

We add the viability trials to the joint posterior in the following way,
for bags $i$ at a single site $j$: $$\begin{aligned}
  \begin{split}
 [ \phi, \gamma, \rho, \bm{\alpha} | \bm{n}, \bm{n_{\mathrm{viab}}}, \bm{y_{\mathrm{total}}},  \bm{y_{\mathrm{germ}}},  \bm{y_{\mathrm{surv}}}, \bm{y_{\mathrm{viab}}} ] \propto 
 & \prod_{i=1}^{I} 
   \mathrm{binomial} ( y_{_{\mathrm{tot}} i} | n_{i}, \phi ) 
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{germ}} i}  | y_{_{\mathrm{tot}} i} , \mathrm{f}( \gamma , \alpha) )
 \\ & \times \mathrm{binomial} ( y_{_{\mathrm{surv}} i}  | y_{_{\mathrm{tot}} i} - y_{_{\mathrm{germ}} i}  , \rho )
 \\ & \times  \mathrm{binomial} ( y_{_{\mathrm{viab}} i} | n_{_{\mathrm{viab}} i}, \mathrm{logit}^{-1}(\alpha_{i}) ) 
 \\ & \times \mathrm{beta} ( \phi | 1,1 ) \mathrm{beta} ( \gamma | 1,1)  \mathrm{beta} ( \rho | 1,1 ) 
  \\ & \times \mathrm{normal} ( \alpha_{i}  | \mu, \sigma )
  \\ & \times \mathrm{normal} ( \mu | 0 , 100 ) \mathrm{uniform} ( \sigma | 0,100).
  \end{split}\end{aligned}$$

Our variance-covariance matrix $C_1$ includes the variances on the
diagonal and covariances on the off-diagonal. Here, we include the
variance of germination probabilities and the variance of interannual
reproductive success. The value $\rho$ gives the correlation between
germination probability and interannual reproductive success. This gives
the survival/germination estimate as a site-level estimate $\alpha_g$
plus a year-site effect $\alpha_t$. We are interested in the correlation
between the site-level estimate $\alpha_g$ and the variance \... I guess
the goal would be to get estimates for seedling survival to fruiting,
fruits per plant, and seed per fruit and multiply those. That could be a
derived quantity in a 3 part model. The same model might include
estimates for dormancy. Both could be calculated at the site level and
the correlation of interest would be between the parameter for
site-level germination probabilities. Both would be RVs and multiplying
them obviates the need for bootstrapping.

$$\begin{aligned}
y_{i,s} \sim \mathrm{binomial}(\hat{y_{s}}) \\
\mathrm{logit}(\hat{y}_{i,s}) = \alpha_g + \alpha_t\end{aligned}$$

$$\alpha_s =
  \begin{bmatrix}
   \alpha_g \\
   \alpha_r
   \end{bmatrix}$$

$$\alpha_s \sim \mathrm{MVN}(\bm{\mu},\bm{\Sigma})$$

$$\alpha_s =
  \begin{bmatrix}
   \mu_g \\
   \mu_r
   \end{bmatrix}$$

$$\bm{\Sigma} =
  \begin{bmatrix}
   \sigma_1 \sigma_1 & \sigma_1 \sigma_2 \rho \\
   \sigma_1 \sigma_2 \rho & \sigma_2 \sigma_2   
   \end{bmatrix}$$

Extra material {#extra-material .unnumbered}
--------------

The factored joint distribution is represented visually by the
corresponding directed acyclic diagrams:

and

Equivalent notation would be:

$$\begin{aligned}
 [ \bm{\phi}, \bm{\gamma}, \bm{\rho} | \bm{n}, \bm{y_{\mathrm{total}}}, \bm{y_{\mathrm{germ}}}, \bm{y_{\mathrm{surv}}} ] \propto 
 & \prod_{t=1}^{T}
  \prod_{j=1}^{J}   
  \prod_{i=1}^{I} 
   [ y_{_{\mathrm{total}} ijt} | n_{ijt}, \phi_{jt} ] 
 \\ & \times [ y_{_{\mathrm{germ}} ijt}  | y_{_{\mathrm{total}} ijt} , \gamma_{jt} ]
 \\ & \times [ y_{_{\mathrm{surv}} ijt}  | y_{_{\mathrm{total}} ijt} - y_{_{\mathrm{germ}} ijt}   , \rho_{jt} ]
 \\ & \times [\phi_{jt}] [\gamma_{jt}] [\rho_{jt}]\end{aligned}$$

where

$$\begin{aligned}
y_{_{\mathrm{total}} ijt} & \sim \text{binomial}( n_{ijt}, \phi_{jt} ) 
\\ y_{_{\mathrm{germ}} ijt} & \sim \text{binomial}( y_{_{\mathrm{total}} ijt} , \gamma_{jt} )
\\ y_{_{\mathrm{surv}} ijt} & \sim \text{binomial}( y_{_{\mathrm{total}} ijt} - y_{_{\mathrm{germ}} ijt}  , \rho_{jt} )
\\ \phi_{jt} & \sim \text{beta}( 1, 1)
\\ \gamma_{jt} & \sim \text{beta}( 1, 1)
\\ \rho_{jt} & \sim \text{beta}( 1, 1).\end{aligned}$$

Code {#code .unnumbered}
----

I implemented the model to estimate seed survival and germination in R
with the following JAGS code block:

        model { 
        
        # priors
        for(j in 1:nsites){
          for(i in 1:nyears){ 
            ps[j,i] ~ dbeta(1, 1) 
            pg[j,i] ~ dbeta(1, 1)
            pr[j,i] ~ dbeta(1, 1)
          }
        }
        
        # likelihood
        for (i in 1:N){
            yt[i] ~ dbin(ps[site[i],year[i]], n[i])
            yg[i] ~ dbin(pg[site[i],year[i]], yt[i])
            yo[i] ~ dbin(pr[site[i],year[i]], yt[i]-yg[i])
        } 
    }

I implemented the model to estimate viability in R with the following
JAGS code block:

        model { 
        
        # priors
        for(j in 1:nsites){
          for(i in 1:nyears){ 
            for(k in 1:nbags)}
                v[j,i,k] ~ dbeta(1, 1) 
                    }
            }
        }
        
        # likelihood
        for (i in 1:N){
            yg[i] ~ dbin(v[site[i],year[i],bag[i]], ng[i])
            yv[i] ~ dbin(v[site[i],year[i],bag[i]], nv[i])
        } 
    }

I implemented the model to estimate seed survival and germination in R
with the following JAGS code block:

        model { 
        
        # priors
        for(j in 1:nsites){
          for(i in 1:nyears){ 
            ps[j,i] ~ dbeta(1, 1) 
            pg[j,i] ~ dbeta(1, 1)
            pr[j,i] ~ dbeta(1, 1)
             }
        }
        
        for(i in 1:N){
        v[i] ~ dbeta(1 + yv[i], 1+ nv[i] -yv[i])
        }
        
        # likelihood
        for (i in 1:N){
            yt[i] ~ dbin(ps[site[i],year[i]], n[i])
            yg[i] ~ dbin(pg[site[i],year[i]]*(v[i])^(1/3), yt[i])
            yo[i] ~ dbin(pr[site[i],year[i]], yt[i]-yg[i])
        } 
    }
