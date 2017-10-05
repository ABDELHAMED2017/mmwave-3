[![Build Status](https://travis-ci.org/nyuwireless-unipd/mmwave.svg?branch=master)](https://travis-ci.org/nyuwireless-unipd/mmwave)

# mmWave ns-3 module #

This is an [ns-3](https://www.nsnam.org "ns-3 Website") mmWave module for the simulation
of 5G mmWave cellular networks. A description of this module can be found on [arXiv](https://arxiv.org/abs/1705.02882 "mmwave paper").

Please clone the [main repo](https://github.com/nyuwireless-unipd/ns3-mmwave/ "ns3-mmwave") (with the branches master, with the basic functionalities, and new-handover, with all the functionalities provided here) for a complete install or follow the instructions provided below.

## Getting started ##

### Prerequisites ###

To run simulations using this module, you will need to install ns-3, clone
this repository inside the `src` directory and patch the LTE module. 
Required dependencies include git and a build environment.

#### Installing dependencies ####

On Ubuntu, run the following to install all the required packets:

```bash
sudo apt install git build-essential
```

macOS instructions will be added soon.

<!-- On macOS, you can install the command line tools with:

```bash
xcode-select --install
```

while Mercurial and git can be installed via [Homebrew](https://brew.sh/ "Homebrew
homepage"):

```bash
brew install mercurial git
``` -->

#### Downloading #####

First, clone the main ns-3 repository:

```bash
git clone https://github.com/nsnam/ns-3-dev-git ns-3-dev
cd ns-3-dev/src
```

Then, clone the mmwave module and patch the LTE one:
```bash
git clone https://github.com/nyuwireless-unipd/mmwave mmwave
cp mmwave/ns-3-patches/patch-for-lte.diff lte
cd lte
patch -p1 -N -E -i patch-for-lte.diff
rm patch-for-lte.diff

```

### Compilation ###

Configure and build ns-3 from the `ns-3-dev` folder:

```bash
./waf configure --enable-tests --enable-examples
./waf build
```

If you are not interested in using the Python bindings, use
```bash
./waf configure --enable-tests --enable-examples --disable-python
./waf build
```

## Documentation and examples ##

For a complete description and examples, refer to:

- [End-to-End Simulation of 5G mmWave Networks](https://arxiv.org/abs/1705.02882 "comst paper")
- [A Framework for End-to-End Evaluation of 5G mmWave Cellular Networks in ns-3](https://arxiv.org/abs/1602.06932 "wns3 paper")
- [ Performance Comparison of Dual Connectivity and Hard Handover for LTE-5G Tight Integration](https://arxiv.org/abs/1607.05425 "simutools paper")
- [ns-3 manual](https://www.nsnam.org/docs/manual/html "ns-3 Manual")

## Authors ##

 - Marco Mezzavilla < mezzavilla@nyu.edu>
 - Menglei Zhang <menglei@nyu.edu>
 - Michele Polese <michele.polese@gmail.com>
 - Sourjya Dutta <sdutta@nyu.edu>
 - Russell Ford <russell.ford@nyu.edu>
 - Marco Giordani <m.giordani91@gmail.com>

## License ##

This software is licensed under the terms of the GNU GPLv2 (the same license
that is used by ns-3). See the LICENSE.md file for more details.
