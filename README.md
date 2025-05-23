# Go Linker Patch For OPSEC

This branch contains Golang linker patches for mangling the pclntab and entirely removing build info from builds.

## Build
```bash 

# Switch to src dir
cd ./src

# Build the compiler (make.bat for windows)
./make.bash

# Replace the linker in your toolchain
cp "../pkg/tool/$(go env GOOS)_$(go env GOARCH)/link $(go env GOTOOLDIR)"
```

## Usage
Patched linker will mangle all pcln data when `MANGLE_PCLN` environment variable is set.

```bash
MANGLE_PCLN=1 go build -o myApp
```
Set `NO_BUILDINFO` variable for removing the entire build info section.

```bash
NO_BUILDINFO=1 go build -o myApp

```
