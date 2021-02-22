# Measuring Performance

One of the more difficult aspects of systems programming is figuring out how to
optimize work, and sometimes to even define what "optimize" means. Do we want
more clear code, less memory consumption, lower latency responses, less variant
real-time responses, better throughput etc etc. What happens when optimization
goals conflict?

Anyhow, here's a list of interesting resources for measuring performance:

* [Performance Engineering Requires Stable Benchmarks](https://buttondown.email/nelhage/archive/f6e8eddc-b96c-4e66-a648-006f9ebb6678)
* [CI for performance: Reliable benchmarking in noisy environments](https://pythonspeed.com/articles/consistent-benchmarking-in-ci/)
* [Criterion.rs v0.3.4 And Iai 0.1.0](https://bheisler.github.io/post/criterion-rs-0-3-4/)
* [Achieving 11M IOPS & 66 GB/s IO on a Single ThreadRipper Workstation](https://tanelpoder.com/posts/11m-iops-with-10-ssds-on-amd-threadripper-pro-workstation/)
* [Always-on Profiling for Production Systems](https://0x.tools/)
* [flamegraph-rs](https://github.com/flamegraph-rs/flamegraph)

The `flamegraph-rs`
[README](https://github.com/flamegraph-rs/flamegraph#systems-performance-work-guided-by-flamegraphs)
has an excellent section on performance work.
