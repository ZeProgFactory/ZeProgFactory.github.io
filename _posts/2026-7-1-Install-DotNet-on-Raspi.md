---
layout: post
title: Install .Net on Raspberry Pi
tags : [.Net, Linux, Bash, RaspberryPi]
---
### A quick, user-level .Net SDK install for Raspberry Pi
Hi folks,  
Here is the recipe I use to install the .Net SDK on Rasperry Pi with Microsoft's official `dotnet-install.sh` script. Everything goes in your home folder (`~/.dotnet`), so you don't need root rights or a package manager. This is handy on Raspberry Pi, or distros without an official package.

## 1. Install .Net

```bash
# Remove any previous user-level install (optional, for a clean start)
rm -rf ~/.dotnet

# Download the official install script
rm -f dotnet-install.sh
wget https://dot.net/v1/dotnet-install.sh
chmod +x dotnet-install.sh

# Use a temp folder in $HOME (/tmp is sometimes too small or mounted noexec)
mkdir -p ~/tmp
TMPDIR=$HOME/tmp ./dotnet-install.sh --version latest
```

By default, `--version latest` installs the most recent SDK from the **LTS** channel. To pick a specific channel instead, use something like:

```bash
TMPDIR=$HOME/tmp ./dotnet-install.sh --channel 9.0
```

## 2. Add .Net to the path

```bash
echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
echo 'export PATH=$PATH:$HOME/.dotnet:$HOME/.dotnet/tools' >> ~/.bashrc
```

- `DOTNET_ROOT` tells apps and tools where the runtime lives.
- `~/.dotnet/tools` makes global tools (`dotnet tool install -g ...`) available.

## 3. Reload the profile

```bash
source ~/.bashrc
```

## 4. Check the installation

```bash
dotnet --info
dotnet --list-sdks
```

If you see your SDK version listed, you're good to go. 🎉

## Notes

- If you use `zsh`, put the `export` lines in `~/.zshrc` instead of `~/.bashrc`.
- Run the same steps again to upgrade: the first `rm -rf ~/.dotnet` gives you a clean install.
- More options: [dotnet-install scripts reference](https://learn.microsoft.com/dotnet/core/tools/dotnet-install-script).
