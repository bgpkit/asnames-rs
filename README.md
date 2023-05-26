# asnames-rs

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
