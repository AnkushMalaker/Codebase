# Customize build with Release Profile

Cargo has `dev` profile when we use `cargo build` and `release` when we do `cargo build --release`  
We can add `[profile.dev]` to our `Cargo.toml` file to define the `opt-level` (level of optimization. Range is 0-3, higher means more compile time but faster execution. dev default is 0, release default is 3.). Same with `[profile.release]`

# Publishing crates, cargo workspaces, installing binaries from cargo and extending cargo with custom commands need no specific notes.
