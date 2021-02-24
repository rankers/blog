---
title: "Domain Driven Design"
date: 2021-01-19T19:59:36Z
draft: true
---


Capture:

* Emphasis on refactor
* Emphasis on communication
* Moving business rule to domain object, overbooking policy example. Page 19
* Maps are models, models are selectively simplified, consciously structured form of knowledge
* How DD fits with event driven archs 
* https://github.com/heynickc/awesome-ddd
* ooo vs funcyional
* Layers only depend one way. Relatng layers - can you have a evolitionary arch continual test to show depedency directino
* Don't couple framework to domain implementation, need to apply framewokr features judicuoslt: 74
* Struggled with app vs domain. If the app layer can kick off business process and knows which objects to call to make that happen then its part of the domain. When domain objects are too fine grained this happens as there is a certain amount of coordination
* Dan north code that fits in your head
* S-curve - anathema to DDD, as you refactoring to deeper insight you accelerate.


Policy is a strategy - Java does a very good job of following some of these conventions but can be overkill. FizzBuzz enterprise 

# Introduction

There are many things that make software development complex. But the heart of this complexity is the essential intricacy of the problem domain itself.

2 Premises 

Development is iterative
Developers and domain experts have a close realtionship 
# History

Domain Driven Design (DDD) is a phrase bandied about a lot in the world of microservices but I feel decomposing a domain into services and partitioning them along fairly standard planes is only a small part of the process that gets attention. Theres a whole host of behaviours and technical practices that make up DDD that we should focus on. Those that do pay attention stop after decomposing or recomposing their services after the initial pass. To give an example I see a lot of decomposition along obvious lines that maybe fail to get to the breakthrough point of DDD due to lack of time or lack of attention to the things we'll discuss here.

First off read the book! Eric Evans - Domain Driven Design. It can be dense in places especially the first part but get past the set up and get into the application of the new knowledge you've just learned and its amazing.

Eric Evans sees DDD as part of Extreme Programming Paradigm - an approach that emphasizes pairing and human interaction but more on this later.

# Definitions

Ubiquitous Language - this is the shared language we all use to describe every day things and events within yoir domain. See if you notice in conversations with colleagues common words and phrases that descries the domain. Eric Evans believes this ubiquitous language should be continually reflected in code. Any change in language calls for a refactor. 

Why I like this approach as it doesn't focus on developers as lone geeks in basements coding away. It posits development as a social activity of continual discussion and information sharing. 

Meta: 1 slide vs 25 pages of uiqitous language. Really stresses this

# Models:

Astrolabe - mechanical model of the sky
Model to model to model mapping causes issues. Only need a single model for this activity.

Represent using 3 types of object:

## Objects

Entities, Value Objects, Services

### Entities

Does an object represent something with continuity and identity—something that is tracked through different states or even across different implementations? Or is it an attribute that describes the state of something else? This is the basic distinction between an ENTITY and a VALUE OBJECT.

Entity is not just Java language object entity - its areal life thing that has an ongoing identity. Thknk of a customer

### Value Objects 

Value Objects don't have identity VALUE OBJECTS are instantiated to represent elements of the design that we care about only for what they are, not who or which they are. Numbers and strings are value objects. You don't care which 4 you have, you only care if you've got one or now. They are frequently transient. Treat them as immutable

When you care only about the attributes of an element of the model, classify it as a VALUE OBJECT. Make it express the meaning of the attributes it conveys and give it related functionality. Treat the VALUE OBJECT as immutable (In special case if it is mutable can share it). Don’t give it any identity and avoid the design complexities necessary to maintain ENTITIES.

Don't care about instance, therefore can make decisions around copying sharding and immutability. When you care about access speed can copying this info, think about denirmalized db. Same as when you have distributed services

Evans, Eric. Domain-Driven Design (p. 99). Pearson Education. Kindle Edition. 
Evans, Eric. Domain-Driven Design (p. 97). Pearson Education. Kindle Edition. 

### Services

Sometimes it just isn't a 'thing'.

