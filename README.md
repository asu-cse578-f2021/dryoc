[![Docs](https://docs.rs/dryoc/badge.svg)](https://docs.rs/dryoc) [![Crates.io](https://img.shields.io/crates/v/dryoc)](https://crates.io/crates/dryoc) [![Build & test](https://github.com/brndnmtthws/dryoc/actions/workflows/build-and-test.yml/badge.svg)](https://github.com/brndnmtthws/dryoc/actions/workflows/build-and-test.yml) [![Codecov](https://img.shields.io/codecov/c/github/brndnmtthws/dryoc)](https://app.codecov.io/gh/brndnmtthws/dryoc/)

# dryoc: Don't Roll Your Own Crypto™<sup><sup>[1](#footnotes)</sup></sup>

dryoc is a pure-Rust, general-purpose cryptography library. It's provides an
implementation of the excellent
[libsodium](https://github.com/jedisct1/libsodium) library, in _pure_ Rust.

![Granny says no](dryoc.png)

The purpose of this project is to provide a pure-Rust, mostly drop-in
replacement for libsodium. This library has nearly the same ergonomics as
libsodium (referred to in dryoc as the _Classic_ API), such that people
familiar with libsodium can use this library nearly interchangeably. While
the API is not 100% identical to libsodium, most functions have the same or
very similar signatures.

In addition to the Classic API, there's a _Rustaceous_ API which aims to bring
an idiomatic Rust implementation of libsodium's core features: public and
secret key authenticated cryptography and general-purpose cryptography tools.

Not all features from libsodium are implemented here, either because there
exist better implementations in other crates, or because they aren't
necessary as part of this crate.

Additionally, this crate provides exceptionally safe cryptography thanks to
Rust's safety features. The Rustaceous API is designed designed to make it
difficult to shoot yourself in the foot. It's worth noting, however, you
certainly can still shoot yourself if you choose (either by leaking private
data, using insecure hardware, OPSEC issues, etc).

## Features

* Many libsodium implemented with both Classic and Rustaceous API
* Protected memory handling
* [Serde](https://serde.rs/) support (with `features = ["serde"]`)

## Project status

The following libsodium features are currently implemented, or awaiting
implementation:

* [x] [Public-key cryptography](https://doc.libsodium.org/public-key_cryptography) (`crypto_box_*`)
* [x] [Secret-key cryptography](https://doc.libsodium.org/secret-key_cryptography) (`crypto_secretbox_*`)
* [x] [Point*scalar multiplication](https://doc.libsodium.org/advanced/scalar_multiplication) (`crypto_scalarmult_base`)
* [x] [Zeroing memory](https://doc.libsodium.org/memory_management) with [zeroize](https://crates.io/crates/zeroize)
* [x] [Generating random data](https://doc.libsodium.org/generating_random_data) (`randombytes_buf`)
* [x] [Encrypted streams](https://doc.libsodium.org/secret-key_cryptography/secretstream) (`crypto_secretstream_*`)
* [x] [Memory locking](https://doc.libsodium.org/memory_management) (`sodium_mlock`, `sodium_munlock`, `sodium_mprotect_*`)
* [x] [Encrypting related messages](https://doc.libsodium.org/secret-key_cryptography/encrypted-messages) (`sodium_increment`)
* [x] [Generic hashing](https://doc.libsodium.org/hashing/generic_hashing) (`crypto_generichash_*`)
* [x] [Secret-key authentication](https://doc.libsodium.org/secret-key_cryptography/secret-key_authentication)
* [x] [One-time authentication](https://doc.libsodium.org/advanced/poly1305) (`crypto_onetimeauth_*`)
* [x] [Sealed boxes](https://doc.libsodium.org/public-key_cryptography/sealed_boxes)
* [x] [Key derivation](https://doc.libsodium.org/key_derivation) (`crypto_kdf_*`)
* [x] [Key exchange](https://doc.libsodium.org/key_exchange) (`crypto_kx_*`)
* [ ] [Public-key signatures](https://doc.libsodium.org/public-key_cryptography/public-key_signatures) (`crypto_sign_*`)
* [ ] [Short-input hashing](https://doc.libsodium.org/hashing/short-input_hashing)
* [ ] [Password hashing](https://doc.libsodium.org/password_hashing/default_phf)
* [ ] [Public-key signatures](https://doc.libsodium.org/public-key_cryptography/public-key_signatures)

The following libsodium features are either incomplete, not exposed as public
APIs, or not implemented; you may find equivalent functionality in other
crates:

* [Stream ciphers](https://doc.libsodium.org/advanced/stream_ciphers) (use [salsa20](https://crates.io/crates/salsa20) crate directly instead)
* [Helpers](https://doc.libsodium.org/helpers) and [padding](https://doc.libsodium.org/padding) utilities
* [Advanced features](https://doc.libsodium.org/advanced):
  * [Scrypt](https://doc.libsodium.org/advanced/scrypt) (use [scrypt](https://crates.io/crates/scrypt) crate directly instead)
  * [Ed25519 to Curve25519](https://doc.libsodium.org/advanced/ed25519-curve25519) (try [dalek.rs](https://dalek.rs/))
  * [Finite field arithmetic](https://doc.libsodium.org/advanced/point-arithmetic) (try [dalek.rs](https://dalek.rs/))

## Stargazers over time

[![Stargazers over time](https://starchart.cc/brndnmtthws/dryoc.svg)](https://starchart.cc/brndnmtthws/dryoc)

## Other NaCl-related Rust implementations worth mentioning

* [sodiumoxide](https://crates.io/crates/sodiumoxide)
* [crypto_box](https://crates.io/crates/crypto_box)

## Footnotes

1. Not actually trademarked.
