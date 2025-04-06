# Android Logical Partition Tools

This repository contains tools for working with Android's logical partition (dynamic partition) format, extracted from AOSP and improved compiler warnings and modern C++ compatibility.

## Included Tools

- **lpunpack**: Extracts partitions from an Android super.img or similar logical partition image
- **lpmake**: Creates logical partition images from individual partition files
- **lpdump**: Displays information about a logical partition image
- **lpflash**: Flashes a logical partition image to a device
- **lpadd**: Adds a partition to an existing logical partition image

## Installation Options

### Option 1: Download Prebuilt Binaries

You can download prebuilt binaries from the [Releases](https://github.com/itsNileshHere/android-lptools/releases).

1. Download the release appropriate for your platform
2. Extract the archive
3. Move the binaries to a location in your PATH

### Option 2: Build from Source

#### Prerequisites

- C/C++ compiler (clang or gcc)
- Make or similar build tool
- Bash shell

#### Build Instructions

```bash
# Clone the repository
git clone https://github.com/itsNileshHere/android-lptools.git
cd android-lptools

# Build the tools
./make.sh

# Tools will be available in the bin/ directory
bin/lpunpack  # Run lpunpack
```

## Usage Examples

### lpunpack

Extract partitions from a super.img file:

```bash
./bin/lpunpack super.img output_directory
```

### lpmake

Create a super.img file:

```bash
./bin/lpmake --metadata-size 65536 \
  --super-name super \
  --metadata-slots x \
  --device super:x \
  --group main:x \
  --partition system:readonly:x:main \
  --image system=system.img \
  --partition vendor:readonly:x:main \
  --image vendor=vendor.img \
  --output super.img
```

### lpdump

Display information about a super.img file:

```bash
./bin/lpdump super.img
```

## Source

The source code is derived from the Android Open Source Project (AOSP) and has been modified to fix compiler warnings and improve compatibility with modern C++ standards.

## License

This project is licensed under the same terms as the original AOSP code.
