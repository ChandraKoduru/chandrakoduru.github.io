---
title: The Power of Abstraction - my take
date: 2014-06-12
layout: post
categories: tech talks
---

## Main Talk
* Barbara Likov @ http://www.infoq.com/presentations/programming-abstraction-liskov
* March - 2013, MIT


## Software is Complex

* Systems are big
* Distributed systems

## Addressing Complexity

* Algorithms


* Programming Methodology
    - Programming structure

* Programming Languages
    - Some programming methodologies have become programming languages

## Programming Methodology

* how should programs be designed - process
* how should programs be structured - underlying the design process

## Go To statment considered harmful - E.W. Dijkstra

* no proper control structures
* software programs are hard to reason

* program code is static 
* program execution is dynamic.

* reasoning about static is different from reasoning when in execution.
* when static and dynamic paths are similar it is to trasfer static reasoning to dynamic behaviour
* the goto statement kind of spoils relationship

## Program Development by stepwise refinement - N. Wirth

* top down design
* problem spec ..to line by line statements

## Modularity 

* A program is collection of modules
* each has an interface, described by specification
* a using module depends only on the interface
* benefits
    - local reasoning
    - independent development

## The situation
* procedures were only type of module
* not enough - e.g. file system

## Partitions
* no globals
* hid state and access only by functions

## Idea

* Connect partitions to data types


## Programming Languages supporting Abstract Data Types

* Syntactic - extension - terrible idea (factorial ! symbol)
* Difference between abstraction and encapsulation(java)
    * Abstraction is implemented using interface and abstract class while Encapsulation is implemented using private and protected access modifier.

## Protection in Programming Languages - J.H. Morris

## Programming with Abstract Data Types - B. Liskov
* Abstract data types
    - a set of opertions
    - a set of objects
    - operations provide the ONLY way to use the objects

## Why a programming language

* Communicating to programmers - providing language constructs
* getting a precise definition

## Facts about CLU

* static type 
* heap based
* separate compilation units - object files
* no concurrancy, no gotos, no inheritance

## CLU Mechanism

* new data types -> Cluster -> class in java
* polymorphism

## Clusters
* operations belong to type (instead of object)
* pick the operation of type and invoke it on an instance of that type

## Polymorphism (generics)

* Set<T>

## Iterators

* For all x in C do S
    - Destroy the collection
    - Complicate the abstraction

## Alphard

* Generators - Iterators(java)
* Iterators - Yield - (c#)
* d

## Exception Handling

* first class procedures and iterators 

## Type Hierarcy

## CLU to Object Oriented Programming

* small talk provided the inheritance

## Inheritance was used for
* Implementation - technique
* Type hierarchy

## Liskov Substitution Principle

## Programming Languages Today

* Java, C#
* introductory - python
