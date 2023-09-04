# asnames-rs

> [!WARNING]
> This crate is deprecated, use [`bgpkit-commons`](https://crates.io/crates/bgpkit-commons) instead.


[![Crates.io](https://img.shields.io/crates/v/asnames)](https://crates.io/crates/asnames)
[![Docs.rs](https://docs.rs/asnames/badge.svg)](https://docs.rs/asnames)
[![License](https://img.shields.io/crates/l/asnames)](https://raw.githubusercontent.com/bgpkit/asnames/master/LICENSE)
[![Discord](https://img.shields.io/discord/919618842613927977?label=Discord&style=plastic)](https://discord.gg/XDaAtZsz6b)

Simple Autonomous System (AS) names and country lookup Rust library

## Data source

- <https://ftp.ripe.net/ripe/asnames/asn.txt>

## Data definition

```rust
#[derive(Debug, Clone)]
pub struct AsName {
    pub asn: u32,
    pub name: String,
    pub country: String,
}
```

## Usage

```rust
use std::collections::HashMap;
use asnames::{AsName, load_asnames};

let asnames: HashMap<u32, AsName> = load_asnames().unwrap();
assert_eq!(asnames.get(&3333).unwrap().name, "RIPE-NCC-AS Reseaux IP Europeens Network Coordination Centre (RIPE NCC)");
assert_eq!(asnames.get(&400644).unwrap().name, "BGPKIT-LLC");
assert_eq!(asnames.get(&400644).unwrap().country, "US");
```
