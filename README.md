# Kicad Diff

This repo is a copy of LeoHeck's kdiff tool with a a couple more quality of life features. It is also to be a platform to be primarily Windows tested and validated with support for both Linux and MacOS systems as well.

## How it works

The kdiff command uses SVG's to compile differences using the [Kicad-Diff](https://github.com/Gasman2014/KiCad-Diff)  and  [Plotgitsh](https://github.com/jnavila/plotkicadsch) commands. 

## Installation for Windows

Configure WSL
(https://www.tenforums.com/tutorials/46769-enable-disable-windows-subsystem-linux-wsl-windows-10-a.html)

Install Ubuntu either through [webstore](https://www.microsoft.com/en-ca/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab)) or any other option (working on Ubuntu 20.04)

Continue to Linux installation

## Installing on Linux

```
# Basic dependencies
sudo apt install -y libgmp-dev
sudo apt install -y pkg-config
sudo apt install -y opam
sudo apt install -y python3-pip
sudo apt install -y python3-tk

# Initialize opam
opam init --disable-sandboxing
opam switch create 4.09.1
opam switch 4.09.1
eval $(opam env)

# Install custom plotgitsch
git clone https://github.com/leoheck/plotkicadsch.git
cd plotkicadsch
./install.sh

# Kicad-Diff dependencies
pip3 install pygubu
pip3 install python_dateutil

# Install Kicad-Diff
git clone https://github.com/Gasman2014/KiCad-Diff.git
```

## Installing dependencies on OSX

Install dependencies from "Installing dependencies on Linux" section and then

```
brew install gsed
brew install findutils
```

## Environment Setup (before using it)
```
# Load KiCad-Diff environment
cd KiCad-Diff
source ./env.sh

# Install kdiff environment
git clone https://github.com/leoheck/kdiff
cd kdiff

# Load kdiff environment
source ./env.sh
```

## Using
```
cd [kicad_git_repo]
kdiff board.kicad_pcb
```

## Command line flags (Help)

How to access tool help, this may change, so prefer to use `kdiff -h` instead.

```
USAGE :

    kdiff [OPTIONS] KICAD_PCB

OPTIONS:

    -a          Track all commits (slower).
    -o HASH     Show commits starting from this one.
    -n HASH     Show commits until this one delimited by this one.
    -r          Remove kidiff folder before run
    -l          Do not launch browser at the end
    -p PORT     Set webserver port
    -V          Verbose
    -h          This help

EXAMPLES:

    # Kicad project on the root of the repo
    kdiff board.kicad_pcb

    # Nested Kicad projects
    kdiff nested-project/board.kicad_pcb -r -V
```

Credit goes to: @leoheck, @jnavila and @Gasman2014 for the underlying structure
Special thanks to: @leoheck for building the basis for the support of kdiff
