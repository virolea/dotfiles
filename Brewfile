# Brewfile — managed by `brew bundle`
# Run on a new machine with: brew bundle --file=Brewfile
# Trim anything you no longer need before bootstrapping the new Mac.

# ---------------------------------------------------------------------------
# Core CLI / dev tooling
# ---------------------------------------------------------------------------
brew "git"
brew "gh"                    # GitHub CLI
brew "mise"                  # runtime version manager (ruby, node, python...)
brew "starship"              # shell prompt
brew "neovim"
brew "coreutils"
brew "curl"
brew "wget"
brew "jq"
brew "ripgrep"
brew "bat"
brew "htop"
brew "gum"                   # shell-script UI helpers
brew "cmake"
brew "libffi"

# ---------------------------------------------------------------------------
# Git workflow
# ---------------------------------------------------------------------------
brew "lazygit"
brew "difftastic"           # used by .gitconfig (diff.external = difft)
brew "gitleaks"             # secret scanning

# ---------------------------------------------------------------------------
# Ruby on Rails essentials
# ---------------------------------------------------------------------------
brew "postgresql@18"        # Postgres server + client (brew services start postgresql@18)
brew "libpq"                # Postgres client libs (pg gem)
brew "valkey"               # Redis-compatible store (cache / Sidekiq)
brew "overmind"             # Procfile process manager
brew "hivemind"             # lighter Procfile runner
brew "ruby-build"           # ruby build definitions (used by mise)

# ---------------------------------------------------------------------------
# Image / media processing (Active Storage variants)
# ---------------------------------------------------------------------------
brew "vips"                 # libvips — Rails 7+ default image processor
brew "imagemagick"          # ImageMagick — if a project still needs MiniMagick
brew "ffmpeg"               # video/audio (Active Storage previews)

# ---------------------------------------------------------------------------
# JS / Node (Node itself comes from mise)
# ---------------------------------------------------------------------------
brew "pnpm"

# ---------------------------------------------------------------------------
# Deploy / cloud / services (review — some are job-specific)
# ---------------------------------------------------------------------------
# brew "flyctl"               # Fly.io
# brew "heroku/brew/heroku" # uncomment if you still deploy to Heroku
# brew "awscli"             # AWS
# brew "stripe/stripe-cli/stripe"

# ---------------------------------------------------------------------------
# Casks — apps & fonts
# ---------------------------------------------------------------------------
cask "ghostty"              # terminal
cask "zed"                  # editor (dot_config/zed/*)
cask "raycast"              # Spotlight replacement / launcher
cask "rectangle"            # window management (keyboard shortcuts)
cask "orbstack"             # Docker / Linux VMs (Docker Desktop replacement)
cask "slack"
cask "font-iosevka"
cask "1password-cli"
cask "ngrok"
cask "chromedriver"
