# dotfiles

Personal macOS dotfiles for Ruby on Rails development, managed with
[chezmoi](https://chezmoi.io). Built for Apple Silicon (M-series).

## What's in here

| Area        | Files |
|-------------|-------|
| Shell       | `dot_zshrc` (+ oh-my-zsh, installed automatically) |
| Prompt      | `dot_config/starship.toml` |
| Git         | `dot_gitconfig`, `dot_config/git/ignore` |
| Editors     | `dot_config/zed/*`, `dot_config/nvim/*` (LazyVim) |
| Terminal    | `dot_config/ghostty/config` |
| Window mgr  | Rectangle (configured in-app) |
| Runtimes    | `dot_config/mise/config.toml` (ruby, python via mise) |
| Packages    | `Brewfile` |

The `run_*` scripts are executed by chezmoi during `apply`:

1. `run_once_before_00-install-homebrew` — installs Homebrew if missing
2. `run_onchange_after_10-brew-bundle` — `brew bundle` from the `Brewfile`
3. `run_once_after_20-oh-my-zsh` — installs oh-my-zsh (non-destructive)
4. `run_onchange_after_30-mise-install` — `mise install` global runtimes

## Bootstrapping a brand-new Mac

> ⚠️ Run everything below as your **normal user** — never with `sudo`.
> Homebrew refuses to install as root. Your account must be an **administrator**
> (Homebrew needs sudo to create `/opt/homebrew`).

```sh
# 1. Xcode Command Line Tools (git, compilers). Wait for the GUI installer to finish.
xcode-select --install

# 2. Cache sudo credentials (enter your password once). Also confirms you're an admin.
sudo -v

# 3. Install chezmoi, pull this repo, and apply everything in one command.
#    This installs Homebrew, all Brewfile packages, oh-my-zsh, runtimes, and
#    drops every dotfile into place.
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply virolea

# 4. Restart the shell (or open a new terminal tab).
exec zsh
```

> The `init --apply virolea` form resolves to `github.com/virolea/dotfiles`.
> If the repo is private, authenticate first (`gh auth login`) or use the SSH/HTTPS URL.

### Post-install (manual, not in dotfiles)

These hold secrets or are account-specific and are intentionally **not** tracked:

- SSH keys (`~/.ssh`) and GnuPG keys (`~/.gnupg`)
- `gh auth login`
- `~/.npmrc` / `~/.yarnrc.yml` — private registry tokens (per project/job)
- Start Postgres: `brew services start postgresql@18`
- Sign in to 1Password CLI: `op signin`

App permissions / setup that macOS won't let a script do (TCC-protected):

- **Raycast**: launch it, grant Accessibility, set its hotkey to `⌘Space`, then
  disable the Spotlight shortcut (System Settings → Keyboard → Keyboard Shortcuts
  → Spotlight) so Raycast takes over.
- **Rectangle**: launch it and grant Accessibility.
- **OrbStack**: launch once to start its Docker engine; it replaces Docker Desktop.
- **Slack**: sign in.

macOS system tweaks (applied automatically by `run_onchange_after_40-macos-defaults`):

- Caps Lock → Escape (persists via `~/Library/LaunchAgents/com.local.caps-to-esc.plist`)
- Two-finger tap = right click

  A logout/login may be needed for the trackpad change to fully register.

## Day-to-day

```sh
chezmoi edit ~/.zshrc      # edit a tracked file
chezmoi apply              # apply pending changes to $HOME
chezmoi cd                 # jump into the source repo to commit/push
chezmoi update             # pull latest from GitHub and apply
chezmoi add ~/.somefile    # start tracking a new file
```
