---
title: Introduction
author: Dakotah Lambert
...

* A monoid is a set with an associative operation and an identity
  + Here we considered the free monoid over Î£={a,b,c}, Î£*
  + This is all possible sequences of these letters, with concatenation
  + The identity is the empty sequence
* A formal language ð¿ is a set of words, a set of sequences.
* Nerode equivalence
  + ð¥ ~â ð¦ iff for all ð£, ð¥â¢ð£âð¿ âº ð¦â¢ð£âð¿
  + Equivalence classes define a minimal DFA
  + Even-a has two classes: â¦Î»â§ and â¦aâ§
  + There is a union of classes equal to ð¿: here â{â¦Î»â§}
  + One-sided, caring only about distinguishability by suffixes
* Myhill equivalence
  + Accounts for distinguishability by prefixes or circumfixes too
  + ð¥ ~â ð¦ iff for all ð¢ and ð£, ð¢â¢ð¥â¢ð£âð¿ âº ð¢â¢ð¦â¢ð£âð¿
  + A refinement of the Nerode equivalence: can (only) split classes
  + A congruence, so Î£*/~â remains a monoid!
  + This is the **syntactic monoid**.
  + The smallest monoid for which a union of classes can equal to ð¿
  + Construct the functions from the minimal DFA
  + For even-a, the two relations are identical!
  + Â¬aâ¢a has only three Nerode classes, but six Myhill classes
* Semigroups: Î£âº is Î£* without Î».  Keep â¦Î»â§ iff reachable.
* Â¬aâ¢a
  + Table below
  + â¦Î»â§ is the identity, we can call this 1: 1â¢ð¥=ð¥â¢1=1
  + â¦aaâ§ is zero: 0â¢ð¥=ð¥â¢0=0
  + Forbidden factors like this are always 0
  + The main diagonal of the table is ð¥Â²
  + Idempotents E(M) are where ð¥Â²=ð¥: everything but â¦aâ§
  + Preview: most of the classification problems are based on E(M)

|  â |  Î» |  a |  b | ab | ba | aa |
|---:|---:|---:|---:|---:|---:|---:|
|  Î» |  Î» |  a |  b | ab | ba | aa |
|  a |  a | aa | ab | aa |  a | aa |
|  b |  b | ba |  b |  b | ba | aa |
| ab | ab |  a | ab | ab |  a | aa |
| ba | ba | aa |  b | aa | ba | aa |
| aa | aa | aa | aa | aa | aa | aa |
