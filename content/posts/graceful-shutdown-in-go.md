+++
title = 'Grafecully shutting down in Go'
date = 2024-06-18T21:09:17+02:00
draft = true
+++
### Introuduction
Can you imagine going to a grocery store right around closing time. You run inside, scramble to get everything on your shopping list and as you get to the checkout line the cashier just walks away and goes home? This is essentially what we do to our users when we don't gracefully shut down our applications. 

If we were to arrive at the store and the doors were already closed, we can probably live with the fact that we need to come back tomorrow, but once we are let into the store, we should be able to complete our business right?

*In this post, we will explore how to prevent new customers from entering the store, but also allow the ones already inside to finish up before we close up shop completely.*

### 24/7 Stores
Some might say a grocery store is a bad example becase software should be available 24/7. This is true, but even 24/7 stores need to sometimes temporarily close their doors for maintenance, restocking or other reasons.

