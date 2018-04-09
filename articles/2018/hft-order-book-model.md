Title: Describing high-frequency trader's behavior in the order book
Date: 2018-09-18 08:00
Author: Aleksejus Kononovicius
Tags: Interactive models, financial markets, order book, kinetic models
Slug: describing-high-frequency-traders-behavior-in-the-order-book
Status: draft
Image_url: uploads/2018/hft-ob-marginal.png

We continue our series of posts on [order book models](/tag/order-book/) by
considering an order book model proposed by a group of scientists from Japan
[cite id="Kanazawa2018PRL, Kanazawa2018arxiv"], which is based on high resolution
data from foreign exchange market. Their work is extremely interesting as
it starts from the empirical observations at the lowest level observable and
is built up to reproduce some empirical observations at the higher levels.
Also the model is analytically tractable using [kinetic theory](/tag/kinetic-models/).

## The model

## Weak, strong and marginal trend following regimes

This model exhibits three distinct behavioral regimes based on how much impact
trend following has. The strength of trend following is well captured by the
\\\( \\tilde c \\\) parameter, which depends on the model parameters as follows [cite id="Kanazawa2018PRL, Kanazawa2018arxiv"]:

\\\[ {\\tilde c} =\\sqrt{\\frac{\\Gamma\(\\alpha+1\)}{\\Gamma\(\\alpha-1\)}} \\frac{c L^{\*}}{\\sigma^2 \\sqrt{2 N}} . \\\]

As the model is based on empirical observations Kanazawa et al. [cite id="Kanazawa2018PRL, Kanazawa2018arxiv"]
estimated the parameter values from their data set. These values are the default ones
in the figures (app screenshots) and app bellow: \\\( c = 6 \\\), \\\( \\Delta p^{\*} = 7.5 \\\) ,
\\\( \\sigma=3.8 \\\) (authors do report a different value, but I believe that
this is a mistype on their part as in that case \\\( \\tilde c \\\) value would
not be a correct one), \\\( \\alpha=3 \\\) and \\\( L^{\*}=15.5 \\\). We have used
\\\( N = 100 \\\) in all our simulations, which consistent with the data set
used in the original paper.

If \\\( \\tilde c \\\) is significantly smaller than 1, then trend following is weak.
In this case diffusive behavior of the HFTs dominates, hence the price change
distribution is approximately Gaussian. Auto-correlation function for the short lags
is noticeably negative.

![weak trend following](/uploads/2018/hft-ob-weak.png "Weak trend following (default parameters, except \\\( \\sigma=14.5 \\\)).")

If \\\( \\tilde c \\\) would be significantly larger than 1, then trend following is
strong. In this case drift behavior of the HFTs dominates. The price change PDF
is exponential, while auto-correlation function for the short lags is noticeably
positive. The auto-correlation function in our app bellow is positive, if last
1024 time ticks (points) include at least one trend reversal. If the current trend
persists for longer than 1024 points, then auto-correlation function will fluctuate
around zero. This is just minor artifact of the algorithm we implemented in the app.

![strong trend following](/uploads/2018/hft-ob-strong.png "Strong trend following (default parameters, except \\\( \\sigma=1.8 \\\)).")

If \\\( {\\tilde c} \\approx 1 \\\), then trend following is marginal. In this case
we observe interplay between the drift and diffusion terms of the HFTs. The price
change PDF is exponential. While the auto-correlation function will fluctuate around
zero. For some parameter sets it will favor negative side, for some -- positive side.

![marginal trend following](/uploads/2018/hft-ob-marginal.png "Marginal trend following (default parameters).")

The empirical estimates point to the third case. The paper reports that marginal
following case is also consistent with empirical facts (price change PDF and
auto-correlation for the short times).

## Interactive applets

To understand the model and its dynamics better you should study the interactive
applets bellow.

The first applet, as has become usual, shows us how the structure of the order
book evolves as the time goes on. Note that unlike in most other cases here we
have relative price on the x axis, thus negative "prices" will also be observed.
Also note that this model uses continuous prices, hence the plot bellow shows
a number of submitted limit orders in the interval \\\( \[ p, p+1 \) \\\). Note
that the shape of the both sides of the order book is symmetric and has shape
similar to the log-normal distribution (similarly as in the
[previously discussed model]({filename}/articles/2018/preis-order-book-model.md)),
but the true expression is different [cite id="Kanazawa2018PRL, Kanazawa2018arxiv"].

[html5-interactive
src="/uploads/models/takayasu-ob-model/ob-vizualization-en.html"
width="520" height="430" mode="iframe"]

The second applet is in certain sense traditional Physics of Risk applet for all
financial market models. Only now every plot was changed somewhat to show the
important feature of this model.

First of all this model uses relative price instead of log-price or price and
"price change" instead of returns. Relative price is measured as a distance in
price ticks from some arbitrarily selected "zero" level. "Price change",
\\\( \\Delta p \\\) is measured as a difference between relative prices at two
different points in time (the temporal distance, \\\( \\Delta t \\\), between
these points is kept constant for consistency).

This model exhibits statistical properties which are different from the ones
we are usually interested in. In this model the price change is distributed
either normally or exponentially (depending on the parameter values), hence
the PDF plot features log-linear axes instead of log-log axis we usually use.

Also instead of plotting power spectral density we plot auto-correlation,
\\\( C \( \\tau \) \\\), function of the price change. \\\( C \( 0 \) \\\)
will be also equal to 1, but other nearby values will behave different depending
on the parameter values. For the sake of speed, we consider only 1024 last
time series points when calculating auto-correlation function, so some
"artifacts" may appear. Note that we show two curves, which will most of the time
over lap. The blue curve shows auto-correlation of the price change time series,
while the yellow curve shows auto-correlation of the absolute price change time
series.

[html5-interactive
src="/uploads/models/takayasu-ob-model/index.html" width="520"
height="530" mode="iframe"]

[acknowledge id="postdoc-ak-2017"]
