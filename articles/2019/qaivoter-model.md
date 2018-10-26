Title: q-Voter model with non-conformers
Date: 2019-04-16 08:00
Author: Aleksejus Kononovicius
Tags: Interactive models, Agent-based models, opinion dynamics, voter model, non-conformity
Slug: q-voter-model-with-non-conformers
Status: draft
Image_url: uploads/2019/qaivoter-model.png

[Two years ago]({filename}/articles/2017/kodel-individualiu-agentu-savybes-gali-buti-nesvarbios.md)
we have already explained that properties of individual agents in some cases do
not matter, because they average out. But in some cases this minute details can
have interesting effects on the dynamics of the social system.

Here we discuss a generalization of the [q-Voter model]({filename}/articles/2019/qvoter-model.md)
using so-called diamond model of social response [cite id="Nail2016APPA"]. An
interesting result reported in [cite id="Nail2016APPA"] is that two different
psycho-social approaches to non-conformative behavior generate somewhat different
results when introduced into the [q-Voter model]({filename}/articles/2019/qvoter-model.md).<!--more-->

## The diamond model

The core idea of the diamond model is that there are four possible responses
to an external influence [cite id="Willis1965"]:

* **Conformity.** After being exposed to an opposite opinion, agent changes his
opinion to conform.
* **Independence.** After being exposed to some opinion, agent ignores it and
keeps his own.
* **Anti-conformity.** After being exposed to some opinion, agent changes his
opinion to disagree with it.
* **Variability.** After being exposed to some opinion, agent changes his opinion
regardless of the source.

Conformative behavior is already present in numerous sociophysical models. What
is missing from the most of them is details about non-conformative behavior.
Usually these details are hand-waived and simple noise is used to reflect
non-conforming behavior in agents. Yet as we can see there are three types
of non-conformist behaviors.

[cite id="Nail2016APPA"] builds two different models based on the
[q-Voter model]({filename}/articles/2019/qvoter-model.md). First one (A model)
incorporates anti-conformist behavior, second one (I model) incorporates
independence and variability (which are actually two sides of the same, random
behavior, coin). In the article and its precursor articles (e.g., [cite id="Nyzka2012PRE"])
it is shown that these two models have different critical values.

Before discussing the critical values let us provide an algorithms for each
model. A model:

1. Pick a random agent.
1. With probability \\\( p_a \\\) agent is anti-conformist. He will disagree
with his \\\( q \\\)-panel. Otherwise agent is conformist and will agree with
his \\\( q \\\)-panel (as usual in the
[q-Voter model]({filename}/articles/2019/qvoter-model.md)).
1. Select \\\( q \\\) neighbors of the selected agent. If all neighbors have
the same opinion, the selected agent changes his opinion to either agree (if
he is conformist) or disagree (if he is anti-conformist) with the selected
\\\( q \\\)-panel.

I model:

1. Pick a random agent.
1. With probability \\\( p_i \\\) agent is independent. His opinion will be
flipped with probability \\\( 1/2 \\\). Otherwise agent is conformist and will
agree with his \\\( q \\\)-panel (as usual in the
[q-Voter model]({filename}/articles/2019/qvoter-model.md)).
1. If the agent is conformist, then select \\\( q \\\) neighbors of his. If all
neighbors have the same opinion, the selected agent changes his opinion to agree
with the selected \\\( q \\\)-panel.

Critical values, when the model is executed on the complete graph, are the following:
for the A model
\begin{equation}
p^\*=\frac{q -1}{2 q},
\end{equation}
and for the I model
\begin{equation}
p^\*=\frac{q -1}{q -1 + 2^{q-1}}.
\end{equation}

If the probabilities are larger than the critical probabilities, then disordered
(anti-ferromagnetic) phase should be observed in the dynamics of that model.
Otherwise ordered (ferromagnetic) phase should be observed. Note that for \\\( q>5 \\\)
I model has a rather complicated behavior in the vicinity of critical
probability. Namely, both phases appear to coexist.

## HTML 5 apps

Here we provide two apps, which allows you to explore both A model (the first app)
and I model (the second app). Explore the difference in their dynamics with
larger values of \\\( q \\\) and intermediate probabilities.

[html5-interactive width="515" height="505" mode="iframe"
src="/uploads/models/voter/qavoter.html"]

[html5-interactive width="515" height="505" mode="iframe"
src="/uploads/models/voter/qivoter.html"]

[acknowledge id="postdoc-ak-2017-lit"]
