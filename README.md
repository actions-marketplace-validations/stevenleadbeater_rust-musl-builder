# GitHub Action for Rust and MUSL

Action provides an environment with stable Rust, MUSL and x86_64-unknown-linux-musl target. This is based heavily off https://github.com/emk/rust-musl-builder. 
code for the base image from which the Dockerfile derives is here: https://github.com/stevenleadbeater/rust-musl-builder-base
The following static binaries are compiled in to the base image as per the emk/rust-musl-builder repo

1. Open SSL
2. ZLib
3. LibPQ

## Usage

To compile a rust binary/library with x86_64-unknown-linux-musl target:

```yaml
name: Static Musl Build

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
      
    - name: Build static
      uses:  stevenleadbeater/rust-musl-builder@master
      with:
          args: /bin/bash -c "cargo build --release --target=x86_64-unknown-linux-musl"
```

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE-MIT.txt).

