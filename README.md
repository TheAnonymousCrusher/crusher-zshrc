# Dotfiles README

🌌 **Custom Zsh Configuration by TheAnonymousCrusher** – This repository contains a highly customized `.zshrc` file designed to supercharge your Zsh shell experience. Inspired by Kali Linux aesthetics, it integrates Oh My Zsh, Powerlevel10k, and a suite of plugins, aliases, functions, and utilities for efficient system management, media handling, development workflows, and hardware monitoring. Whether you're a developer, sysadmin, or power user, this setup aims to make your terminal faster, more intuitive, and visually appealing.

![Terminal Screenshot](https://via.placeholder.com/800x400?text=Custom+Zsh+Prompt+Example) <!-- Replace with an actual screenshot of the prompt in action for better visualization -->

## Overview

This dotfiles repo focuses primarily on the `.zshrc` configuration, but it can be extended to include other dotfiles like `.vimrc`, `.tmux.conf`, or window manager configs. The core is a feature-rich Zsh setup that emphasizes:

- Productivity shortcuts for navigation, file management, and system tasks.
- Custom functions for hardware monitoring (battery, temp, CPU/memory), network diagnostics, media downloads/conversions, and secure note-taking.
- Safety features like a trash system instead of direct `rm` for safer deletions.
- Aesthetic enhancements with colorized outputs, icons (via Nerd Fonts), and motivational startup messages.
- Integration with modern tools like fzf for fuzzy searching, eza for enhanced `ls`, and yt-dlp for YouTube handling.

The configuration is modular, with sections for environment setup, aliases, functions, and startup routines. It's optimized for Arch Linux but adaptable to other distros with minor tweaks.

## Features In-Depth

Here's a breakdown of the key features, grouped by category:

### Shell Environment & Prompt
- **Powerlevel10k Integration**: Enables instant prompt loading and customizable segments. Run `p10k configure` after setup for personalization.
- **Custom Kali-Style Prompt**:
  - Displays full directory path.
  - Differentiates user/root with colors (cyan/blue for user, blue/red for root).
  - Shows command execution time and success/fail icons (✔/✖) on the right prompt.
  - Plays a "bruh" sound (via mpv) on command failure for auditory feedback.
- **History Options**: Ignores duplicates, shares history across sessions, and appends with timestamps for better recall.
- **Sudo Prompt**: Customized with yellow color for visibility.
- **Path Extensions**: Adds `$HOME/bin` to PATH for custom scripts.

### Plugins
Loaded via Oh My Zsh:
- `git`: Git command completions and aliases.
- `zsh-autosuggestions`: Suggests commands as you type based on history.
- `zsh-syntax-highlighting`: Colors commands for validity (green for valid, red for invalid).
- `z`: Jump to frequently visited directories (frecency-based).
- `sudo`: Double-tap Esc to prepend `sudo` to the current command.
- `history-substring-search`: Up/down arrow searches history substrings.

### Color Variables
Defines ANSI escape codes for regular, bright, and bold colors (e.g., `$GREEN`, `$BOLD_RED`). Used throughout for consistent, themed outputs.

### Aliases & Shortcuts
- **System Info**:
  - `space`: Human-readable disk usage for filesystems and /dev.
  - `weather`: Fetches weather via `curl wttr.in`.
  - `bro`: Echoes a motivational meme ("💀 just run it, bro.").
  - `getout`: Terminates the session via loginctl.
- **Navigation & Listing**:
  - `ls/la/ll/lt/lta`: Enhanced with eza (icons, tree view, git status). Shows "(empty)" for empty dirs.
  - `../.../....`: Quick cd up levels.
  - `zconf`: cd to `~/.config` and list with icons.
  - `ff`: fzf with bat preview for file fuzzy find.
  - `zz`: fzf over directory stack for jumping.
  - `hs`: fzf over command history.
  - `j`: Alias to `zz` for quick dir jumps.
- **Cleanup & Maintenance**:
  - `cls`: Clear screen with lolcat message.
  - `clean-cache`: Sudo rm `~/.cache/*`.
  - `clean-pacman`: Removes package cache and orphans.
  - `grub-update`: Regenerates GRUB config.
- **Date & Open**:
  - `datetime`: Colored, formatted date/time.
  - `open`: Opens files in default app (xdg-open).
- **Git Shortcuts**:
  - `gi`: git.
  - `gst`: status.
  - `gco`: checkout.
  - `gp`: push.
  - `gl`: Oneline graph log.
  - `gcm/gcam/gcad`: Commit variations.
- **Dev & System Tools**:
  - `src`: Reload `.zshrc`.
  - `psx`: ps aux with fzf to kill processes.
  - `d`: docker.
  - `r`: rails.
  - `n/nano`: nvim (opens dir if no args).
  - `update-all`: Updates pacman, yay, flatpak, pip.
  - `please`: Sudo the last command.
  - `zzz`: Locks session.
- **Package Management (Pacman/Yay/Pikaur)**:
  - Pacman: `in` (install), `del` (remove), `up` (upgrade), `srch` (search), etc.
  - Yay: `yin` (install), `yup` (upgrade), etc., with noconfirm.
  - Pikaur equivalents for alternative AUR helper.
- **Gamma, Brightness, Volume**:
  - `g1` to `g15`: Sets xgamma (0.1 to 1.5) with warnings for extremes.
  - `b<1-100>`: Sets brightness % with icons (brightnessctl fallback to xbacklight).
  - `v<0-100>`: Sets volume % with icons (pactl fallback to amixer).
- **Extras**:
  - Game/Apps: `vba` (VisualBoy Advance), `vsc` (VS Code OSS), `cm` (Chromium on X11).
  - AI/Chat: `gpt` (tgpt with pollinations provider).
  - Monitoring: `mon` (cpu + mem + temp).
  - Anime: `yth` (yt-dlp-hianime).
  - Sounds: `wakeup`, `gambare`, `idwin`, `augh`, `bruh` (mpv clips).

### Functions In-Depth
- **File/Dir Management**:
  - `mkcd`: Creates dir and cds into it.
  - `zd`: Smart cd (home if no arg, fallback to z).
  - `backup`: Creates .bak copy.
  - `extract`: Handles tar, zip, rar, 7z, etc., with success messages.
  - `biggest`: Top 10 largest files/dirs via du.
  - `cmx`: Makes file executable.
  - `rn`: Renames file/dir with feedback.
  - `longrun`: Runs command and notifies on success/fail (libnotify).
  - Safer Delete: `rm/rmf` (trash), `rmp` (permanent), `trash` (list trash).
- **Network & Devices**:
  - `netstat`: Detailed network info (interface, SSID, IPs, gateway, DNS).
  - `speedtest`: Curl-based speed test with parsed output.
  - `lsdevices`: Lists storage, USB, network, bluetooth, displays, batteries with icons.
- **Media & Downloads**:
  - `pahe`: AnimePahe downloader to ~/Videos/Anime.
  - `install-font`: Installs fonts to ~/.local/share/fonts and rebuilds cache.
  - `batchconvert`: Converts videos/images in batch (ffmpeg/imagemagick), supports extensive extensions.
  - `yt`: yt-dlp wrapper to ~/Videos/Youtube. Flags: -a (audio mp3), -h (high-quality 4K), -i (playlist ignore errors).
- **Notes**:
  - `note`: Appends colored timestamped note to ~/notes.txt.
  - `notes`: Views reversed with bat paging.
  - `secnote/snotes`: GPG-encrypted notes with password prompt.
- **System Fixes**:
  - `fix-audio`: Restarts PipeWire/Pulse/WirePlumber/ALSA.
  - `fix-net`: Restarts NetworkManager/ConnMan.
  - `fix-blue`: Restarts BlueZ, unblocks rfkill.
  - `fix-font`: Rebuilds font cache with count diff.
- **Hardware Monitoring**:
  - `batt`: Lists batteries/devices with % icons, status, names.
  - `p`: Switches power profiles (perf/bal/save).
  - `temp/temp-all`: CPU temp (main/all cores) with icons.
  - `mem`: Memory usage with icon and free avail.
  - `cpu`: CPU % usage with icon.
- **Theming & Extras**:
  - `greet`: Random motivational message.
  - `fetch`: Fastfetch with kitty image (cycles images if configured).
  - `banner/logo`: Figlet/toilet username with lolcat.
  - `term-colors`: Terminal color palette.
  - `membar`: Visual memory bar with dots.
- **Startup**: Runs `fetch` (system info + image), optional `greet`, `banner`, `logo`.

## Prerequisites

For optimal functionality:

1. **Oh My Zsh**: Install as above.
2. **Powerlevel10k**: Clone and set theme.
3. **Nerd Fonts**: Essential for icons. Download from nerdfonts.com or via package (e.g., `ttf-firacode-nerd`).
4. **Plugins**: Included in OMZ.
5. **Dependencies**: See list in original quickstart. Key ones: eza, fzf, bat, neofetch, lolcat, upower, sensors, brightnessctl, curl, yt-dlp, ffmpeg, imagemagick, notify-send, nmcli, 7z, unrar, fontconfig, pipewire, bluez, yay, flatpak, pip, nvim, docker, kitty, mpv, etc.

## All-in-One Install Command (Arch/Yay)

```bash
yay -S --needed --noconfirm oh-my-zsh powerlevel10k eza fzf bat neofetch figlet toilet lolcat upower lm-sensors brightnessctl xorg-xgamma power-profiles-daemon curl yt-dlp ffmpeg imagemagick libnotify-bin iw networkmanager p7zip unrar unzip tar bzip2 gzip fontconfig systemd pipewire pulseaudio wireplumber alsa-utils rfkill bluez bluez-utils flatpak python-pip neovim docker kitty mpv iproute2 bc fastfetch ruby-rails visualboyadvance-m code-oss chromium tgpt
```

- Post-install: Clone P10k, set font, enable services (`systemctl enable bluetooth networkmanager docker`).

## Installation & Quick Start

1. **Install Dependencies**: Use AIO command or manually.
2. **Clone Repo**: `git clone https://github.com/TheAnonymousCrusher/dotfiles.git ~/dotfiles`.
3. **Copy Config**: `cp ~/dotfiles/.zshrc ~/.zshrc`.
4. **Source**: `source ~/.zshrc` or restart terminal.
5. **Configure P10k**: `p10k configure`.
6. **Test**: Run `fetch`, `mon`, `netstat`, `yt <url>`, etc.
7. **Customize**: Edit sections in `.zshrc` for personal tweaks.

## Notes & Troubleshooting

- **Root Requirements**: Some commands (e.g., updates, fixes) need sudo.
- **Font Issues**: Ensure Nerd Font is set in terminal (Kitty recommended for images).
- **Dependencies Missing**: Functions gracefully handle absences (e.g., "sensor not found").
- **Sound Clips**: Place mp3s in ~/Documents/VoiceClips for sound aliases.
- **Extensions**: Add more dotfiles to repo as needed.
- **Compatibility**: Tested on Arch; for Ubuntu/Fedora, replace pacman/yay with apt/dnf equivalents.
- **Security**: GPG notes use symmetric encryption; keep passwords secure.

If you encounter issues, check logs or open an issue. Contributions welcome—fork and PR! 🌌 💀
