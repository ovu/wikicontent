Lazy evaluation
================

Fibonacci
=========

Idea: two lists, one shifted in one element

let fibs'' = (0 :: Integer) : 1 : zipWith (+) (tail fibs'') fibs''


Peano Natural numbers
=====================

data N = Z | S N deriving Show

plus :: N -> N -> N
plus Z a = a
plus ( S a ) b = S $ plus a b

-- Per Induktion: plus a Z == a
--   + IA a=0: plus Z Z == Z
--   + IS n->n+1: plus (Suc c) Z = Suc (plus c Z) = Suc c
-- plus (plus a b) c == plus a (plus b c)
-- plus a b == plus b a
