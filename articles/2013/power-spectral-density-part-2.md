Title: Power spectral density (part 2)
Date: 2013-03-04 08:17
Author: Aleksejus Kononovicius
Tags: General models, Interactive models, Stochastic models, Brownian motion, Wolfram CDF, methods, white noise, old models, statistical physics
Slug: power-spectral-density-part-2
Status: published

[Last
time](/power-spectral-density-part-1 "Power spectral density (part 1)")
we have written on the power spectral density and we have "analyzed"
deterministic periodic time series. This time we will consider spectral
densities of some stochastic processes.<!--more-->

Spectral density of the white noise
-----------------------------------

As we have already written before, the white noise is a purely random,
non-correlated (possessing no memory), noise. For the white noise the
following is true:


\begin{equation}
 \left\langle \xi(t\_1) \xi(t\_2) \right\rangle =\delta(t\_1 - t\_2) , 
\end{equation}


here \\\(  \xi \\\) is a white noise (formally a function of time),
chevrons denotes averaging over different time moments, while \\\( \delta \\\) is a Dirac delta function.

As such signal has no persistent trends, its spectral density is always
related to the standard deviation, \\\(  \sigma \\\), of the underlying
white noise:


\begin{equation}
 S(\nu) = \sigma^2 . 
\end{equation}


There is no dependence on the frequency, because there is no persistent
trends or alternatively - all trends are reflected equally in the
observed time series.

Spectral density of the Brownian motion
---------------------------------------

Brownian motion, also known as Wiener process or "brown" noise, is a
motion affected by many random perturbations. One of the most well known
examples for such motions is a movements of pollen immersed in water.
The pollen is affected by many hits incoming from the water molecules,
therefore it moves in seemingly random pattern. Mathematically Brownian
motion is defined as a sum, or integral, of the white noise:


\begin{equation}
 \mathrm{d} W(t) = W(t+\mathrm{d} t) - W(t) = \xi(t)\mathrm{d} t , 
\end{equation}



\begin{equation}
 W(t) = \int\limits\_0^t \mathrm{d} W(t) , \quad W\_t =\sum\_{i=0}^t \xi\_i \Delta\_i . 
\end{equation}


The mean of the time series remains zero, but the variance is
proportional to the time. The spectral density of such time series is no
longer constant:


\begin{equation}
 S(\nu) = \frac{\sigma^2}{2 \pi^2 \nu^2} . 
\end{equation}


Spectral density of the Brownian motion with relaxation
-------------------------------------------------------

In most of the real physical situations friction is present, therefore
it proves useful to extend the Brownian motion by implementing some kind
of relaxation term:


\begin{equation}
 \mathrm{d} f(t) = - \gamma f(t) \mathrm{d} t + \sigma\mathrm{d} W(t) . 
\end{equation}


In this spectral density becomes slightly more complex:


\begin{equation}
 S(\nu) = \frac{\sigma^2}{2 \gamma^2 + 2 \pi^2 \nu^2} .
\end{equation}


The mathematical form of spectral density suggests that in certain range
of frequencies, \\\(  \nu \ll \gamma \\\), white noise will prevail,
while for higher frequencies brown noise will be observed.

Geometric Brownian motion
-------------------------

Another interesting take on the Brownian motion is known as geometric
Brownian motion. Generally speaking it is mostly the same as Brownian
motion, but it is not additive, but multiplicative! Namely Brownian
motion occurs on the logarithmic scale. The stochastic differential
equation for the simplified geometric Brownian motion can be
mathematically expressed as follows:


\begin{equation}
 \mathrm{d} f(t) = \sigma f(t) \mathrm{d} W(t) . 
\end{equation}


Spectral densities of the aforementioned stochastic processes
-------------------------------------------------------------

Bellow you should see an interactive CDF program, which enables you to
analyze spectral densities of the stochastic processes discussed above.
\\\(  \sigma \\\) slider is important at all times as it controls the
standard deviation of the underlying (the time series of the other
stochastic processes are derived from it) white noise. \\\(  \gamma \\\)
plays a role only if the Brownian motion is ploted. Most of the spectral
density plots are approximated by a red curves, which stand for the
theoretical expressions of spectral density provided in the text above.

<div id="attachement_2423" class="cdf-embed" style="margin: 0 auto; text-align: center;"><object classid="clsid:612AB921-E294-41AA-8E98-87E7E057EF33" type="application/vnd.wolfram.cdf.text" width="350" height="531"><param name="src" value="/uploads/2013/01/random-spectra-en.cdf"><embed src="/uploads/2013/01/random-spectra-en.cdf" type="application/vnd.wolfram.cdf.text" width="350" height="531"></object></div>

Above you should see a CDF applet. If you do not see it, then please make sure
that you have CDF Player or Mathematica (with CDF support) installed and that
your browser has the corresponding plugin enabled. Also make sure that you are
running newest available CDF Player version. Newest CDF Player version can be
freely downloaded from [http://www.wolfram.com/cdf-player/](http://www.wolfram.com/cdf-player/ "Wolfram CDF Player for Interactive Computable Document Format"). You can also download this [CDF file](/uploads/2013/01/random-spectra-en.cdf) to process it in other means.
