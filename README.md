# mac-cleanup
in the name Interactive macOS system cleanup tool
[README.md](https://github.com/user-attachments/files/24376694/README.md)
# mac-cleanup

Interactive macOS system cleanup tool. Scans your system, shows what's recoverable, and lets you choose what to clean.

## Install

### Homebrew (recommended)
```bash
brew tap YOUR_USERNAME/mac-cleanup
brew install mac-cleanup
```

### Manual
```bash
curl -o mac-cleanup https://raw.githubusercontent.com/YOUR_USERNAME/mac-cleanup/main/mac-cleanup
chmod +x mac-cleanup
sudo mv mac-cleanup /usr/local/bin/
```

## Usage

```bash
mac-cleanup              # Interactive mode (prompts for each category)
mac-cleanup -y           # Auto-approve all cleanups
mac-cleanup -n           # Dry-run (preview without cleaning)
mac-cleanup -d           # Diagnostic health report only
mac-cleanup -h           # Help
```

## What it cleans

| Category | Location | Requires sudo |
|----------|----------|---------------|
| Trash | `~/.Trash` | No |
| User Caches | `~/Library/Caches` | No |
| Homebrew | Old versions + cache | No |
| npm cache | `~/.npm` | No |
| Yarn cache | `~/.yarn/cache` | No |
| Xcode DerivedData | `~/Library/Developer/Xcode/DerivedData` | No |
| iOS Simulators | Unavailable simulators | No |
| Old Downloads | Files >30 days in `~/Downloads` | No |
| Docker | Dangling images, stopped containers | No |
| DNS Cache | System DNS cache | Yes |
| System Maintenance | Daily/weekly/monthly scripts | Yes |

## Example

```
$ mac-cleanup

mac-cleanup v1.0.0

Scanning system...

=== Storage ===
  Trash:               4.2 GB (847 items)
  Clean Trash? [y/N]: y
  ✓ Cleared 4.2 GB

  User Caches:         8.1 GB
  Clean User Caches? [y/N]: n
  ⊘ Skipped

  Brew Cache:          3.4 GB (12 old versions)
  Clean Brew Cache? [y/N]: y
  ✓ Cleaned brew cache

=== Summary ===
  Recovered:  7.6 GB
  Skipped:    8.1 GB

Done!
```

## Requirements

- macOS 10.15+
- zsh (default on modern macOS)

## License

MIT
