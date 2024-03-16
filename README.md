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

## Preparing Your Environment

To check if ~/.local/bin is included in your PATH, run the following command. The absence of output indicates that it is not:

```bash
echo $PATH | grep -o ~/.local/bin
```

If ~/.local/bin does not exist on your system, create it using:

```bash
mkdir -p ~/.local/bin
```

To ensure that executables in ~/.local/bin are accessible from any terminal session, add this directory to your PATH. Do this by adding the following line to your shell's configuration file (e.g., ~/.bashrc, ~/.zshrc, etc.):


```bash
export PATH="$HOME/.local/bin:$PATH"
```

To apply the changes, reload your shell configuration:

```bash
source ~/.bashrc  # Or the relevant file for your shell, such as .zshrc
```

Now, ~/.local/bin is ready for use. You may proceed with the installation instructions.

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