---
title: The Semilattice Row
author: Dakotah Lambert
...

## Review:

In previous sessions, we've discussed the regular and star-free classes
at the top of our finite-strucure hierarchy,
and the trivial languages (𝟏) and extensions thereof at the bottom.


## Varieties:

A variety 𝐕 of semigroups (or monoids)
is a collection satisfying the following:

* 𝐕 is closed under taking products: if 𝐀∈𝐕 and 𝐁∈𝐕, then 𝐀×𝐁∈𝐕
* 𝐕 is closed under taking subsemigroups (or submonoids)
* 𝐕 is closed under quotients

These properties mean that any class of languages
defined by having their syntactic monoids belong to some variety 𝐕
must necessarily be closed under the Boolean operations.
The union and intersection are computed by

1. Finding the product of the state machines recognizing them
   (i.e. of their syntactic monoids),
2. Finding the submonoid reachable from the start state, then
3. Computing the quotient of the result over the Myhill relation.

The first step produces some automaton,
the second removes unreachable states,
and the third merges those that remain
to give us something minimal again.
Using the Nerode relation instead of the Myhill relation
would yield a canonical DFA,
but that might not be a monoid.

So this gives us closure under union and intersection.
The fact that a language and its complement share the same monoid
gives us closure under complementation.
That's all of the Boolean operations.


## Semilattices (a.k.a. Commutative Bands)

If you have a class of languages and you add restrictions,
you get a subclass.
Or if you remove restrictions, you get a superclass.
Recall that a monoid is in 𝟏 iff it has just a single element, denoted 1.
There's only one such monoid,
corresponding to two languages: Σ\* and ∅.
This monoid has the following properties:

* It's commutative: 𝑎⁢𝑏=𝑏⁢𝑎 for all 𝑎 and 𝑏 (both can only be 1)
* It's idempotent: 𝑎⁢𝑎=𝑎 for all 𝑎 (𝑎 can only be 1)
* It has inverses: for each 𝑎, there exists 𝑎⁻¹
  such that 𝑎⁢𝑎⁻¹=𝑎⁻¹⁢𝑎=1 (both 𝑎 and its inverse are 1)
* It's null: there exists an element 0 where 𝑎⁢𝑏=𝑏⁢𝑎=0 (here, 0=1)

The class 𝐋𝟏 is a superclass of 𝟏 because
rather than requiring the whole monoid to be in 𝟏,
we only require its local subsemigroups 𝑒⁢𝑆⁢𝑒 to be in 𝟏.
This is a relaxation of some properties.
But we might also just decide to remove some from the above list.
If we keep only the **commutative** and **idempotent** properties,
we have a semilattice!
That's not a profound theorem or anything by the way,
just the definition of what a semilattice is.

Here is a sample language whose monoid is a semilattice:
<br />
![A state machine with five states, numbered 1 through 5.
  The start state is 1, and all states but 5 are accepting.
  State 1 has transitions to 4, 2, and 3 on a, b, and c respectively.
  State 2 has transitions to 5, 2, and 3 on a, b, and c respectively.
  State 3 is a sink.
  State 4 has transitions to 4, 5, and 3 on a, b, and c respectively.
  And state 5 has self-loops on a and b, and transitions to 3 on c.
 ](./na-or-nb-or-c.svg)
<br />
Its syntactic monoid is actually the same shape:
<br />
![The preceding state machine,
  where states 1 through 5 have been relabeled as
  empty string, a, c, b, and ba, respectively.
 ](./na-or-nb-or-c-mon.svg)

|  ⋅ |  λ |  a |  b | ba |  c |
|---:|---:|---:|---:|---:|---:|
|  λ |  λ |  a |  b | ba |  c |
|  a |  a |  a | ba | ba |  c |
|  b |  b | ba |  b | ba |  c |
| ba | ba | ba | ba | ba |  c |
|  c |  c |  c |  c |  c |  c |

Inspecting the main diagonal, each element is idempotent.
But also, this main diagonal is a mirror;
the monoid is commutative.
Commutative and idempotent, it's a semilattice.

What does it *mean* for a language to be commutative and idempotent?
Consider two words: "abacab" and "bacba".

