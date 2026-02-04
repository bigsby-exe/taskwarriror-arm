# Taskwarrior ARM32 Builds

This repository automatically builds [Taskwarrior](https://github.com/GothenburgBitFactory/taskwarrior) for 32-bit ARM systems (ARMv7l), specifically targeting Raspberry Pi devices running DietPi or similar Debian-based distributions.

## What This Repository Does

This repository uses GitHub Actions to:
- Automatically detect new Taskwarrior releases
- Cross-compile Taskwarrior for ARM32 (armv7l) systems
- Create GitHub releases with pre-built binaries ready for installation

## Downloading Pre-built Binaries

1. Go to the [Releases](https://github.com/YOUR_USERNAME/taskwarriror-arm/releases) page
2. Download the latest `taskwarrior-X.X.X-arm32.tar.gz` file
3. Follow the installation instructions below

## Installation on DietPi / Raspberry Pi

### Quick Install

```bash
# Download the latest release (replace X.X.X with actual version)
wget https://github.com/YOUR_USERNAME/taskwarriror-arm/releases/download/taskwarrior-X.X.X-arm32/taskwarrior-X.X.X-arm32.tar.gz

# Extract the archive
tar xzvf taskwarrior-X.X.X-arm32.tar.gz

# Install to system directories
sudo cp -r usr/* /usr/

# Update library cache
sudo ldconfig

# Verify installation
task --version
```

### Manual Installation Steps

1. **Download the release archive** from the [Releases](https://github.com/YOUR_USERNAME/taskwarriror-arm/releases) page

2. **Extract the archive**:
   ```bash
   tar xzvf taskwarrior-X.X.X-arm32.tar.gz
   ```

3. **Install the binaries**:
   ```bash
   sudo cp -r usr/* /usr/
   sudo ldconfig
   ```

4. **Verify the installation**:
   ```bash
   task --version
   ```

5. **Initialize Taskwarrior** (first time setup):
   ```bash
   task
   ```

## Manual Build Trigger

You can manually trigger a build for a specific Taskwarrior version:

1. Go to the **Actions** tab in this repository
2. Select **Build Taskwarrior for ARM32** workflow
3. Click **Run workflow**
4. Optionally specify a version (e.g., `3.4.2`) or leave empty to build the latest release
5. Click **Run workflow** to start the build

## Build Schedule

The workflow runs automatically:
- **Weekly**: Every Monday at 00:00 UTC to check for new Taskwarrior releases
- **Manual**: On-demand via workflow dispatch

## Build Details

- **Target Architecture**: ARM32 (armv7l, arm-linux-gnueabihf)
- **Compatible Systems**: Raspberry Pi (32-bit), DietPi, and other ARM32 Debian-based systems
- **Build Toolchain**: Cross-compiled on Ubuntu runners using `arm-linux-gnueabihf`
- **Source**: Official Taskwarrior releases from [GothenburgBitFactory/taskwarrior](https://github.com/GothenburgBitFactory/taskwarrior)

## Requirements

The pre-built binaries require:
- ARM32 (armv7l) processor
- Linux kernel
- glibc-based system (Debian, Ubuntu, DietPi, etc.)
- Standard system libraries (libuuid, libgnutls, libreadline)

## Troubleshooting

### Library Not Found Errors

If you encounter library errors, ensure all dependencies are installed:

```bash
sudo apt-get update
sudo apt-get install libuuid1 libgnutls30 libreadline8
```

### Permission Denied

Make sure you're using `sudo` when copying files to system directories.

### Version Mismatch

If you need a specific version, use the manual workflow trigger and specify the version number.

## Contributing

This is a build automation repository. If you encounter issues with the builds or want to improve the workflow, please open an issue or submit a pull request.

## License

This repository contains build automation scripts. Taskwarrior itself is released under the MIT license. See the [official Taskwarrior repository](https://github.com/GothenburgBitFactory/taskwarrior) for license details.

## Related Links

- [Taskwarrior Official Repository](https://github.com/GothenburgBitFactory/taskwarrior)
- [Taskwarrior Website](https://taskwarrior.org/)
- [Taskwarrior Documentation](https://taskwarrior.org/docs/)
