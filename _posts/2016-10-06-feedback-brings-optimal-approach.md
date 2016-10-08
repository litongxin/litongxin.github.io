---
layout: post
title: "Feedback brings optimal approach"
description: "One requirement, four different implementations."
---
We all know ThoughtWorks are hiring the passionate people in consulting, coding and self-learning.     

<span style="color:#0564be">So what makes thoughtworker work better? </span>

Let me tell you a story of my team.
My current project is a UI-heavy application with fancy layout, lively animation and perfect user experience.

One day, our designer gave us responsive mockup for one feature.

<span style="color:#0564be">Mobile:</span>

Selection area has two lines. The left type dropdown has fixed width, the right input box need to be self-adaptive which cover the rest of the space.
Then one GO button follows.

<img src="/asset/images/design-for-mobile.png" width="240px" alt="Mobile Design"/>

<span style="color:#0564be">Tablet:</span>

Selection area becomes one line, the left type dropdown and the right GO button has fixed width, the middle input box need to be self-adaptive.

<img src="/asset/images/design-for-tablet.png" width="400px" alt="Tablet Design"/>

<span style="color:#0564be">Desktop:</span>

Similar with tablet, just consider the line has max-width.

<img src="/asset/images/design-for-desktop.png" width="700px" alt="Desktop Design"/>

Look pretty simple, right?

In fact, it takes **FOUR TIMES** more time than everyone imagine.

The first and regular solution that comes into mind is `position: absolute, left: $fixed-width, ...`
During code review, everyone think *position* is such a jack of all trades, should not use unless no other ways. So we decide to rethink.

Pairing with sarah, she comes up with `display:table-cell, min-width: $fixed-width, max-width:$fixed-width, ...`
This solves the two column (one is fixed, the other is self-adaptive) requirement for mobile version.
But still kind of tricky, need to set *min-width and max-width* to limit width. Also very hard to implement the tablet/desktop version.
So we overthrow current approach. Rethink again.

I suggest to use common two column pattern with `float:left, float:right, margin-left: $fixed-width, ...` for mobile,
adding `margin-right:$fixed-width, margin-top: -$height` for tablet/desktop.


Our premier photographer - Fang says: Why not using New layout mode - *flex* ? Quick win using `display:flex, align-content: space-around, ...`
Unfortunately, flex's good friends `align-items: center, justify-content: center` is not that compatible with iPhone 4 and safari 7.

In the end, using `float` is the final conclusion.

When you read here, I double the following words, you know exactly what I am feeling and what thoughtworker does everyday.

#### What I learn from this:
* Listen other's feedback and take action
* Treat every approach as good as it gets.
* Think twice when using regular way!
* Never stop trying new things.
<small style="color: #0564be">Maybe its adaptability and compatibility is not that good. Still worth trying, at least learn something new.</small>
