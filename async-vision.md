# Lang Team: Async Vision document

Owner: nikomatsakis

Please be aware: this document is widely shared and very much a work-in-progress. 

## What is this

The goal of this document is to lay out a general vision and set of goals for Async I/O in Rust. This document is being written in January of 2021. The core pieces of async-await are stable, but there remains a lot of work for it to feel like a "first class" feature of Rust. The goal of this document is to describe three things:

* The design tenets, or principles, that we are using to drive our work on Async I/O in Rust.
* Descriptions of how it feels to write Async I/O code in Rust today.
* Descriptions of how we think it *should* feel to write Async I/O in Rust in the "fullness of time".

The descriptions of how things should work are intentionally thinking long term. It's more than we can get done in a year. There's also intentionally *maximalist and ambitious*. They stake out an opinionated position on how the ergonomics of Async I/O should feel. This position may not, in truth, be attainable, and for sure there will be changes along the way. Sometimes the realities of how computers actually work may prevent us from doing all that we'd like to. That's ok. This is a dream and a goal.

## Using this document to drive work

Part of my plan is that we can use this document to drive and organize the work to achieve the design described within. The idea is that we can map out parts of the vision that we want to achieve -- or at least move closer -- over 2021, and assign owners to drive those parts. That hasn't happened yet.

## This is a group effort

I (nikomatsakis) am coordinating this document, but I'm looking for help both in informing the vision but also in drafting its contents. You'll find that there are "incomplete" user stories below. If you're interested in helping to draft part of them, please let me know.

## Design tenets

Ordering is meaningful. Earlier has precedence.

1. **Minimal overhead.** Rust Async I/O performance should compare favourably with any other language. In the extreme case, it should be possible to use async/await without any required allocation, although this is unlikely to be a common case in production systems.
2. **Async is like sync, but with blocking points clearly identified.** At the highest level, writing a simple program using asynchronous I/O in Rust should be analogous to writing one that uses synchronous I/O, except that one adds `async` in front of function declarations and adds `.await` after each call. We should aim for analogous design between synchronous and asynchronous equivalents. Similarly, streams should be like asynchronous iterators. One should be able to use the same sort of combinators with streams and to iterate over them in analogous ways.
3. **Easy to get started, but able to  do anything you want.** We should make it simple to write Async I/O code and get things that work reasonably well, but it should be possible for people to obtain fine-grained control as needed.
4. **No one true runtime.** Specialized systems need specialized allocators. We need to be able to hook into existing runtimes in different environments, from embedded environments to runtimes like node.js.
5. **Library ecosystem is key.** We want to have a strong ecosystem of async crates, utilities, and frameworks. This will require mechanisms to write libraries/utilities/frameworks that are generic and interoperable across runtimes.

## Use cases to ensure we support

To elaborate on the "minimal overhead" and "easy to get started, but able to do anything you want" tenet, here are a set of use cases:

* **Single-threaded executors:** Some systems tie each task to a single thread; such tasks should be able to access data that is not `Send` or `Sync`, and the exexcutor for those tasks should be able to be fully optimized to avoid atomic accesses, etc.
* **Multi-threaded executors:** Many systems migrate tasks between threads transparently, and that should be supported as well, though tasks will be required to be `Send`.
* **"Bring your own runtime"**: The Rust language itself should not require that you start threads, use epoll, or do any other particular thing.
* **Zero allocation, single task**: Embedded systems might want to be able to have a single task that is polled to completion and which does no allocation whatsoever.
* **Multiple 

Things to consider:

* Integration with foreign runtimes, poll loops -- 
    * Async function in Rust being driven by executor in other language (most commonly C++, but nodejs and browser event loop are other likely candidates, webassembly in the browser)

## User stories

*This section describes the end-user experience that we are shooting for. It is not expected that we will realize all the details of this experience in 2021, but we should always be advancing toward it.*

### Status quo as of Feb 2021

#### Getting started


#### Bob tries AWS

#### Bob tries Azure


### Status quo

#### Getting started

Bob would like to learn how Async I/O in Rust 

* Bob would like to learn how Async I/O in Rust works.
* The topic is not covered in the Rust books. (is this true?)
* Bob finds the [async book](https://rust-lang.github.io/async-book/index.html), which has a quick introduction to `async fn`, and which directs him to an [async ecosystem](https://rust-lang.github.io/async-book/08_ecosystem/00_chapter.html) section with a list of runtimes to try.
* Bob has to choose which runtime to use and it is stressful.
    * What libraries might Bob want to use? Are they compatible?
    * What about other layers on the stack, such as web framework?

#### Parallelizing a big loop, blocking the main thread

* Sally tries to process a bunch of data

#### Interop with C++, JS, browser

* 

#### Exposing a library that supports sync, async

* Sally

#### Writing and working with streams

* Pin breaks Bob's mind

#### Writing and working with async read, async write

* Pin breaks Bob's mind
* If type is Unpin, you can do it, but have to learn how to do all this work
    * Context
    * Poll
    * 

#### Debugging and developing the service

#### Deploying a production service

### The world we want


* Sally has been working in Rust for a while, and has written various programs using Synchronous I/O, but she's never used asynchronous programming.
* She goes to learn async programming
* She goes to the async book and works through a simple example
    * `async fn main() { }`, etc
* Extend to something that includes streams
* Use of 3rd party libraries, nifty web framework
    * Use of async fn in traits to build abstractions

#### new Rust programmer new to async programming

#### a Java programmer learning Rust

### Implementing libraries, middleware, and adapters

### Optimizing and customizing your setup

* Switching to a different runtime for custom environment, better performance, etc

### Putting services into production

* Using tooling to inspect service problems



## Concerns to resolve

* "zero-cost abstractions, one allocation per task"
    * I think one allocation per task was our goal, but I also think most applications can afford more allocation.
    * There is definite tension between this and general usability. For example, recursive async functions generally require boxing.
* "runtimes" -- 
    * to what extent do we expect users to be able to "mix-and-match" runtimes?

## Roadmap and phases

* 2020 -- 
    * async is possible to use but requires deep expertise
    * async fn only works in a narrow range of places
    * interoperable libraries are possible in some cases
        * if you want to produce a future combinator, you can do it
    * for other cases, they are, but only with the futures crate (stream, I/O)
* 2021
    * async is pleasant to use
    * async fns work everywhere
    * traits for interoperable libraries exist in libstd
    * 
    * runtimes support io-uring
* beyond...
    * async is mature



