# fp-study-group
Collection of links for studying functional programming.

## Current 2022

- [The Dao of Functional Programming](https://github.com/BartoszMilewski/Publications/blob/master/TheDaoOfFP/DaoFP.pdf) by Bartoz Milewski.

- [Category Theory for Programmers](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/) by Bartoz Milewski. [PDF version](https://github.com/hmemcpy/milewski-ctfp-pdf/releases/download/v1.3.0/category-theory-for-programmers.pdf).

## Category Theory

 
- [Programming with Categories](http://brendanfong.com/programmingcats.html): MIT course by Brendan Fong, Bartosz Milewski, and David Spivak. Summary: In this course we explain how category theory—a branch of mathematics known for its ability to organize the key abstractions that structure much of the mathematical universe—has become useful for writing elegant and maintainable code. In particular, we'll use examples from the Haskell programming language to motivate category-theoretic constructs, and then explain these constructs from a more abstract and inclusive viewpoint.

- [An Invitation to Applied Category Theory](https://arxiv.org/abs/1803.05316) by Brendan Fong, David I Spivak.  The tour takes place over seven sketches, each pairing an evocative application, such as databases, electric circuits, or dynamical systems, with the exploration of a categorical structure, such as adjoint functors, enriched categories, or toposes.
No prior knowledge of category theory is assumed.

- [Category Theory in Context](https://emilyriehl.github.io/files/context.pdf): Emily Riehl's popular book. Not a gentle introduction. Good definitions starting on page 4, Section 1.1.


## Actor Model

- [OTP as the Core of Your Application](https://akoutmos.com/post/actor-model-genserver-app/) by Alex Koutmos. "In this two part series, we’ll be taking a deep dive into what exactly the Actor Model is, how exactly the Actor Model is implemented in Elixir/Erlang and how we can leverage this pattern in a pragmatic way from within our applications.To really understand these concepts, we will be writing a Phoenix application that relies on GenServers as the primary datasource that powers our business logic."


## Haskell

- [Learn You a Haskell](http://learnyouahaskell.com/) by Miran Lipovaca.

## Scala

- [Actors in Scala](https://media.pragprog.com/titles/pb7con/Bonus_Chapter.pdf): bonus chapter
[Seven Concurrency Models in Seven Weeks](https://pragprog.com/titles/pb7con/seven-concurrency-models-in-seven-weeks/)
by Paul Butcher. SCMiSW now uses Elixir.

- [Functional Programming in Scala](https://www.manning.com/books/functional-programming-in-scala) by [Paul Chiusano](https://pchiusano.github.io/) and [Rúnar Bjarnason](https://www.youtube.com/watch?v=ElLxn_l7P2I).

## Julia

- [cormullion’s blog](https://cormullion.github.io/): "This is my blog, containing a few posts exploring the Julia language and my ongoing attempts to learn 2D vector graphics with it. Nearly every graphic you see here uses my simple wrapper for the Cairo graphics library, called [luxor.jl](https://github.com/JuliaGraphics/Luxor.jl):."

## Elixir

- [Actor model overview using Elixir](https://courses.cs.ut.ee/MTAT.08.024/2020_spring/uploads/Main/B96281_5867_1.pdf): Abstract—Distributed systems became an architectural standard for modern computer systems. An actor model
is one of the possible solutions for process management in such an environment.
This project report discusses about actor model in general, Elixir 
implementation in particular with examples of applications and abstractions 
based on the model and interaction in a pseudo-distributed environment. Moreover,
it provides comparison of parallel algorithm implementation using operating systems 
threads with an actorbased solution. The experiment results demonstrates a
performance advantage over the former approach.

- [Elixir in Action](https://github.com/sasa1977/elixir-in-action) by [Saša Jurić](https://www.theerlangelist.com/).


## Distributed data

- [Unison](https://www.unisonweb.org/): functional prgramming language for distributed computation, founded by Paul and Rune. See [Spark-like distributed datasets](https://www.unison-lang.org/articles/distributed-datasets/) for sample of Unison.


## Thinking in type, shape and function signature

- https://hackmd.io/CBQPxR3ySpSc5ALiIkac0w

## Functional programming with vanilla Java

Modern functional programming semantics were added to the Java
language in version 8, around 2014. This is shows the native 
way before Java 8 to the modern way in Java 8 and after.

- https://www.oracle.com/java/technologies/javase-downloads.html

- From https://mkyong.com/java8/java-8-filter-a-map-examples/

```java
TestMapFilter.java
package com.mkyong;

import java.util.HashMap;
import java.util.Map;
import java.util.stream.Collectors;

public class TestMapFilter {

    public static void main(String[] args) {

        Map<Integer, String> HOSTING = new HashMap<>();
        HOSTING.put(1, "linode.com");
        HOSTING.put(2, "heroku.com");
        HOSTING.put(3, "digitalocean.com");
        HOSTING.put(4, "aws.amazon.com");

        // Before Java 8
        String result = "";
        for (Map.Entry<Integer, String> entry : HOSTING.entrySet()) {
            if ("aws.amazon.com".equals(entry.getValue())) {
                result = entry.getValue();
            }
        }
        System.out.println("Before Java 8 : " + result);

        //Map -> Stream -> Filter -> String
        result = HOSTING.entrySet().stream()
                .filter(map -> "aws.amazon.com".equals(map.getValue()))
                .map(map -> map.getValue())
                .collect(Collectors.joining());

        System.out.println("With Java 8 : " + result);

        // filter more values
        result = HOSTING.entrySet().stream()
                .filter(x -> {
                    if (!x.getValue().contains("amazon") && !x.getValue().contains("digital")) {
                        return true;
                    }
                    return false;
                })
                .map(map -> map.getValue())
                .collect(Collectors.joining(","));

        System.out.println("With Java 8 : " + result);

    }
}
```
