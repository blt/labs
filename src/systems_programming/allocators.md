# Allocators

An "allocator" is a library that sets aside an area in computer memory -- called
the "heap" as opposed to the "stack" and "static" memory -- for use by some
other program. An allocator may or may not keep track of these "allocations" in
its private mechanism and it may or may not allow for callers to "return"
allocations to the allocator, thus freeing up that memory for us by another
caller. If you've ever called `malloc`, `free` et all in C you've interacted
with an allocator. If you've used a language with a runtime that manages memory
you have done so indirectly. If you've only programmed for embedded devices that
manage memory themselves and allocate only at startup then, well, kudos.

The third chapter of my [new
book](../notes/writing-and-talking.md#systems-programming-for-normal-people)
introduces the memory heirarchy of a computer, starting with static memory,
working into the stack and out to the heap. By the end of the chapter the
reader's got the ability to swap in new allocators but no ability to write them,
on account of the book hasn't built up any expertise in thread-safe
programming. Next chapter aims to teach that very thing and, in so doing, will
build up several allocators. We'll see how successful I am. Anyhow, I've been
going back through the literature on allocators. Here's what's interesting I've
turned up so far, in no particular order:

* Andrei Alexandrescu: [Policy–Based Memory Allocation](http://erdani.org/publications/cuj-2005-12.pdf)
* David Gay et al: [Memory Management with Explicit Regions](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.483.9985&rep=rep1&type=pdf)
* Emery Berger et al: [Composing High-Performance Memory Allocators](https://people.cs.umass.edu/~emery/publications/berger-pldi2001.pdf)
* Jason Evans: [A Scalable Concurrent `malloc(3)` Implementation for FreeBSD](https://www.bsdcan.org/2006/papers/jemalloc.pdf)
* Jeff Bonwick: [Magazines and Vmem: Extending the Slab Allocator to Many CPUs and Arbitrary Resources](https://www.usenix.org/conference/2001-usenix-annual-technical-conference/magazines-and-vmem-extending-slab-allocator-many)
* Jeff Bonwick: [The Slab Allocator: An Object-Caching Kernel Memory Allocator](https://people.eecs.berkeley.edu/~kubitron/courses/cs194-24-S14/hand-outs/bonwick_slab.pdf)
* Maged Michael: [Scalable Lock-Free Dynamic Memory Allocation](https://www.cs.tufts.edu/~nr/cs257/archive/maged-michael/pldi-2004.pdf)
* Paul Lietar et al: [snmalloc: A Message Passing Allocator](https://www.microsoft.com/en-us/research/uploads/prod/2020/04/snmalloc.pdf)
* Trishul M. Chilimbi et al: [Cache-Conscious Structure Definition](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/12/definition_distr.pdf)

## Rust Allocators

These are interesting Rust allocators that I'm aware of:

* [bitpool](https://github.com/jamesmunns/bitpool/)
* mycelium's [buddy](https://github.com/hawkw/mycelium/blob/main/alloc/src/buddy.rs)
* [wee_alloc](https://github.com/rustwasm/wee_alloc/tree/HEAD/wee_alloc)
* [sp-allocator](https://github.com/paritytech/substrate/tree/HEAD/primitives/allocator)
* [basicalloc](https://github.com/wackywendell/basicalloc)
