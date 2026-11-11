# git-debian-binary

Builds binary `.deb` packages of upstream Git for Debian 13 on `amd64` and
`arm64`.

## Releases

Run **Build and release Git** from the repository's Actions tab using
**Run workflow**. The workflow finds the latest stable release published by
upstream Git, builds both architecture packages on Debian 13, and publishes
them as assets in a release whose tag and title are the upstream version
without its leading `v` (for example, `2.54.0`). Running it again updates the
assets for that version.

The packages are named `git_<version>_<architecture>.deb`. They use the Debian
package name `git` and a higher package version than Debian 13's stock package,
so installing one upgrades that package and replaces its Git executable and
support files. Debian's `git-man` package and the runtime libraries remain
provided by Debian.

Install the package for the machine's architecture with:

```sh
sudo apt install ./git_<version>_amd64.deb
```

Use the `arm64` package on an ARM64 system. The workflow builds from the
upstream Git release tag; it does not run automatically when upstream publishes
a release.