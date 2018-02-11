Title: Maslov's order book model
Date: 2018-05-08 08:00
Author: Aleksejus Kononovicius
Tags: Interactive models, financial markets, order book
Slug: maslovs-order-book-model
Status: draft
Image_url: uploads/2018/maslovs-order-book-model.png

Previously we have discussed what [order book]({filename}/articles/2018/what-the-order-book-is.md) is. We have also discussed simplified model inspired by physics ([here]({filename}/articles/2018/bak-order-book-model.md). Let us now consider another simple model [cite id="Maslov2000PhysA"], which appears to be a bit more realistic model of the order book.

## The model

Strictly speaking we cannot classify Maslov's model as an agent-based model because this model does not have agents in traditional sense. In this model it assumed that at each time tick one agent comes out of the pool of agents and submits his order.

The submitted order could be either bid (buy) or ask (sell) order with equal probabilities. Also the order could be either limit (with probability \\\( p_{lim} \\\)) or market (with probability \\\( 1-p_{lim} \\\)) order.

If the order is a market order and there is at least one order on the suitable (opposite) side of the order book, then both orders are executed and the new market price is set. Namely, market order is matched with the best available order from the opposite side of the order book and the limit order is removed from the order book. In this post we use \\\( P \\\) to denote the natural logarithm of the market price (or, alternatively, log-price).

If the order is a limit order, then it will be placed into the order book. Before placing the order into the order book, we must set its limit price. In this model limit price for the order is set randomly. If the order is a bid limit order, then the order's limit price is picked randomly from the interval \\\( (P-\Delta_{max},P) \\\). If the order is an ask limit order, then the order's limit price is picked randomly from the interval \\\( (P,P+\Delta_{max}) \\\). If the newly submitted limit order could be executed immediately, then it is executed in the same manner as market order.

Unlike real markets this model does not have order cancellation possibility. Yet in order to avoid overflow problems, we limit each order book side to \\\( O_{max} \\\) orders. If \\\( O_{max} \\\) is reached, then orders are removed starting from the worst (by price) until the order book shrinks to \\\( O_{max} \\\) orders.

The forth model parameter is \\\( \delta \\\), which defines log-price and return sampling period in model time ticks. Hence it is responsible for the model time scale. This parameter also defines window over which the return is estimated, namely the formula is  \\\( r_t = P_t - P_{t-\delta} \\\).

## Interactive applets

In the [previous text]({filename}/articles/2018/what-the-order-book-is.md) we have already presented a simple implementation of this model to illustrate how the order book works. Here we once again share the same app as you can now look at it from a different perspective. Unlike another app at the end of the text, this app has fixed model parameter values:  \\\( p_{lim}=0.65 \\\), \\\( \Delta=3 \\\), \\\( \delta=1 \\\) (the figure is updated after each time tick) and \\\( O_{max} = 10000 \\\).

[html5-interactive
src="/uploads/models/maslov-order-book-model/ob-vizualization-en.html" width="515"
height="360" mode="iframe"]

The other app we would like to share in this post is more flexible, it allows to change the four parameters discussed in the text. You can change the parameter values and observe how they impact the relevant, log-price and absolute return, time series (bottom figures) as well as the main statistical properties, the probability density function and the power spectrum density, of the absolute return time series (top figures).

[html5-interactive
src="/uploads/models/maslov-order-book-model/index.html" width="515"
height="490" mode="iframe"]

<hr/>

![esf logo]({filename}/uploads/2018/esf.png){.float-right}

**Acknowledgement.** This post was written while reviewing literature for my
postdoctoral fellowship ''Physical modeling of order-book and opinion dynamics''
([09.3.3-LMT-K-712-02-0026](http://www.esinvesticijos.lt/lt/applications/sandoriu-knygos-ir-nuomoniu-dinamikos-modeliavimas-fizikos-metodais)).
The fellowship is funded by the European Social Fund under the No 09.3.3-LMT-K-712
''Development of Competences of Scientists, other Researchers and Students
through Practical Research Activities'' measure.