We don't want to force operations on an object that soesn't conform to the model. Can end up with a lot of obecjt called 'Manager' that end up doing a load of operarions and doens't contian  state.

Named as verb rathe rthan noun. Operations should come from the ubiqutous language

A good SERVICE has three characteristics. 

1. The operation relates to a domain concept that is not a natural part of an ENTITY or VALUE OBJECT.
2. The interface is defined in terms of other elements of the domain model.The operation is stateless.

Not to be confused with services in the infra layer, e.g. generic email service

Evans, Eric. Domain-Driven Design (p. 105). Pearson Education. Kindle Edition.

# Modules

Primary reason is to manage cognitive load. Cognitvie load is term we'll come back to at the end of this talk.

Every one uses them but few use them as modules in domain layer in true sene as that of a first class apart of a domain model. Should emerge as a meaningful part of the model.

We have same objective at object level at this higher level. High cohesion and low coupling. 

Moduels + their classes should co-evelve but classically we leave modules intact without refacotring as its harder to refactor these coarser grain items. As eveything in model driven development a modules bounds and classes are telling you somethign.

Inevitable early mistakes in MODULE choices lead to high coupling, which makes it hard to refactor. The lack of refactoring just keeps increasing the inertia.

Evans, Eric. Domain-Driven Design (p. 111). Pearson Education. Kindle Edition. 

Looking at conceptual relationships is not an alternative to technical measures. They are different levels of the same issue, and both have to be accomplished. But model-focused thinking produces a deeper solution, rather than an incidental one.

Evans, Eric. Domain-Driven Design (p. 111). Pearson Education. Kindle Edition. 

### Distinction of application vs domain layer by example

Many domain or application SERVICES are built on top of the populations of ENTITIES and VALUES, behaving like scripts that organize the potential of the domain to actually get something done. ENTITIES and VALUE OBJECTS are often too fine-grained to provide a convenient access to the capabilities of the domain layer. Here we encounter a very fine line between the domain layer and the application layer. For example, if the banking application can convert and export our transactions into a spreadsheet file for us to analyze, that export is an application SERVICE. There is no meaning of “file formats” in the domain of banking,

Evans, Eric. Domain-Driven Design (pp. 106-107). Pearson Education. Kindle Edition. 

## Associations

For every traversable association in the model, there is a mechanism in the software with the same properties.

In the mdoel  just shows relationship etween two things ut in code can be a collection of onjects, could be a db lookup

Real life lots of many to many and bidirectional associations - these are hard to model. 3 ways to make associations more tractable:

1. Imposing a traversal direction 
2. Adding a qualifier, effectively reducing multiplicity
3. Eliminating nonessential associations

THink about countries and presidents, you don't need to dirty the implementaiton fo person with the concept of president, can make it unidirectional, countrues have presidents. one directional ut 1 to many, can contrain futehr and say for a particualr period the country only hsa 1 president. SO now we have unidirectional and 1 to 1.

Evans, Eric. Domain-Driven Design (p. 83). Pearson Education. Kindle Edition. 

Evans, Eric. Domain-Driven Design (pp. 82-83). Pearson Education. Kindle Edition. 
# A note on mixed implementation paradigms


I've talked a lot about DDD on OOO contexr. We'll continue here for now however you can mix paradigms, rule engine or workflow engines etc. however its hard to mix and you have to maintain the linkage between your model and the implementation. 

You don't have to use OOO you can use anything that can express the model constructs. Be it objects, rules or workflows.

# Ligecylce of domain objects

Aggregates, factories and repositories. Ignore factories and repos for now. Well understood

## Aggregates

How do you manage lifecycle fo an object that references a stack fo other objects. When you delete a person, what do you delete alongside that person.

An Aggregate is a group of associated objects, that we treat as a unit for data change. Each Aggregate has a root and boundary.

The root ios the only member of the aggregate that objects out side of the aggregate are allowed to hold references to

Agg. exmaple: being Purchase orders, line item and parts

# Extedned Example of Domian Modelling.

TBC - part 7

# Refactoring towards deeper insight

