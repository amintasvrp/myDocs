---
title: "Logical Paradigm and Prolog"
date: 2018-08-06
author: "Amintas Victor"
type: "post"
---

Even different paradigms like Functional and Imperative have something in common: both perform mapping, that is, read inputs and generate outputs. However, a program according to the **logical paradigm implements relationships**, which are more general than mappings. In other words, when it comes to logic programming, the level is higher than the imperative or functional programming.

<!--more-->

# Logical Paradigm

We define relations as follows: _Considering two sets S and T, we say that there exists a relation r between S and T if, for each x in S and y in T, the evaluation r(x, y) is true or false_.

Having implemented the relation r, we can make queries like:

  1. Given x and y, determine if r (x, y) is true;
  2. Given x, find all y where r (x, y) is true, and vice versa;
  3. Find all x and y where r (x, y) is true.

Logic programming languages ​​are restricted to **Horn Clauses**, which have the following format: **A0 if A1 and ... and An**, where **Ai** is an assertion of the form **Ri(...)**, with **Ri** being the name of a relationship. If **A1, ..., An** are true, we infer that **A0** is also true. Otherwise, **A0** is false. If the clause sums up to **A0**, this is said to be a **fact**.

Logical Paradigm is part of the "declarative paradigm" subcategory, concerned with facts rather than with procedures, so that knowledge about the problem is described using symbolic logic.

Logical-computational formalism is based on three principles:

1. Use of formal language for knowledge representation;

    >A formal language is precise, as it has sentences with well defined syntax and semantics, although it is less expressive in comparison with natural language.

2. Use of inference rules to manipulate knowledge;

    >An inference rule is a pattern of syntactic manipulation that allows you to create new formulas from existing ones and to simulate valid reasoning forms.
3. Use of a search strategy to control inferences.

    >An agent can have a huge amount of stored knowledge. Usually, it needs to use only part of it to solve a problem. In this sense, the search strategy serves to decide which part of the stored knowledge should be explored in search of the solution.

The programmer should be concerned with describing the problem to be solved (specification), leaving the machine to search for the solution.

# Prolog

Generally associated with the context of AI or linguistics or both, it has its roots in first-order logic.

As an advantage, it allows to represent the knowledge that an agent has about its world in a simple, direct and high level.

## Horn Clause

In prolog, this is the Horn Clauses syntax:

```prolog
    B: - A1, A2, ..., An.
```

## Unification

When responding to a query, the Prolog interpreter may need to assign values ​​to the variables. Unification is the mechanism used to determine if there is a way to instantiate the variables of two predicates in order to make them equal. Two terms can be unified if:

1. Both are constants;
2. One of the terms is a variable;
3. Both are complex terms with the same name and number of arguments

## Lists

Lists consist of a structure representing a sequence of elements of any length. In prolog, the atom **[]** denotes an empty list and the structure **[h|t]** denotes a list whose head is **h** whose tail is **t**, so that the vertical bar notation is provided to separate some elements from the list from the rest of the list .

In this language, the lists are heterogeneous, that is, they can contain values ​​of different types. We can even compare values ​​of different types using the relation "=", but the result will be false.

To see examples of implementations, [click here] (https://github.com/amintasvrp/Dirlididi_PLP/tree/master/questoesProlog). To learn about the _Prolog Story: Colosseum of Champions_ project, which consists of a Marvel characters shuffling battle game, implemented in Prolog, [click here](https://github.com/amintasvrp/A_Prolog_Story_CoC).
