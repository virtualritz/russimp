# russimp ![russimp](https://github.com/jkvargas/russimp/workflows/russimp/badge.svg?branch=master) [![Crates.io](https://img.shields.io/crates/v/russimp.svg)](https://crates.io/crates/russimp)

High level Rust bindings for [`assimp`](https://github.com/assimp/assimp).

# Overview

Russimp is a high level wrapper around the `assimp` library. This is the Swiss
army knife of polygonal 3D geometry import (and partly export). All supported
formats are read into the same data structure.

The bindings are based on `assimp` `5.0.1`.

## Helping

You are very welcome to help with development, adding a feature, fixing a
problem or just refactoring.

When making a PR try to add some tests. =)

We also need help to make sure the build works as expected on Windows.

## Testing

To test the API on your local machine you will need to have the environment
variable GITHUB_WORKSPACE set up with the project root path.

```shell
GITHUB_WORKSPACE=./ cargo test --verbose
```

# Requirements

## Rust

Russimp builds with Rust stable, beta or nightly. You will also need CMake and
C & C++ compiler installed.

# How to Use It?

Just call Scene::from with the filename and the flags you want. From the scene
you will have access to the underlying structs.

```rust
let scene = Scene::from_file(
     "myfile.blend",
     vec![
          PostProcessSteps::CalcTangentSpace,
          PostProcessSteps::Triangulate,
          PostProcessSteps::JoinIdenticalVertices,
          PostProcessSteps::SortByPType
     ])
     .unwrap();
```
