---
title: Introduction
author: Dakotah Lambert
...

* A monoid is a set with an associative operation and an identity
  + Here we considered the free monoid over Σ={a,b,c}, Σ*
  + This is all possible sequences of these letters, with concatenation
  + The identity is the empty sequence
* A formal language 𝐿 is a set of words, a set of sequences.
* Nerode equivalence
  + 𝑥 ~ₙ 𝑦 iff for all 𝑣, 𝑥⁢𝑣∈𝐿 ⟺ 𝑦⁢𝑣∈𝐿
  + Equivalence classes define a minimal DFA
  + Even-a has two classes: ⟦λ⟧ and ⟦a⟧
  + There is a union of classes equal to 𝐿: here ⋃{⟦λ⟧}
  + One-sided, caring only about distinguishability by suffixes
* Myhill equivalence
  + Accounts for distinguishability by prefixes or circumfixes too
  + 𝑥 ~ₘ 𝑦 iff for all 𝑢 and 𝑣, 𝑢⁢𝑥⁢𝑣∈𝐿 ⟺ 𝑢⁢𝑦⁢𝑣∈𝐿
  + A refinement of the Nerode equivalence: can (only) split classes
  + A congruence, so Σ*/~ₘ remains a monoid!
  + This is the **syntactic monoid**.
  + The smallest monoid for which a union of classes can equal to 𝐿
  + Construct the functions from the minimal DFA
  + For even-a, the two relations are identical!
  + ¬a⁢a has only three Nerode classes, but six Myhill classes
* Semigroups: Σ⁺ is Σ* without λ.  Keep ⟦λ⟧ iff reachable.
* ¬a⁢a
  + Table below
  + ⟦λ⟧ is the identity, we can call this 1: 1⁢𝑥=𝑥⁢1=1
  + ⟦aa⟧ is zero: 0⁢𝑥=𝑥⁢0=0
  + Forbidden factors like this are always 0
  + The main diagonal of the table is 𝑥²
  + Idempotents E(M) are where 𝑥²=𝑥: everything but ⟦a⟧
  + Preview: most of the classification problems are based on E(M)

|  ⋅ |  λ |  a |  b | ab | ba | aa |
|---:|---:|---:|---:|---:|---:|---:|
|  λ |  λ |  a |  b | ab | ba | aa |
|  a |  a | aa | ab | aa |  a | aa |
|  b |  b | ba |  b |  b | ba | aa |
| ab | ab |  a | ab | ab |  a | aa |
| ba | ba | aa |  b | aa | ba | aa |
| aa | aa | aa | aa | aa | aa | aa |
