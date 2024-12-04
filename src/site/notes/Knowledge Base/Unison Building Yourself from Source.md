---
{"dg-publish":true,"permalink":"/knowledge-base/unison-building-yourself-from-source/","dgPassFrontmatter":true}
---

Some OSs come with it, some don’t, and they all have different versions that hate each other, and they never include unison-fsmonitor which is required for using the watch feature.

So you can compile it yourself!

Find the latest Production release at https://github.com/bcpierce00/unison/releases

**Note that as of Unison version 2.52.0, OCaml version mismatches are tolerated better!**

# Build It
I am avoiding use of included OS pieces, like OCaml, so that this will work on any system.
Note that once you have a binary for your hardware and architecture, you can just copy it to other devices you own of the same architecture and OS.

This build process works on even a Raspberry Pi

### Install OPAM
https://opam.ocaml.org/doc/Install.html
This is required for getting the latest version of OCaml later.

```
sudo apt install git bubblewrap unzip make gcc
cd
mkdir bin
sh <(curl -sL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh)
```
Tell it to install in the bin folder that you just made.


### Install OCaml 4.14.2
or the latest version of OCaml 4 if there have been bug fixes.
https://ocaml.org/docs/install.html#OPAM
https://ocaml.org/changelog?t=ocaml

NOTE that at the moment Unison works with OCAML >= 4.08,
and OCaml 5.0.0 has been released, but I see no reason to use OCaml 5 **yet**, because:
1. Even the OCaml Readme says 5.0.0 is possibly less than stable.
2. OCaml 5.0 has dropped native support for 32bit architectures, meaning extra steps/differences for 32bit Raspbery Pi setup.
3. As far as I am aware, while Unison will compile with OCaml 5, it has not been designed to take advantage of any of the new OCaml 5 features yet.
**Fortunately, unlike in the past, Unison's current version will talk to each other, even if they are not all built with the same version of OCaml, so you can mix and match if you want to.**

**OCaml Releases**:
https://ocaml.org/releases/

#### Initialize Opam
NOTE: Using `--bare` to prevent it from automatically installing a version. It often attempts to install the latest 5.x version which is slow to build and often fails on environments such as the Raspberry Pi, and we don't need it as we will be installing our own later.

```
$HOME/bin/opam init --bare
```
 - "5" No, I'll remember to run ... when I need opam
 - "n" don't add a hook
```
eval $($HOME/bin/opam env)
```

#### Install wanted version of OCAML

```
$HOME/bin/opam switch create 4.14.2
eval $($HOME/bin/opam env)
```

NOTE: If this complains that the requested version already exists (the create fails) then just switch to it instead of installing it with the command `$HOME/bin/opam switch 4.14.2`

FURTHER: If you get in a pickle where your version is "installed" but broken, you can remove it by running: `$HOME/bin/opam switch remove 4.14.2` and then start over.

#### Check that you got what you want

```
which ocaml
ocaml -version
```

### Get Unison Source Code
https://github.com/bcpierce00/unison/

 - Either by copying down the latest release bundle
```
cd
wget https://github.com/bcpierce00/unison/archive/refs/tags/v2.53.7.tar.gz
tar xvf v2.53.7.tar.gz
rm v2.53.7.tar.gz
cd unison-2.53.7/
```

- **Or** by cloning the Unison source directly, and optionally checking out the last "release" tag.
```
git clone https://github.com/bcpierce00/unison.git
cd unison
git checkout v2.53.7
```
- **Or** if you are crazy/catching a bugfix, just leave it at the root of `master`

### Make sure `ocaml` is available
```
eval $($HOME/bin/opam env)
which ocaml
ocaml -version
```

### Then follow the unison build process

```
make tui
make fsmonitor # If you need it
./src/unison -version
```

 - **IF** you get an error saying `ocamlopt: No such file or directory` it may be that OCaml "native" does not support your hardware, in which case you will need to edit `src/Makefile` and find the line "NATIVE=true" and change it to "NATIVE=false" and try again.
     - I expect this to eventually happen when building on Raspberry Pi 32bit with OCaml 5, but for now I'm using OCaml 4, so this should not be an issue.

Then move the binaries to someplace in your path.

`cp src/unison src/unison-fsmonitor $HOME/bin`

#KnowledgeBase #Linux 