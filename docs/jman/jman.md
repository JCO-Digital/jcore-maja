# jman CLI — Setup and Usage

This guide covers installation, setup, and day-to-day usage of the **`jman` CLI tool**.

> Scope: This document only covers the main CLI tool (`jman`).
> It does **not** cover `jman-api` or `jman-monitor`.

Latest binaries are available here:
https://github.com/JCO-Digital/jman/releases/latest

---

## 1) Install

### Option A: Download a prebuilt binary (recommended)

1. Open the latest release page:
   https://github.com/JCO-Digital/jman/releases/latest
2. Download the executable for your OS/architecture.
3. Extract it.
4. Move the `jman` binary to a directory in your `PATH` (for example `~/.local/bin` or `/usr/local/bin` if you want it system wide).

Example (Linux/macOS):

```bash
chmod +x jman
mv jman ~/.local/bin/jman
```

Option B: Build from source

If you prefer building locally, clone the repository and build with the project’s standard build process, then place the resulting `jman` binary in your `PATH`.

---

## 2) Verify installation

Run:

```
jman --version
jman --help
```

If both commands work, the CLI is installed correctly.

---

## 3) Configuration

`jman` may be configured through:

- command-line flags
- environment variables
- config file

The config file is located in XDG config directory (e.g., `~/.config/jman/config.toml` on Linux) and can be used to set defaults for flags and other settings.

```toml
tokenSpinup = "ffe3d......."
cvssThreshold = 7
vulnThreshold = 7
ignoreSites = [
        "example.com",
        "testing.example.com",
        ]
```

The one setting you have to set is `tokenSpinup`, which should be a read only API token for the SpinupWP API. You may find it in BitWarden.

The other settings are mainly for vulnerability reports, which are not the main focus of this document.

---

## 4) Basic command structure

Most usage follows this pattern:

```bash
jman <subcommand> <target> [args] [flags]
```

### Subcommands

Subcommands can be found by running:

```bash
jman --help
```

### Target

The target is a search string to match what you are operation on. It can be a server or a site or something else depending on the subcommand. The target is used to find the correct item to operate on. Not all commands require a target.

## Arguments

Arguments are additional parameters that some commands require. They wary a lot depending on the command.

---

## 5) Common usage workflow

### Fetch data

The first command you should run is `jman fetch`. It fetches and caches the data from SpinupWP to have all the site and server information on which the other commands are based.

The fetch command can get 4 types of data:

1. Servers - Information about the servers in SpinupWP. Target: servers, all or basic
2. Sites - Information about the sites in SpinupWP. Target: sites, all or basic
3. Plugins - Fetches the installed plugins from all sites. This requires SSH access to the sites, so this is probably not useful unless you have access to all the sites. Target: plugins or all
4. Vulnerabilities - Fetches the vulnerabilities for all the plugins. This is based on the plugin information, so you need to fetch plugins first. Target: vulnerabilities or all

For most uses, you only need to fetch the `basic` target, which is the default.

### Plugin management

The `jman plugin` subcommand is one of the more useful ones for everyday use. It can be used to list, install, update and remove plugins.

---

## 6) Troubleshooting

### Command not found

- Ensure `jman` is in your `PATH`
- Re-open terminal or reload shell config
- Verify with `which jman` (Linux/macOS) or `where jman` (Windows)

### Permission denied

- Make the binary executable (`chmod +x jman`)
- Verify directory execute permissions

### Unexpected behavior

- Confirm version: `jman --version`
- Re-check flags with `--help`
- Use verbose/debug mode if available

---

## 7) Upgrading

The recommended way to upgrade your version of jman is to run `jman update`. This should self update if there is a new version available. If for some reason that does not work, you can manually update by following these steps:

1. Download the newest binary from
   https://github.com/JCO-Digital/jman/releases/latest
2. Replace the existing `jman` binary
3. Verify with `jman --version`
