# clone

[![Test](https://github.com/maxmouchet/clone/actions/workflows/test.yaml/badge.svg)](https://github.com/maxmouchet/clone/actions/workflows/test.yaml)

[`clone`](/clone) is an extremely simple bash script that does two things:

1) It clones Git repositories in a consistent directory hierarchy.

```bash
clone git@github.com:octocat/Spoon-Knife.git
clone https://git.sr.ht/~sircmpwn/git.sr.ht
tree ~/Clones
# ~/Clones
# ├── git.sr.ht
# │   └── sircmpwn
# │       └── git.sr.ht
# └── github.com
#     └── octocat
#         └── Spoon-Knife
```

2. It adds the cloned repository to [`autojump`](https://github.com/wting/autojump), if installed.
```bash
clone git@github.com:octocat/Spoon-Knife.git
j spoon
# ~/Clones/github.com/octocat/Spoon-Knife
```

## Installation

```bash
curl -Lo ~/.local/bin/clone \
    https://github.com/maxmouchet/clone/releases/latest/download/clone
chmod +x ~/.local/bin/clone
mkdir -p ~/Clones # Or specify another directory, see below.
```

## Usage

```bash
clone [git-clone-options] <repository>
```

By default `clone` uses the `~/Clones` directory. Use the `CLONE_BASE_DIR` environment variable to specify another directory:
```
export CLONE_BASE_DIR=/tmp/clones
clone git@github.com:octocat/Spoon-Knife.git
# Cloning into '/tmp/clones/github.com/octocat/Spoon-Knife'...
```

## Help

If you encounter an error when executing the curl command to install clone, it may be due to `~/.local/bin` not existing on your system or not being included in your PATH. Follow the steps below to resolve these issues:

### Ensuring `~/.local/bin Exists`

If `~/.local/bin` does not exist on your system, create it using:

```bash
mkdir -p ~/.local/bin
```

This directory is used by clone to store executable scripts and should be included in your system's PATH for easy access.

### Adding `~/.local/bin` to Your PATH

To make sure executables in `~/.local/bin` are accessible from any terminal session, you'll need to add this directory to your PATH. You can do this by appending the following line to your shell's configuration file (e.g., ~/.bashrc, ~/.zshrc, etc.):

```bash
export PATH="$HOME/.local/bin:$PATH"
```

After adding the line, reload your shell configuration to apply the changes:

```bash
source ~/.bashrc  # Or the relevant file for your shell, such as .zshrc
```

By following these steps, you should be able to successfully run the curl command to install clone and execute it from any location in your terminal.