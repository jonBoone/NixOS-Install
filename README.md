# NixOS Installation
## last update: 2022-12-24

### Overview

This file documents my process for installing NixOS on my Lenovo Legion S7-15ACH6 Laptop.  I purchased this machine in order to do software development, primarily of an open source nature.

#### x86_64 Laptop for Software Development

In the recent past, I've primarily relied on Apple hardware along with VMs for Linux functionality.  When Apple exclusively used SoCs that leveraged Intel processors, this meant I could work on code bases that were intended to run natively on both Linux (x86_32 and x86_64), as well as macOS (which most recently only supported x86_64).  With the introduction of the new Apple SIlicon M* line of SoCs, this became more challenging, which led me to seriously consider an x86_64 machine upon which to run Linux natively. When I initially purchased the machine, I did a bit of research (starting with reading [this Reddit post](https://www.reddit.com/r/pop_os/comments/sn6c3e/pop_os_2110_on_legion_slim_7_ryzen_7_5800h_3060/)) before settling on using [System76's Pop!_OS](https://pop.system76.com/).  This proved to be a nearly seamless experience with almost all of the built-in hardware working out of the box.  The only exceptions I am aware of were the Sonix camera and the ELAN WBF Fingerprint Sensor, neither of which I ever put any effort into getting to work.

#### Deterministic Reproducability

My system design and architecture experience has taught me that the same value provided through using deterministic, reproducible language and library versions in building software artifacts applies to the configuration of the infrastructure upon which the artifacts execute.
