# Blixel — releases

[Blixel](https://blixel.app) is video chat for Mac. Everyone in a call can share
multiple windows at once, and anyone can hand a spoken or typed request to the
coding agents in the room. Native macOS, built on LiveKit.

Docs: [blixel.app/docs](https://blixel.app/docs)

This repository hosts release artifacts only. Downloads live under
[Releases](../../releases).

Requires Apple silicon and macOS 15 (Sequoia) or later.

## Install

```bash
brew install --cask blixel-app/tap/blixel
```

That adds the tap and installs in one step. If you would rather tap first, these
are equivalent:

```bash
brew tap blixel-app/tap
brew install --cask blixel
```

Either way you get `Blixel.app` and the `blixel` command on your PATH.

To update:

```bash
brew upgrade --cask blixel
```

Or download `Blixel-<version>.dmg` from the [Releases](../../releases) page and
drag `Blixel.app` to `/Applications`.

## Verifying a download

Every release is signed with an Apple Developer ID certificate and notarized by
Apple, so macOS accepts it without any Gatekeeper workaround. To check that for
yourself:

```bash
spctl -a -vvv -t exec /Applications/Blixel.app
```

```
/Applications/Blixel.app: accepted
source=Notarized Developer ID
```

The signing team is what identifies the publisher:

```bash
codesign -dv /Applications/Blixel.app 2>&1 | grep TeamIdentifier
```

```
TeamIdentifier=N79N985D2P
```

Each release also carries a `.sha256` file alongside the disk image:

```bash
shasum -a 256 -c Blixel-<version>.dmg.sha256
```

Homebrew performs this check for you on every install and upgrade.

## Uninstalling

```bash
brew uninstall --cask blixel          # app and CLI
brew uninstall --zap --cask blixel    # also removes settings and logs
```
