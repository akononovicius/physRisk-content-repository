Title: Facebook contest data set: Reproducing day-night cycle 
Date: 2018-10-02 08:00
Author: Aleksejus Kononovicius
Tags: facebook, data science, marketing, Bass model, Interactive models
Slug: facebook-contest-data-set-reproducing-day-night-cycle
Status: draft
Image_url: uploads/2018/fb-comm-bass.png

During summer hiatus I have promised to look into a data set I have extracted
from [one particular Facebook contest](https://www.facebook.com/HAPPYLietuva/photos/a.1208205755944127.1073741828.1207052856059417/1699711786793519/).
While many Facebook contests are not based on any logical reasoning, this
contest appeals to me as it appears to require at least some thought or
expertise.

Last time I have briefly explored the [data set]({filename}/articles/2018/fb-contest.md).
Now I try to build models for these observations. This time I will consider the
day-night cycle.

<!--more-->

## Building the Bass diffusion model with a day-night cycle

In our exploration we have encountered a peculiar pattern. We have observed the
expected growth of the number of comments, but we have also observed a couple
saturation plateaus. I have speculated that these plateaus are related to the
sleeping habits of the contest participants. I will build these habits into
the well-known [Bass diffusion model](/tag/bass-model/). I have selected this
model, because it otherwise replicates the general shape of growth.

Now lets assume that there are two special times:

* after \\\( T\_{\text{wakeup}} \\\) each day people start waking up (at the
rate of \\\( \lambda\_{\text{wakeup}} \\\) per person per unit of time),
* after \\\( T\_{\text{sleep}} \\\) each day people start going to sleep (at the
rate of \\\( \lambda\_{\text{sleep}} \\\) per person per unit of time).

The people who are not asleep can submit their comment to the contest (but
no more than once). The probability that they will comment is proportional to
the number of comments present.

This model can be easily implemented using the Gillespie method [cite id="Gillespie1977"].
The program will have to consider five different event rates: two going to sleep
rates, two waking up rates and single commenting rates. These rates must be
updated after every event occurring as well as at those special times.

We invite you to explore the dynamics of the modified model by using the
interactive HTML5 app bellow. The app will present you with two figures: the top
figure will show the total number of comments (red curve) as well as the total
number of awake agents (blue curve), the bottom figure will show the number of
new comments per 15 minute windows (red curve).

[html5-interactive
src="/uploads/models/bass-day-night/index.html" width="515"
height="540" mode="iframe"]

