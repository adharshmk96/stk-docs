---
sidebar_position: 2
---

# Getting Started

## Installation

### Using `go install`:
    
```bash
go install github.com/adharshmk96/stk@latest
```

If installation fails, check the `GOPATH` and `GOBIN` environment variables. Make sure that `GOBIN` is added to your `PATH`.

```bash
echo export PATH=$PATH:$GOBIN >> ~/.profile && source ~/.profile
```

### Directly download the binary:

Download the binary from the releases page [here](https://github.com/adharshmk96/semver/releases), Extract and move the binary to a directory in your `PATH`

### Check installation:

On successful installation, you should be able to run the following command:

```bash
stk --version
```
