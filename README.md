# GlobWalker

_Fork of [GlobWalk](https://github.com/Gilnaa/globwalk)_

[![](https://docs.rs/globwalker/badge.svg)](https://docs.rs/globwalker/)
![License](https://img.shields.io/crates/l/globwalker.svg)
[![crates.io](https://img.shields.io/crates/v/globwalker.svg)](https://crates.io/crates/globwalker)

Recursively find files in a directory using globs.

Based on both `walkdir` & `ignore` (❤), this crate inherits many goodies from
both, such as limiting search depth and amount of open file descriptors.

Licensed under MIT.

### Why not `glob` ###

 - The `glob` crate does not support having `{a,b}` in patterns.
 - `globwalker` can match several glob-patterns at the same time.
 - `globwalker` supports excluding results with `!`.
 - `glob` searches for files in the current working directory, whereas `globwalker` starts at a specified base-dir.

### Usage ###

To use this crate, add `globwalker` as a dependency to your project's `Cargo.toml`:

```toml
[dependencies]
globwalker = "0.9.0"
```

The following piece of code recursively find all `png`, `jpg`, or `gif` files:

```rust
extern crate globwalker;

use std::fs;

for img in globwalker::glob("*.{png,jpg,gif}").unwrap() {
    if let Ok(img) = img {
        println!("{:?}", img);
    }
}
```

See the [documentation](https://docs.rs/globwalker/) for more details.
