## BFQ reverts

#### Patches for [github/lucjan-kernels](https://github.com/sirlucjan/lucjan-kernels/) / [gitlab/lucjan-kernels](https://gitlab.com/sirlucjan/lucjan-kernels/)

#### Patches for [github/linux-lucjan](https://github.com/sirlucjan/linux-lucjan/) / [gitlab/linux-lucjan](https://gitlab.com/sirlucjan/linux-lucjan/)

###### Some patches for BFQ conflict with patches for BFQ-dev.

###### To use lucjan-kernels smoothly apply bfq-reverts before linux-lucjan patch. Otherwise the kernel will not compile.

* [bfq-reverts](https://github.com/sirlucjan/kernel-patches/tree/master/5.10/bfq-reverts-sep) / [bfq-reverts](https://gitlab.com/sirlucjan/kernel-patches/tree/master/5.10/bfq-reverts-sep) - specific patches authored by Piotr Gorski
