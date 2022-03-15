<p align="center">
  <img alt="GoReleaser Logo" src="https://storage.googleapis.com/trufflehog-static-sources/pixel_pig.png" height="140" />
  <h2 align="center">TruffleHog</h2>
  <p align="center">Find leaked credentials.</p>
</p>

---


[![CI Status](https://github.com/trufflesecurity/trufflehog2/workflows/release/badge.svg)](https://github.com/trufflesecurity/trufflehog2/actions)
[![Go Report Card](https://goreportcard.com/badge/github.com/trufflesecurity/trufflehog2)](https://goreportcard.com/report/github.com/trufflesecurity/trufflehog2)
[![Docker Hub Build Status](https://img.shields.io/docker/cloud/build/trufflesecurity/trufflehog2.svg)](https://hub.docker.com/r/trufflesecurity/trufflehog2/)
![GitHub](https://img.shields.io/github/license/trufflesecurity/trufflehog2)

---

## Join The Slack
Have questions? Feedback? Jump in slack and hang out with us

https://join.slack.com/t/trufflehog-community/shared_invite/zt-pw2qbi43-Aa86hkiimstfdKH9UCpPzQ


## Demo

![Stargazers over time](https://storage.googleapis.com/truffle-demos/non-interactive.svg)

## Installation

Several options:

### 1. Go
`go install github.com/trufflesecurity/trufflehog2.git@latest`

### 2. [Release binaries](https://github.com/trufflesecurity/trufflehog2/releases)

### 3. Docker


> Note: Apple M1 hardware users should run with `docker run --platform linux/arm64` for better performance.

#### **Most users**

```bash
docker run -it -v "$PWD:/pwd" ghcr.io/trufflesecurity/trufflehog2:latest github --repo https://github.com/trufflesecurity/test_keys --debug 
```

#### **Apple M1 users**

The `linux/arm64` image is better to run on the M1 than the amd64 image.
Even better is running the native darwin binary avilable, but there is not container image for that.

```bash
docker run --platform linux/arm64 -it -v "$PWD:/pwd" ghcr.io/trufflesecurity/trufflehog2:latest github --repo https://github.com/trufflesecurity/test_keys 
```

### 4. Pip (help wanted)

It's possible to distribute binaries in pip wheels.

Here is an example of a [project that does it](https://github.com/Yelp/dumb-init).

Help with setting up this packaging would be appreciated!

### 5. Brew (help wanted)

We'd love to distribute via brew and could use your help.

## Usage

TruffleHog has a sub-command for each source of data that you may want to scan:

- git
- github
- gitlab
- S3
- filesystem
- file and stdin

Each subcommand can have options that you can see with the `-h` flag provided to the sub command:

```
$ trufflehog git --help
usage: TruffleHog git [<flags>] <uri>

Find credentials in git repositories.

Flags:
      --help           Show context-sensitive help (also try --help-long and --help-man).
      --debug          Run in debug mode
      --json           Output in JSON format.
      --concurrency=8  Number of concurrent workers.
      --verification   Verify the results.
  -i, --include_paths=INCLUDE_PATHS  
                       Path to file with newline separated regexes for files to include in scan.
  -x, --exclude_paths=EXCLUDE_PATHS  
                       Path to file with newline separated regexes for files to exclude in scan.
      --branch=BRANCH  Branch to scan.
      --allow          No-op flag for backwards compat.
      --entropy        No-op flag for backwards compat.
      --regex          No-op flag for backwards compat.

Args:
  <uri>  Git repository URL. https:// or file:// schema expected.
```

For example, to scan a  `git` repository, start with

```
$ trufflehog git https://github.com/trufflesecurity/trufflehog2.git
```

## Contributors

This project exists thanks to all the people who contribute. [[Contribute](CONTRIBUTING.md)].


<a href="https://github.com/trufflesecurity/trufflehog/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=trufflesecurity/trufflehog" />
</a>


## Stargazers over time

[![Stargazers over time](https://starchart.cc/trufflesecurity/trufflehog.svg#cache-bust)](https://starchart.cc/trufflesecurity/trufflehog)

## License Change

Since v3.0, TruffleHog is released under a AGPL 3 license, included in [`LICENSE`](LICENSE). TruffleHog v3.0 uses none of the previous codebase, but care was taken to preserve backwards compatibility on the command line interface. The work previous to this release is still available licensed under GPL 2.0 in the history of this repository and the previous package releases and tags. A completed CLA is required for us to accept contributions going forward.
