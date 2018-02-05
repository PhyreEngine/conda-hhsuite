This repository contains a [conda][conda] recipe for building [HHsuite][hh], a
tool for remote homology detection via Hidden Markov Model matching.

## Prerequisites

1. You will need an installation of [conda][miniconda].

2. Your root conda installation must have the `conda-build` installed.

## Building

You should be able to build this package by simply running `conda build .`.

## Patches

The default build process for HHsuite attempts to detect which CPU features are
available on the host system, and automatically optimises for those features.
We want to distribute binary versions of the HHsuite tools, so this recipe
patches the build system and explicitly compiles versions for several CPU
architectures.

To choose the package to be installed by conda, install the metapackage
`arch-{architecture}`, where `{architecture}` is the architecture of your CPU.
The list of available architectures can be found by running `conda search
'arch-*'`.

This package installs scripts in `$PREFIX/etc/conda/activate.d` and
`$PREFIX/etc/conda/deactivate.d` that set and unset the environment variable
`$HHLIB` when the conda environment is `source`d.

[conda]: https://conda.io
[miniconda]: https://conda.io/miniconda.html
[hh]: https://github.com/soedinglab/hh-suite