## Breakthorugh 
Breakthroguh - refactoring can jsut tinker away with the design nut it can lead to a breakthrough. 

Read refactoring by Martin Fowler
Now we have applied DDD, actual difficulty is finding a good model

Classically we focus on easier to read, easier to maintain code through DRY or classic micro refactoring - good book is martin fowler refactoring . Or we refactor to a pattern, Big 4 design patterns - microservices worked this could be Saga pattern choreography, orchestration or CQRS
These are technical pattern. Don't focus on the model

We care about those motivated by new insights into the domain or those that clarify the model’s expression through the code.

A deep model provides a lucid expression of the primary concerns of the domain experts and their most relevant knowledge while it sloughs off the superficial aspects of the domain.

Example in this chapter is a candidate for presentation

Evans, Eric. Domain-Driven Design (p. 190). Pearson Education. Kindle Edition. 
Evans, Eric. Domain-Driven Design (p. 189). Pearson Education. Kindle Edition. 

## Make implicit explict

Python easter egg

Snuffling for truffles. Developers have to sensitize themselves to the hints of lurking concepts 

Listen to the language of domain experts. They 

2 examples: 

1. Cargo -> creating the itinerary
2. Financial Services firm -> creating the accrual

Read the book -> go and read about finance

Some people say software development is just the process of developers learning a domain

### Explicit Constraints

Emerge implicitly but the desing benefits from making them explicit.

Bucket has a volume, this must not be exceeded. This is a constraint within this domian.

Contents must be less than or equal to capacity, factor out the constraint. Use an intention revealing method name

Sometimes a constraint needs to live outside an object. Smells
1. Evaluating a constraint requires data that does not otherwise fit the object’s definition
2. Related rules appear in multiple objects, forcing duplication or inheritance between objects that are not otherwise a family.
3. A lot of design and requirements conversation revolves around the constraints, but in the implementation, they are hidden away in procedural code.

Evans, Eric. Domain-Driven Design (p. 221). Pearson Education. Kindle Edition. 


### Specifications

A lot of time the domain has a shed load of business rules, lots of little predicates. We want to evaluate these to see if our objects satisfy the rule. Some can be simple. isOverude() - just check a date vs now. Others more complex. An invoice could have isDelinquent on it. THis has a load of rules and context needed. Can spearate from invoce object and put in a value object called Invoice Delinquency. Then run test on the object. Can even then combine specifications to do more complex predicate logic

Specifications can be used for not just validation but query and also building to order
## Supple Design

Code will be read more than it will be written so make it nice to read. When software lacks good design its a bit of a vicious cycle. You know that bot of code is crap so maybe you end up duplicating it or working around it. This then compounds the mess

We talk about s-curves on projects somtimes. THis has got to be setting off alarm bells in your head. Why should I be getting slower as the project proceeds, with a supple design which is easy to change I should be accelrating

Need to serve a number of users, the end user the cusotmer
The client developer consuming the output of the desing 
THe domain developer themselves - may be the same person above but they're playing two distinct roles

To be open to change it must be easy to unudertnad, the effects of the code must be transparent

If a developer must consider the implementation of a component in order to use it, the value of encapsulation is lost.

#### Intention Revealing Interfaces:

Name classes and operations to describe their effect and purpose, without reference to the means by which they do what they promise. This relieves the client developer of the need to understand the internals. These names should conform to the UBIQUITOUS LANGUAGE so that team members can quickly infer their meaning. Write a test for a behavior before creating it, to force your thinking into client developer mode.

Evans, Eric. Domain-Driven Design (p. 247). Pearson Education. Kindle Edition. 
Evans, Eric. Domain-Driven Design (p. 246). Pearson Education. Kindle Edition. 

#### Example

ROGER And brian eno - mixing colours

Paint! How to model paint! We couldn't get anymore boring if we tried but stick with me. The example of modelling paint shows how the domain context affects the design of the code.

1. Side effect free functions - side effect changes state of a system - nested operations make it hard to see affect of your change
 