* By commutativity, we can swap adjacent letters
* Iterating this, ⟦abacab⟧ = ⟦aaabbc⟧ and ⟦bacba⟧ = ⟦aabbc⟧
* All elements are idempotent, 𝑥⁢𝑥=𝑥.
* So we can replicate letters as needed
* ⟦aabbc⟧ = ⟦aaabbc⟧,
* So ⟦bacba⟧=⟦abacab⟧ — they must be treated identically
* This generalizes!
* 𝐿 is a semilattice language (𝐂𝐁, for "commutative band")
  iff words are treated identically
  whenever they contain the same set of letters.
* This is locally testable or piecewise testable
  for a factor width of 𝑘=1.


## Extensions

Semilattices form a variety.
So we can construct a "locally-" extension
and a tier-based extension of that.
"Locally a semilattice"
turns out to be the same as "locally testable",
so we'll denote it as such: LT.

This is the DFA for the language in which all words contain "ab":
<br />
![A DFA of three states, labeled 1 through 3.
  State 1 transitions to 2 on a, and has self-loops on b and c.
  State 2 transitions to 2, 3, or 1 on a, b, or c, respectively.
  State 3 is a sink, as well as being the only accepting state.
 ](./ab.svg)
<br />
Its syntactic monoid is as follows:
<br />
![The syntactic monoid of the preceding DFA.
  There are six states: empty string, a, b, c, ab, and ba.
  The Cayley table is given below.
 ](./ab-mon.svg)

|  ⋅ |  λ |  a |  b |  c | ba | ab |
|---:|---:|---:|---:|---:|---:|---:|
|  λ |  λ |  a |  b |  c | ba | ab |
|  a |  a |  a | ab |  c |  a | ab |
|  b |  b | ba |  b |  b | ba | ab |
|  c |  c |  a |  c |  c |  a | ab |
| ba | ba | ba | ab |  b | ab | ab |
| ab | ab | ab | ab | ab | ab | ab |

Notice that ⟦ba⟧ is not an idempotent,
so this language isn't in 𝐂𝐁.
(It also lacks commutativity.)
But let's find 𝑒⁢𝑆⁢𝑒,
remembering to exclude the empty string
because we are in the semigroup and not the monoid.
Recall that 𝑒 is an idempotent,
𝑒⁢𝑆 is everything reachable from it in the graph,
and 𝑒⁢𝑆⁢𝑒 is the set you get when multiplying each element of 𝑒⁢𝑆 by 𝑒:

|  𝑒 |      𝑒⁢𝑆     |   𝑒⁢𝑆⁢𝑒   |
|:--:|:-----------:|:-------:|
|  a | {a, c, ab}  | {a, ab} |
|  b | {b, ba, ab} | {b, ab} |
|  c | {a, c, ab}  | {c, ab} |
| ab | {ab}        | {ab}    |

* As noted, 𝑀 isn't idempotent or commutatitve,
  so the language isn't in 𝐂𝐁
* The 𝑒⁢𝑆⁢𝑒 aren't singleton,
  so the language isn't Generalized Definite (𝐋𝟏)
* But each 𝑒⁢𝑆⁢𝑒 is itself in 𝐂𝐁 (try it, test the properties)
* The language is locally a semilattice — it's LT

And of course if we draw in self-loops everywhere
on some new symbol d,
then we have something tier-based locally testable, TLT.

## Summary

For any given variety 𝐕,
there is a corresponding "locally" class 𝐋𝐕
and a tier-based extension of that, 𝐓𝐋𝐕.
The 𝐋𝐕 is also a variety, but 𝐓𝐋𝐕 is not,
as the latter is not closed under products.
In the table below, inclusions hold downward and leftward.

|   𝐕 | 𝐋𝐕 | 𝐓𝐋𝐕 |
|:---:|:---:|:---:|
| Reg |     |     |
|  SF |     |     |
| 𝐂𝐁 |  LT | TLT |
|   𝟏 |  GD | TGD |

If we haven't mentioned it yet,
the variety of finite monoids (what regular languages are)
is called 𝐅𝐢𝐧,
and the aperiodic ones (for star-free)
are 𝐀𝐩.
Note: there is a language class called Fin,
which should not be confused with the monoid variety 𝐅𝐢𝐧.
