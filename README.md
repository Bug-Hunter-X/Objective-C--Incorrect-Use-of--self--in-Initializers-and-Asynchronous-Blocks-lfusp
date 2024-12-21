# Objective-C: `self` Misuse in Initializers and Asynchronous Blocks

This repository demonstrates a common Objective-C error involving incorrect use of `self` within initializers and asynchronous blocks.  Improper handling of `self` can lead to crashes due to uninitialized objects or memory leaks due to retain cycles.

The `bug.m` file showcases the problematic code, while `bugSolution.m` provides the corrected version.

## Problem

* **Uninitialized `self` in Initializers:** Accessing `self`'s members before `super`'s initializer completes results in accessing uninitialized memory.
* **Retain Cycles in Asynchronous Blocks:** Retaining `self` within a block without using `__weak` or `__block` can cause retain cycles, leading to memory leaks.

## Solution

* **Initialize in Correct Order:**  Ensure all properties are initialized after the superclass initializer finishes successfully.
* **Weak References in Blocks:** Use `__weak` to break retain cycles when capturing `self` in blocks.