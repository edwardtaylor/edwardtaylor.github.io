---
layout: post
title: "Embracing BDD"
date: 2013-08-05 23:30
comments: true
categories: [BDD, TDD, DDD]
---

###Wikipedia Definition

> Behavior-driven development combines the general techniques and principles of [test-driven-development](http://en.wikipedia.org/wiki/Test-driven_development) with ideas from [domain-driven design](http://en.wikipedia.org/wiki/Domain-driven_design) and [object-oriented analysis and design](http://en.wikipedia.org/wiki/Object-oriented_analysis_and_design) to provide software developers and business analysts with shared tools and a shared process to collaborate on software development, with the aim of delivering software that matters (as opposed to software that doesn't matter).

###Not about the tests
Most people's first reaction when being introduced to TDD and BDD is thinking these methodologies are all about writing tests. The value realized by writing tests lies not with the instant gratification of seeing a green check after writing code, but the thought process and team collaboration that occurs prior to coding. The principles of BDD bring the team together to share a common understanding of the functionality a feature will provide after its implementation. As an added bonus, automated testing builds the support system required to allow the team to refactor and embrace change within the application. 

Veterans of TDD understand and appreciate the work-flow TDD provides to add structure to development process. TDD breaks down the implementation process into small incremental pieces and creates of work-flow where the developer is constantly asserting the expected behavior of the code written. BDD strives to bring these same benefits to the entire team and external customers by providing a framework which focuses on functionality delivered and not the implementation details.

###Ubiquitous Language
BDD complements the practice of Domain-Driven-Design and shares the concept of a [ubiquitous language](http://martinfowler.com/bliki/UbiquitousLanguage.html). While also being a $5 dollar term, the ubiquitous language is defined by Eric Evans in his book, [Domain Driven Design](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) (the blue book), as a "language structured around the domain model and used by all team members to connect all the activities of the team with the software."

This common language is used by the Customer, Product Owner, Developer, QA, and all members of the team. Instead of communicating in technical terms, everyone on the team communicates using the evolving language. This domain vernacular stretches deep into the implementation details as the code itself represents the shared model the team uses to communicate. Developers will frequently rename methods or classes in response to changes in terminology used by the Customer and Product Owner. Approaching software development practicing DDD allows us to remove unnecessary translation from the non-technical to the technical persons as both parties speak in the same terms. Due note that not all code found within an application will match the domain's language, but we want to strive to have our business model map directly to the mental model shared by the team.

###Specifications
In the realm of BDD, specifications are written using the ubiquitous language and are the medium used to communicate functionality to all team members. By embracing and defining the domain language, we enable everyone the ability to design, write, and review the constraints and expectations of a feature. What exactly makes up a specification?

Specifications consist of the following:

* Title - One line description
* Narrative - Explains the business value of the feature
* Acceptance Criteria - Describes the features functionality by asserting expectations

Example:

	Title:  Add product to cart

	Narrative:  As a customer
	            I want to add products to a cart
	            So that I can view my current total

	Acceptance Criteria:

	  Scenario 1: Add Product to Cart
	              Given a user viewing the product catalog
	              When the user adds a product to the cart
	              Then the product is listed in the Cart 
	                And the cart total is increased

###Acceptance Criteria
We continue to define Acceptance Criteria until there is no more ambiguity surrounding the user story. Once we've exhausted all the acceptance criteria, the team can properly size and estimate the amount of effort required to complete the feature. This implies all acceptance tests need to be written prior to beginning a sprint or as part of the planning session. Ideally defining the acceptance criteria will take place as part of regular scheduled grooming meetings where the Product Owner can address the entire team about an upcoming features and priority.

What makes an acceptance test?

* Owned by the customer or Product Owner
* Written by the team (Product Owner, Developer, QA)
* Focuses on *what* not *how*
* Expressed using the ubiquitous language
* Concise, Precise, and unambiguous

###Remove ambiguity
Much like a plumber passes water through a pipe to check the handy work of a patch job, passing data through our tests allows us to see scenarios we missed and removes ambiguity. How are we handling rounding? Are we using Banker's rounding? How do I distribute $1.00 across 12 months? Data helps tell the story and provides concrete examples of the expectations of the feature from all the stakeholders. Part of wrestling complexity in software is removing ambiguity. Following the principles of *specifications by example*, we learn more about a feature by analyzing the desired outcomes.

###Knowing the answer
The greatest impact I've experienced by practicing BDD & TDD comes not from executing the test cases but the process involved in authoring the tests. By thinking about each scenario and the acceptance criteria, I have a more thorough understanding of what I need to accomplish before writing a single line of code. It's truly remarkable how easily the implementation details can be discovered when you know the end result. Have you ever been required to show your work for a calculus problem? How much easier was the problem to solve by knowing the question and the answer. In the event you miscalculated, you quickly notice the error (most of the time prior to completion), and can backtrack to the point your solution deviated. This type of immediate feedback is at the core of driving our implementation details by external specifications.


###Development cycle
I'll wrap up this post by showcasing this snazzy [workflow](http://www.planetgeek.ch/2013/06/05/clean-code-cheat-sheet) that describes how acceptance tests integrate with my current development cycle. Take note of where the process starts and where the first line of code is actually written.

[![ATDD TDD Workflow](/images/atdd_tdd_lifecycle.png)](/images/atdd_tdd_lifecycle.png)

### Additional Reading

* [ATDD by Example: A Practical Guide to Acceptance Test-Driven Development](http://www.amazon.com/ATDD-Example-Test-Driven-Development-Addison-Wesley/dp/0321784154) Markus Gärtner 
* [Test Driven: TDD and Acceptance TDD for Java Developers](http://www.amazon.com/Test-Driven-Acceptance-Java-Developers/dp/1932394850) Lasse Koskela 
* [The RSpec Book: Behaviour Driven Development with Rspec, Cucumber, and Friends](http://www.amazon.com/RSpec-Book-Behaviour-Development-Cucumber/dp/1934356379/) David Chelimsky, Dave Astels, Bryan Helmkamp, Dan North, Zach Dennis, Aslak Hellesoy