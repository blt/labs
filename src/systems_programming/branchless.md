# Branchless Programming

Modern processors have very deep pipelines, making branch mispredictions
costly. Compilers are pretty good at removing branches but not perfect at
it. Here's a list of interesting things I've read on "branchless" programming:

* [Branchless programming, an article](https://jaredgorski.org/notes/zett-branchless-programming-2020-08-11-1532/)
* [Branchless Programming, a Github repo](https://github.com/alpbintug/Branchless-programming)
* [A loopless and branchless `O(1)` algorithm to generate the nextDyck word](https://arxiv.org/pdf/1602.06426.pdf)
* [Branchless Equivalents of Simple Functions](https://hbfs.wordpress.com/2008/08/05/branchless-equivalents-of-simple-functions/)
* [Branchless Rust](https://bluejekyll.github.io/blog/rust/2018/01/10/branchless-rust.html)
* [Branchless Conditionals (Compiler Optimization Technique)](https://www.blueraja.com/blog/285/branchless-conditionals-compiler-optimization-technique)
* [Making Code Faster: Taming Branches](https://www.infoq.com/articles/making-code-faster-taming-branches/)
* [Chess Programming Wiki: Avoiding Branches](https://www.chessprogramming.org/Avoiding_Branches)

The Chess Programming wiki is probably the most obsessive piece in this list
with additional references around the internet. I mean this in a good way. Chess
folks do some of the most unusual high-performance programming around.
