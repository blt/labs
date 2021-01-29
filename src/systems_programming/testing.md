# Testing

Testing and software correctness are different but related things. "Correct"
software is proven true in some important sense, like
[seL4](https://sel4.systems/). Correctness is something our software culture
still struggles to achieve. Testing is a process to demonstrate the absence of
error for some inputs and previous state. It's a piecemeal process, where
"correctness" is global.

I'm very fond of testing tools that use randomness or exhaustiveness to explore
the state space of a program, since human beings are (and I am especially) bad
at coming up with failure causing inputs for programs. Here's some:

* [Automated property based testing for Rust (with shrinking)](https://github.com/BurntSushi/quickcheck)
* [disorderfs](https://salsa.debian.org/reproducible-builds/disorderfs)
* [Concurrency permutation testing tool for Rust](https://github.com/tokio-rs/loom)
