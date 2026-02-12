# Build Instructions for Seismic Solidity

This document provides instructions for building the Seismic Solidity compiler from source.

## Prerequisites

### Required Dependencies
- CMake (>= 3.13.0)
- C++ compiler with C++17 support (GCC or Clang)
- Boost libraries (>= 1.70.0)
- OpenSSL development libraries
- zlib development libraries
- Python 3

### Installing Dependencies on Ubuntu/Debian
```bash
sudo apt-get update
sudo apt-get install -y build-essential python3 python3-pip zlib1g-dev libboost-all-dev libssl-dev
```

## Build Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/giwaov/seismic-solidity.git
cd seismic-solidity
```

### 2. Create Build Directory and Configure
```bash
mkdir -p build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
```

### 3. Build the Project
```bash
make -j$(nproc)
```

This will compile the project using all available CPU cores for faster compilation.

### 4. Verify the Build
```bash
./solc/solc --version
```

You should see output similar to:
```
ssolc, the seismic solidity compiler commandline interface
Version: 0.8.31-develop.2026.2.12+commit.264a3fd5.Linux.g++
```

## Build Artifacts

After a successful build, you will find the following binaries in the `build` directory:

- `solc/solc` - The Seismic Solidity compiler (ssolc)
- `test/soltest` - Test suite for running unit tests
- `tools/yul-phaser` - YUL optimizer tool

## Alternative Build Script

You can also use the provided build script:
```bash
bash scripts/build.sh
```

This script will automatically create the build directory, configure CMake, and compile the project.

## Build Types

You can specify different build types when configuring CMake:

- **Release** (default): Optimized for performance
  ```bash
  cmake .. -DCMAKE_BUILD_TYPE=Release
  ```

- **Debug**: Includes debug symbols for debugging
  ```bash
  cmake .. -DCMAKE_BUILD_TYPE=Debug
  ```

- **RelWithDebInfo**: Optimized with debug information
  ```bash
  cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo
  ```

## Troubleshooting

### Missing Boost
If CMake cannot find Boost, ensure you have installed `libboost-all-dev` or install specific Boost components:
```bash
sudo apt-get install libboost-filesystem-dev libboost-program-options-dev libboost-test-dev
```

### Submodule Issues
If you encounter issues with git submodules, initialize them manually:
```bash
git submodule update --init --recursive
```

## Additional Information

For more information about the Seismic Solidity extensions to the EVM, please refer to the [README.md](README.md) file.
