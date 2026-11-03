# Homebrew tap for Vogter

[Vogter](https://github.com/schlunsen/vogter) watches your Mac for malware, keyloggers and
spying. This tap holds:

- `Formula/vogter.rb`: the `vogter` CLI and the `vogterd` service, built from source.
- `Casks/vogter.rb`: the `Vogter.app` menu bar app (Apple silicon, macOS 14+).

## Install

```sh
brew install schlunsen/vogter/vogter          # CLI + service
brew services start vogter                    # run vogterd as your user, at login
brew install --cask schlunsen/vogter/vogter   # menu bar app (also pulls in the formula)
```

Or tap once and use short names:

```sh
brew tap schlunsen/vogter
brew install vogter
brew install --cask vogter
```

Then give `$(brew --prefix)/opt/vogter/bin/vogterd` **Full Disk Access** (System Settings >
Privacy & Security) so it can read the privacy-permission databases.

The app is ad-hoc signed and **not notarized** yet, so Gatekeeper blocks the first launch.
Allow it under System Settings > Privacy & Security > "Open Anyway", or, if you trust the
download, run `xattr -dr com.apple.quarantine /Applications/Vogter.app`.

`brew services` runs the service as your user. To see every process and use Endpoint Security,
run it as a root LaunchDaemon instead with `scripts/install-daemon.sh` from the main repository.

## Maintainers

See [docs/homebrew.md](https://github.com/schlunsen/vogter/blob/main/docs/homebrew.md) in the
main repository for how to cut a release and bump this tap.
