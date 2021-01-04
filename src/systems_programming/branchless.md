# Branchless Programming

Modern processors have very deep pipelines, making branch mispredictions
costly. Compilers are pretty good at removing branches but not perfect at
it. Here's a list of interesting things I've read on "branchless" programming:

* https://jaredgorski.org/notes/zett-branchless-programming-2020-08-11-1532/
* https://github.com/alpbintug/Branchless-programming
* https://arxiv.org/pdf/1602.06426.pdf
* https://hbfs.wordpress.com/2008/08/05/branchless-equivalents-of-simple-functions/
* https://bluejekyll.github.io/blog/rust/2018/01/10/branchless-rust.html
* https://www.blueraja.com/blog/285/branchless-conditionals-compiler-optimization-technique
* https://www.infoq.com/articles/making-code-faster-taming-branches/
* https://www.chessprogramming.org/Avoiding_Branches

The Chess Programming wiki is probably the most obsessive piece in this list
with additional references around the internet. I mean this in a good way. Chess
folks do some of the most unusual high-performance programming around.
