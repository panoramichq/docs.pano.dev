---
description: Installation details for the Pano CLI
---

# Installation

We recommend using one of our OS-specific guides for help with installing the Panoramic CLI. If your OS is not listed, or you prefer to use`pip`, please see the instructions below.

## OS-Specific Guides

* [macOS](installation.md#macos-installation)
* [Windows](installation.md#windows-installation)

## Install with PIP

The Panoramic CLI is a Python module distributed on [PyPI](https://pypi.org/project/panoramic-cli/), and can be installed using PIP. We recommend using virtual environments when installing tools like the Panoramic CLI.

### Installation

`pip install panoramic-cli`

### Upgrading

`pip install --upgrade panoramic-cli`

## macOS Installation

### Homebrew

#### Installation

The preferred method of installing the Panoramic CLI on macOS is via [Homebrew](https://brew.sh/). Install Homebrew, then run the following:

`brew update  
brew tap panoramichq/brew  
brew install panoramic-cli`

#### Upgrading

To upgrade via Homebrew, use:

`brew update  
brew upgrade panoramic-cli`

## Windows Installation

Before starting, you will need to install [Python 3.6 or higher for Windows](https://www.python.org/downloads/windows/).

Open a Windows shell **as an administrator** and install Panoramic CLI with`pip`:

`pip install panoramic-cli`

To upgrade, use:

`pip install --upgrade panoramic-cli`

