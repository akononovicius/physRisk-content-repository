Title: KLDivergence: Debunking claims of election rigging
Date: 2020-12-01 08:00
Author: Aleksejus Kononovicius
Tags: video, KLDivergence, opinion dynamics, statistics
Slug: kldivergence-debunking-claims-of-election-rigging
Status: published

Another group of people using statistical methods have shown that Biden has
stolen Trump's votes! To be more precise, they have misused statistical methods
to prove their point. Well as you know there are
[lies, damned lies and statistics](https://en.wikipedia.org/wiki/Lies,_damned_lies,_and_statistics).<!--more-->

The "proof" relies on a fact that multiple elections were held at the same time
(at least in some states). The people who have conducted the analysis have
calculated the difference between the fraction of votes for Trump (in
presidential elections), \\\( v\_t \\\) and the fraction of votes for Republican
candidates in other elections, \\\( v\_r \\\):

\begin{equation}
    \Delta = v\_t - v\_r .
\end{equation}

They have found that \\\( \Delta \\\) decreases with \\\( v\_r \\\). Their claim
is that with larger \\\( v\_r \\\) we should observe larger \\\( v\_t \\\),
therefore \\\( \Delta \approx 0 \\\). Which appears logical from the first
glance, but is actually false.

Let us imagine that there is some non-zero probability of defecting (voting
for president representing another party), \\\( p\_d \\\). Assuming that there
were \\\( 1 - v\_r \\\) votes cast for Democrats (equivalent to assumption that
there are no third parties), fraction of votes cast for Trump will be given by:

\begin{equation}
    v\_t = v\_r (1-p) + (1-v\_r) p .
\end{equation}

Fraction of votes cast for Trump is a sum of votes from non-defecting
Republican voters and votes from defecting Democrat voters. Let us now obtain
the expression for difference:

\begin{equation}
    \Delta = \left[ v\_r (1-p) + (1-v\_r) p \right] - v\_r = 
           = p ( 1 - 2 v\_r ) .
\end{equation}

So, it appears qualitatively the same as this simplistic model predicts. And
we have no election rigging built into the model.

A bit more details along with visual exploration of slightly more complicated
version of this model can be found in an excellent video by KLDivergence. We
invite you to watch [it](https://www.youtube.com/watch?v=MANdMBpMghw) as well as
a [follow up video](https://www.youtube.com/watch?v=fH0Z-8563-E), which goes
into even more details (explaining how the relationship between \\\( \Delta \\\)
and \\\( v\_r \\\) can be nonlinear for this specific data set).

[youtube v="etx0k1nLn78"]
