---
author: Sergey P.
title: "Unit Tests and All those DDs"
layout: post
description: "How Unit Tests, TDD and BDD differ from each other and in what cases each techniques can be used."
redirect_from: ["/2016/03/17/unit_tests_tdd.html"]
image: "/img/tdd_comics.png"

---


![](/img/tdd_comics.png)

The definition of Unit Tests is “A unit test is an automated piece of code that invokes a unit of work in the system and then checks a single assumption about the behavior of that unit of work”. Here in Itexus we believe that writing unit test is really necessary in fastly growing and complex projects. In our company we are not adepts of architecture complexity from the project start but rather product evolve. So, iterative code refactoring is the part of the product development. And that is when unit testing comes on the scene. The project good covered with tests is pretty safe to refactoring or to introducing some low level and architecture changes. And for sure unit tests helps to improve product stability.

When Unit Testing concentrates on question “How?” to test the TDD (Test Driven Development) is answer on the question “When?”. Unlike a unit test, a TDD test is used to drive the design of an application. A TDD test is used to express what application code should do before the application code is actually written. BDD (Behavior Driven Development) is the same thing as TDD is but for a broader audience: testers, analysts, project and program managers. And BDD has grown to eliminate issues that TDD might cause.

But again we believe that chose of between Unit Tests, TDD or BDD depends from specific project and project team. Simple project and small team just of programmers? So, go with unit tests or TDD. Need something more verbose? Then choose BDD.

These test practices assume the using of specific technical tools to use and here is example list of tools and frameworks which are used in our company: RSpec, FactoryGirl, Capybara, VCR.