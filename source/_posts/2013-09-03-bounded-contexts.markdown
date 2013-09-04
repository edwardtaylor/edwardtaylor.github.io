---
layout: post
title: "Bounded Contexts"
date: 2013-09-03 20:04
comments: true
categories: [DDD, CQRS]
---

###Bounded Contexts

*Define: Bounded Context is a principle of strategical mapping out our domain models and setting consistency boundaries. A model (entity) is guaranteed to be consistent inside of its BC.*

Let's break it down. Ever heard the phrase, "Jack of all trades, master of none." Too many times we have seen systems that try to be everything to everybody and end up with a mediocre system with half-baked functionality. These systems tend to suffer from tight coupling and cannot be extended or changed easily without substantial risk. The problem lies with sharing the same model throughout your entire application. Different domains require different sets of information, workflows, views, and validation.

By defining our bounded contexts, we explicitly state the responsibilities and expectations for each model. A "recurring gift" means entirely different things to a fundraiser, an accountant, and a payment processor. Instead of getting the three personas in a room and having a fight to the finish of what the "real" definition of "recurring gift" means, let them each work inside their domain.

> "Any intelligent fool can make things bigger, more complex, and more violent. It takes a touch of genius -- and a lot of courage -- to move in the opposite direction." - Albert Einstein

Complexity is the true archnemesis of software development and Bounded Contexts are another weapon we can use to keep our applications simple and maintainable. Drawing these clear boundaries allows us to deploy/scale to the specific needs of each domain. Each Bounded Context can pick the technologies and architecture best suited for their domain. There are several BCs where a simple CRUD application will suffice while others may require different approaches. In the end, the constaints imposed by Bounded Context add incrediable amounts of flexability and freedom to choose the best solution for a given domain.

Resources:

* [Domain-Driven Design: Tackling Complexity in the Heart of Software](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) Eric Evans

* [Strategic Domain Driven Design with Context Mapping](http://www.infoq.com/articles/ddd-contextmapping)

* [Bounded Context - Definition](http://dddcommunity.org/uncategorized/bounded-context)