Place as much of the logic of the program as possible into functions, operations that return results with no observable side effects. Strictly segregate commands (methods that result in modifications to observable state) into very simple operations that do not return domain information. Further control side effects by moving complex logic into VALUE OBJECTS when a concept fitting the responsibility presents itself.

Evans, Eric. Domain-Driven Design (p. 251). Pearson Education. Kindle Edition. 

2. Assertions
State post-conditions of operations and invariants of classes and AGGREGATES. If ASSERTIONS cannot be coded directly in your programming language, write automated unit tests for them. Write them into documentation or diagrams where it fits the style of the project’s development process. Seek models with coherent sets of concepts, which lead a developer to infer the intended ASSERTIONS, accelerating the learning curve and reducing the risk of contradictory code.

Evans, Eric. Domain-Driven Design (p. 256). Pearson Education. Kindle Edition. 

3. Conceptual contours -> fracture planes in Team Topology

Heuristic: When you refactor, if you;re able to make localized successive localized change that s a sign of a good conceptual contour. Encounter a new requirement that forces a breakdown of objects and methods that is a sig the model needs refinement.

4. Closure of operations

Where it fits, define an operation whose return type is the same as the type of its argument(s). If the implementer has state that is used in the computation, then the implementer is effectively an argument of the operation, so the argument(s) and return value should be of the same type as the implementer. Such an operation is closed under the set of instances of that type. A closed operation provides a high-level interface without introducing any dependency on other concepts.

Evans, Eric. Domain-Driven Design (pp. 268-269). Pearson Education. Kindle Edition. 

5. Specification

Skipped

## Design Patterns and the Domain

Point of view affects one’s interpretation of what is and isn’t a pattern. One person’s pattern can be another person’s primitive building block. For this book we have concentrated on patterns at a certain level of abstraction. Design patterns are not about designs such as linked lists and hash tables that can be encoded in classes and reused as is. Nor are they complex, domain-specific designs for an entire application or subsystem. The design patterns in this book are descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context. [Gamma et al. 1995, p. 3]

Strategy(policy), Composite,
Evans, Eric. Domain-Driven Design (p. 309). Pearson Education. Kindle Edition. 

## 13 Refacotirng towards deeper insigt 

There are three things you have to focus on. 1. Live in the domain. 2. Keep looking at things a different way. 3. Maintain an unbroken dialog with domain experts.
### Digging for concepts

Love this phrase, it evokes the attritional affair that finding the right fit is. It also means good design isn't hit upon first time. You have to learn the domain

INitiate: Spend time in the code -developers cna spot this 
Explore: Work with team mates to understandn and creatre possible solitions
Prior knowleedge: epxlore books and experience of others in the domain
Design for developers 
Timing: IIf you wait until you can make a complete justification for a change, you’ve waited too long.
Continuous refactoring has come to be considered a “best practice,” but most project teams are still too cautious about it. They see the risk of changing code and the cost of developer time to make a change; but what’s harder to see is the risk of keeping an awkward design and the cost of working around that design.

Evans, Eric. Domain-Driven Design (pp. 324-325). Pearson Education. Kindle Edition. 
Crisis as opprotunity 

“punctuated equilibrium” model. In this expanded view of evolution, long periods of gradual change or stability are interrupted by relatively short bursts of rapid change. Then things settle down into a new equilibrium.

Evans, Eric. Domain-Driven Design (p. 325). Pearson Education. Kindle Edition. 

Evans, Eric. Domain-Driven Design (p. 321). Pearson Education. Kindle Edition. 

# Strategiuc Desing

Context, Distillation, Large Scale Structure

## Context or rather bounded context

Models want to be logically consistent throughout, without contradictory or overlapping definitions.

Although we seldom think about it explicitly, the most fundamental requirement of a model is that it be internally consistent; Is my version of a domain object the same as anothers.

When a model is internally consistent it is called unification

Ideal world an entire company has a single unififed model but this is never the case - overhead of unifying it is too great. 


Have to allow multiple models to evolve separately to achieve the agility
Models apply on in contexts, create bounded contexts to partition your domain

