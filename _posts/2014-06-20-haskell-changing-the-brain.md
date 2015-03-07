---
title: Haskell/Scala changing the brain
date: 2014-06-20
layout: post
categories: tech talk
---

## Haskell Resources

* Philip Wadler course in University of Edinburgh
    - https://www.youtube.com/playlist?list=PLtRG9GLtNcHBv4cuh2w1cz5VsgY6adoc3

## Original Talk
* <http://vimeo.com/96639840>

* To Understand deeply

## Types are Cool

#### Scala
Int
String
Option[Boolean]
List[Double]

#### Haskell
Int
String
Maybe Bool
[Double]

## Types represent a set of values

#### Scala

A Boolean can represent 2 values
A Option represents presence or absence.

Together, we can represent 3 values.

val mby: Option[Boolean] = Some(true)
val mby: Option[Boolean] = Some(false)
val mby: Option[Boolean] = None

#### Haskell

mby:: Maybe Bool (syntax varibale :: Type)
mby = Just True
mby = Just False
mby = Nothing

## Large sets of values

A type can also represent infinite values.

#### Scala
val bools: List[Boolean] = List(true, false, false)
val bools: List[Boolean] = List(false, false)

#### Haskell
bools :: [Bool]
bools = [True, False]
bools = [False, ...]

## Type Equivalence

* Yoneda lemma (what is it?)
* Two types are equivalent when their underlying sets of values are equivalent
* Two equivalent types represent the same information, even though they may look drastically different
* Two types X and Y are equivalent when can morph from values
of X to values of Y and back without losing any information(and vice versa)

* Functions change value of one type to value of another type !!
    * The new type encodes the ‘function output’

## No Equivalence

#### Scala
def toList(opt: Option[Boolean]) = opt match {
    case None => List.empty[Boolean]
    case Some(b) => List(b)
}

def toOpt(bools: List[Boolean]): Option[Boolean] = bools.headOption

* toOpt loses information

#### Haskell

toList :: Maybe Bool -> [Bool]
toList Nothing = []
toList Just b = [b]

toMby :: [Bool] => Maybe Bool
toMby [] = Nothing
toMby(a:_) = Just a

## Types That are Equivalent

#### Scala

def g1: Option[Boolean]

def g2[B](f: Boolean => B): Option[B]

#### Haskell

g1 :: Maybe Bool

g2 :: forall b. (Bool -> b) -> Maybe b

Yoneda claims g1 and g2 are isomorphic

## Values are Implementations

#### Scala
def g2[B](f: Boolean => B): Option[B]

def g2[B]: (Boolean => B) => Option[B]

#### Haskell

g2 :: forall b. (Bool -> b) -> Maybe b

## Implementing g2 (Only 3 impls are possible !)

#### Scala
def g2[B](f: Boolean => B): Option[B] = None
def g2[B](f: Boolean => B): Option[B] = Some(f(true))
def g2[B](f: Boolean => B): Option[B] = Some(f(false))

#### Haskell
g2 ::forall b. (Bool -> b) -> Maybe b
g2 _ = Nothing
g2 f = Just $ f True
g2 f = Just $ f False

## What are we claiming ?

#### Scala
type X[B] = (Boolean => B) => Option[B]

//Option[Boolean] is **equivalent** to X
#### Haskell

type X = forall b. (Bool -> b) -> Maybe b

-- Maybe Bool is **equivalent** X

## Intutions for the isomorphism

#### Scala
#### Haskell

type X = forall b. (Bool -> b) -> Maybe b

g1 :: Maybe Bool

g1 = Nothing
g2 = Just True
g3 = Just False

g2 :: forall b. (Bool -> b) -> Maybe b

g2 _ = Nothing
g2 f = Just $ f True
g2 f = Just $ f False


If we take f to be an identity function then,

g2 is same as g1 !!!


What is the isomorphism ?

#### Scala
#### Haskell

type X = forall b. (Bool -> b) -> Maybe b

inv1 :: Maybe Bool -> X
inv1 mby = \f -> fmap f mby
inv1 = flip fmap


inv2 :: X -> Maybe Bool
inv2 f = f id

Following the types:

-- inv2 (inv1 p) == p
-- inv1 (inv2 q) == q


## What I’ve Observed
* Haskell forces you to stop and reason about your code
* You cannot just ‘mess with it’ until it compiles
* read haskell code.. can read other languates

* <http://github.com/NICTA/course>
* <http://eed3si9n.com/learning-scalaz/day0.html>
