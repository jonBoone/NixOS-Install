# NixOS Installation
## last update: 2022-12-24

### Overview

This file documents my process for installing NixOS on my Lenovo Legion S7-15ACH6 Laptop.  I purchased this machine in order to do software development, primarily of an open source nature.

#### x86_64 Laptop for Software Development

In the recent past, I've primarily relied on Apple hardware along with VMs for Linux functionality.  When Apple exclusively used SoCs that leveraged Intel processors, this meant I could work on code bases that were intended to run natively on both Linux (x86_32 and x86_64), as well as macOS (which most recently only supported x86_64).  With the introduction of the new Apple SIlicon M* line of SoCs, this became more challenging, which led me to seriously consider an x86_64 machine upon which to run Linux natively. When I initially purchased the machine, I did a bit of research (starting with reading [this Reddit post](https://www.reddit.com/r/pop_os/comments/sn6c3e/pop_os_2110_on_legion_slim_7_ryzen_7_5800h_3060/)) before settling on using [System76's Pop!_OS](https://pop.system76.com/).  This proved to be a nearly seamless experience with almost all of the built-in hardware working out of the box.  The only exceptions I am aware of were the Sonix camera and the ELAN WBF Fingerprint Sensor, neither of which I ever put any effort into getting to work.

#### Deterministic Reproducability

Recent practice in software artifact creation has leaned heavily into the concept of determinstic reproducability, in an attepmt to avoid the `Works On My Machine` problem. I don't know the first time this idea was articulated, but it was prominent enough that a [WOMM certification program](https://blog.codinghorror.com/the-works-on-my-machine-certification-program/) was publicized by Jeff Atwood on 2007-03-15.

One of the techniques used to address this isue is to build an environment that is predictable and reproducable.  At a minimum, this would mean having a consistent set of tools used to create the software artifacts, including a specific version of any programming languages and their implementations, as well as associated libraries.  In the context of Python, this would mean using `pyenv` to create a virtual environment with specificed versions of Python and the associated libraries.  The specificiation of the environment components is documented and can be shared on all machines used to create the executable versions of the artifacts on each target platform.

This is a powerful tool for enabling multiple developers to work on the same code base while preserving consistent behavior across development machines.  This same environment specification can be used to create a target platform environment that is consistent across deployment targets as well.  The same is achieved in the Java world through the requirements for a Java Runtime version and the distribution of the `.jar` files for execution on the target machines.  


My system design and architecture experience has taught me that the same value provided by using deterministic, reproducible language and library versions in software artifact construction can be readily applied to underlying infrastructure upon which the artifacts are run.  This runs the gamut from consistent sourcing of physical hardware component configurations, pinned release versions of firmware and operating systems, through the configuration and maintenance of the hosts and their interconnections to each other and the larger Internet. With the rise of cloud computing, the majority of these tasks can be accomplished through a technique known as Infrastructure as Code (IaC).

Applying these techniques to personal systems seemed excessively challenging (sometimes in matching the concepts applied to servers to machines designed for personal use; more often through cost constraints).  The attempt to provide a consistent base of software for installation on a particular personal machine has been addressed through the use of package managers (sometimes for operating systems, such as [`homebrew`](https://brew.sh); sometimes for individual programming languages, such as [`pip`](https://https://pypi.org/project/pip/) for python; sometimes for particular specializations such as [`anaconda`](https://www.anaconda.com) for data science).  These can make the installation and upgrade of the relevant components (relatively) easy, but consistently applying updates on multiple machines still remains non-trivial.
