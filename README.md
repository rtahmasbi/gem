# GEM
golang, bazel, gazelle

## git
```
git clone https://github.com/rtahmasbi/gem.git
```

## Installation

### Linux

**Go**
```bash
wget https://go.dev/dl/go1.25.0.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.25.0.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
```

> Check https://go.dev/dl/ for the latest version and update the filename accordingly.

**Bazel (via Bazelisk)**
```bash
sudo curl -Lo /usr/local/bin/bazel https://github.com/bazelbuild/bazelisk/releases/latest/download/bazelisk-linux-amd64
sudo chmod +x /usr/local/bin/bazel
```

### macOS

**Go + Bazel (via Homebrew)**
```bash
# Install Homebrew if not present
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install go
brew install bazelisk
```

### Verify

```bash
go version
bazel version
```