Cell pic. Like cell walls context keep whats inside inside, whats outside  and what information can pass in and out.

Pru we had something called the CIM. This was managed centrally. Nightmare. Splunk seems to have one

By defining a boudded context you bound the software and the coombuciation between the teams. This gives clairty. Should I coordicate with that perosn over there about a model change i'm making. Nice to have freedom to do what you want.
Evans, Eric. Domain-Driven Design (p. 328). Pearson Education. Kindle Edition. 

### Recognizing Splinters Within a BOUNDED CONTEXT

1. duplicate concepts - 2 impementations of the same concept, everytime this info is updated have to update in two places. expect this never happens so one falls behind and becomes
2. false cognates. This is the case when two people who are using the same term (or implemented object) think they are talking about the same thing, but really are not.

How to prevent model break down in a context:

CI: Integraiton of code and integration of concepts. First one is well understood, we merge code daily to trunk, we execute tests we get feeedback and if the trunk is broken we fix it fairly fast. (Side note - don't think we do this as well as we can)

Seocnd integraiton of concepts by constant discussion of the UBIQUTOUS LANGUAGE 


A CONTEXT MAP is in the overlap between project management and software design. The natural course of events is for the boundaries to follow the contours of team organization. People who work closely will naturally share a model context. People on different teams, or those that don’t talk, even if they are on the same team, will split off into different contexts. Physical office space can have an impact too, as team members on opposite ends of a building—not to mention different cities—will probably diverge without extra integration effort. Most project managers intuitively recognize these factors and broadly organize

Evans, Eric. Domain-Driven Design (p. 344). Pearson Education. Kindle Edition. 

Evans, Eric. Domain-Driven Design (p. 339). Pearson Education. Kindle Edition. 

### Relationships between bounded domains 

Shared Kernel - not sure this is a practice thats done nowadays
Customer /Suplier  - Team Topologies calls this platform teams
Contract Testiung

###  Transforming Boundaries

Favoring Larger BOUNDED CONTEXTS • Flow between user tasks is smoother when more is handled with a unified model. • It is easier to understand one coherent model than two distinct ones plus mappings. • Translation between two models can be difficult (sometimes impossible). • Shared language fosters clear team communication. Favoring Smaller BOUNDED CONTEXTS • Communication overhead between developers is reduced. • CONTINUOUS INTEGRATION is easier with smaller teams and code bases.Larger contexts may call for more versatile abstract models, requiring skills that are in short supply. • Different models can cater to special needs or encompass the jargon of specialized groups of users, along with specialized dialects of the UBIQUITOUS LANGUAGE.

Evans, Eric. Domain-Driven Design (p. 383). Pearson Education. Kindle Edition. 

Evans, Eric. Domain-Driven Design (p. 383). Pearson Education. Kindle Edition. 

## Disitilling

Identify you core domain and best devs on long lived team
Have a domain vision statement to direct whats in and whats out if the core domain
Try and carve off generic subdomins these can be fulfilled through 
1. COTS product, think Accounting, CRM, etc.
2. Ue a publsihed domain model 
3. Outsource
4. In  house ut make it simple

Coheive mechanism - speacialized susystem

Segregated Core - monotlith to microservice

software. A good project has lots of people sticking their nose in other people’s business. Developers play with frameworks. Architects write application code. Everyone talks to everyone. It is efficiently chaotic. Make the objects into specialists; let the developers be generalists.

Creating a supple design based on a deep model is an advanced design activity, but the details are so important that it has to be done by someone working with the code. Strategic design emerges out of application design, yet it requires a big-picture view of activity, possibly spanning multiple teams.

Evans, Eric. Domain-Driven Design (p. 495). Pearson Education. Kindle Edition. 
# Techniques

Event storming

# Conway's Law

Team design is Software design

# Team Topologies

What squares the circle 
Doesn't mater if you manage a team or you're in a team. This Impacts you


# Key Takeways

Learn your domain - read a book / ask domain expert
Take time to think and reflect on your design!
Team desing and software desing is the same thing
Software is fractal in nature, fracture planes exist at class, at module and at enterprise level
