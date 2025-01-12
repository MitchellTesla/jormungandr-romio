#  Jörmungandr-Æxperimental Full-Node 
[![API Check](https://github.com/MitchellTesla/Alfa-ROMio/actions/workflows/api.yml/badge.svg)](https://github.com/MitchellTesla/ALfa-ROMio/actions/workflows/api.yml)
[![Python scripts linters](https://github.com/MitchellTesla/jormungandr-XEN/actions/workflows/python-scripts.yml/badge.svg)](https://github.com/MitchellTesla/jormungandr-XEN/actions/workflows/python-scripts.yml)

Do NOT Use!..... Alfa-ROMeo is an experimental implementation of Jörmungandr, actively being tested and developed * (WIP) work-in-progress

This experimental node implementation is written in rust, with the initial aim to support the Ouroboros type of consensus protocol.

This node is a participant of a blockchain network, continuously making, sending, receiving, and validating blocks. All nodes are responsible for making sure that all the rules of the protocol(s) are followed!!! 

> Just because you call something a blockchain, that doesn't mean you aren't
> subject to normal engineering laws or physics...


User guide documentation available [https://input-output-hk.github.io/jormungandr/][docs]

<p align="center">
  <img src="jormungandr-XENsmite_4kwallpaper.png" alt="demo" />
</p>

# Mythology

Jörmungandr refers to the Midgard Serpent in Norse mythology. It is a hint to Ouroboros, the Ancient Egyptian serpent,(The World Serpent) who ate it's own tail, as well as ALL THE LEVERAGE, and the IOHK paper on proof of stake (POS). ;)
[docs]: https://input-output-hk.github.io/jormungandr

## It is recommended that you use the original Jörmungandr source code, and NOT this specific implementation.

## Master current build status

| CI | Status | Description |
|---:|:------:|:------------|
| CircleCI | [![CircleCI](https://circleci.com/gh/input-output-hk/jormungandr/tree/master.svg?style=svg)](https://circleci.com/gh/input-output-hk/jormungandr/tree/master) | Master and PRs |

## Install from Binaries

Use the [Latest Binaries](https://github.com/input-output-hk/jormungandr/releases),
available for many operating systems and architectures.

## Install from Source

### Prerequisites

#### Rust

Get the [Rust Compiler](https://www.rust-lang.org/tools/install) (latest stable
version is recommended, minimum required: 1.39+).

```sh
rustup install stable
rustup default stable
rustc --version # if this fails, try a new command window, or add the path (see below)
```

#### Dependencies

* For detecting build dependencies:
  * Homebrew on macOS.
  * `vcpkg` on Windows.
  * `pkg-config` on other Unix-like systems.
* C compiler (see [cc-rs](https://github.com/alexcrichton/cc-rs) for more details):
  * Must be available as `cc` on Unix and MinGW.
  * Or as `cl.exe` on Windows.

#### Path

* Win: Add `%USERPROFILE%\.cargo\bin` to the  environment variable `PATH`.
* Lin/Mac: Add `${HOME}/.cargo/bin` to your `PATH`.

#### protobuf

* The [Protocol Buffers](https://developers.google.com/protocol-buffers) version
  bundled with crate `prost-build` will be used.
* For distribution or container builds in general, it's a good practice to
  install `protoc` from the official distribution package if available.

### Commands

Check `<latest release tag>` on
https://github.com/input-output-hk/jormungandr/releases/latest

```sh
git clone https://github.com/input-output-hk/jormungandr
cd jormungandr
git checkout tags/<latest release tag> #replace this with something like v1.2.3
cargo build # skip this if you do not want to run the tests
cargo test  # skip this if you do not want to run the tests
cargo install --locked --path jormungandr # --features systemd # (on linux with systemd)
cargo install --locked --path jcli
```

This will install 2 tools:

* `jormungandr`: the node part of the blockchain;
* `jcli`: a command line helper tool to help you use and setup the node;

<p align="center">
  <img src="Jormungandr-XEN.png" alt="demo" />
</p>

## Configuration Basics

A functional node needs 2 configurations:

1. Its own [node configuration](https://input-output-hk.github.io/jormungandr/configuration/introduction.html):
   Where to store data, network configuration, logging.
2. The [blockchain genesis configuration](https://input-output-hk.github.io/jormungandr/advanced/introduction.html),
   which contains the initial trusted setup of the blockchain: coin
   configuration, consensus settings, initial state.

In normal use, the blockchain genesis configuration is given to you or
automatically fetched from the network.

## Quick-Start - Public Mode

To start a new node from scratch on a given blockchain, you need to know the
block0 hash of this blockchain for trust purpose and internet peers to connect
to. The simplest way to start such a node is:

    jormungandr --block0-hash <HASH> --trusted-peers <IPs>

## Quick-Start - Cardano Shelly Testnet

* [Official Cardano Shelly Testnet Documentation](https://testnet.iohkdev.io/cardano/shelley/).
* For the **nightly testnet**, ask within the
  [Cardano Stake Pool Workgroup Telegram group](https://web.telegram.org/#/im?p=@CardanoStakePoolWorkgroup).

## Quick-Start - Private Mode

Follow instructions on installation, then to start a private and minimal test
setup:

```sh
mkdir mynode
cd mynode
python3 PATH/TO/SOURCE/REPOSITORY/scripts/bootstrap.py <options>
```

Use the following recommended bootstrap options:

```sh
bootstrap --bft # BFT setup
bootstrap --genesis-praos --slot-duration 2 # Genesis-praos setup
bootstrap --help # further help
```

The bootstrap script creates a simple setup with a faucet with 10 millions
coins, a BFT leader, and a stake pool.

Both scripts can be used to do simple limited operation through the jcli
debugging tools.

## Documentation

Documentation is available in the markdown format [here](doc/SUMMARY.md)

## License

This project is licensed under either of the following licenses:

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
  http://www.apache.org/licenses/LICENSE-2.0)
* MIT license ([LICENSE-MIT](LICENSE-MIT) or
  http://opensource.org/licenses/MIT)
