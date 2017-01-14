---
author: Mitch Carlson
date: 2016-06-03T06:03:34-07:00
description: Legacy code can be difficult to work with; here I provide a means of dealing with legacy code that will increase confidence in your changes and decrease the chance of regression
draft: true
tags:
- legacy
- refactoring
title: Working with Legacy Code
topics:
- Refactoring code
- Legacy code
type: post
---
Legacy code is often brittle and difficult to maintain. It is typically too complex for a single developer to know in its entirety. There are few, if any, unit tests. Documentation is dated and not fully representative of the current system, and as such it may not be reliable. Numerous changes over time obfuscate the original design, to accommodate new feature development and patches to fix bugs. As technical dept builds, making changes can incur heavy consequences, which may result in a lack of trust or anxiety when considering any new changes.

## What to do:

* Metrics and analytics
    * compile time
        * release
        * debug
    * unit test coverage
        * what code is being exercised
        * what contract is being enforced
    * size
        * executable
        * libraries
            * shared
            * static
    * runtime
        * performance
        * memory usage
        * cache coherence
* Unit tests
    * If changing an interface, an abstraction layer may need to be created first to encapsulate/capture the desired functionality
    * If refactoring the implementation details in support of a current interface, be sure to thoroughly test the expected behavior of the interface

## Unit Test

    * faster than 1/10th of a second
    * small
    * localized
    * in isolation of individual components of software

## Not a Unit Test

    * talks to a database
    * communicates across a network
    * touches the file system
    * special things are required in the environment to run it, e.g., edit config files
    * large
    * integration

Note: use separate tests for the above