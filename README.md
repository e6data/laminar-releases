# Laminar

Laminar is a unified engine for SQL queries, Python notebooks, streaming, and data
workloads. The package includes the web UI, a Python notebook runtime, and the ICU
time-zone extension. It runs locally without Docker, Node.js, or a separate
Python installation.

## Install

Requires an Apple Silicon Mac with macOS 14 or later and [Homebrew](https://brew.sh).

```sh
brew tap e6data/tap https://github.com/e6data/laminar-releases.git
brew install e6data/tap/laminar
laminar
```

Open <http://127.0.0.1:15003/> after the engine reports that it is ready.
Keep the terminal open. Press Ctrl+C to stop the engine.

This repository is the Homebrew tap and download location. It contains release
packages and the formula. It does not contain the engine source code.

## Configuration and data

The first launch creates:

```text
~/Library/Application Support/Laminar/config.toml
~/Library/Application Support/Laminar/data/
```

Use Settings in the UI to edit configuration. Restart the engine when a setting
requires it. The package includes a Python runtime for notebooks. Playground and
external integrations can be enabled and configured in Settings. An assistant
provider needs its own credentials.

To use another local data directory:

```sh
LAMINAR_HOME="$HOME/my-laminar" laminar
```

To use an existing server configuration:

```sh
laminar --config /absolute/path/config.toml --allow-config-edit
```

An explicit config keeps its configured paths. It does not use `LAMINAR_HOME`.
Do not start two engines with the same data directory.

## Upgrade

```sh
brew update
brew upgrade e6data/tap/laminar
```

Stop and restart the engine to use the new version. Upgrades keep the config and
data directory. Back up that directory, including `data/secrets.key`, to preserve
your workspace and encrypted secrets.

`brew uninstall laminar` removes the installed package. It keeps your data.

## Direct download

Download the Apple Silicon ZIP and `SHA256SUMS` from
[Releases](https://github.com/e6data/laminar-releases/releases).
Check the checksum, extract the ZIP, and run `laminar/bin/laminar`. Keep the full
extracted folder together; the executable uses the Python and ICU files beside
it. Homebrew is the supported installation path for this release.

The command-line package does not require an Apple Developer account. This is a
custom Homebrew formula, not a notarized desktop app.

## Help

```sh
laminar --help
laminar --version
```

The package contains third-party license notices under `share/laminar/licenses`.
