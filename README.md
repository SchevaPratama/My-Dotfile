# idk what to write on the title tbh

Personal Linux configuration files managed with **GNU Stow**. Optimized for a sleek, responsive, and minimalist **Hyprland** desktop environment powered by **Demonshot / Glyph**, **Fish**, **Kitty**, and **LazyVim**.

---

## 🖥️ Overview & Stack

| Component | Software |
| :--- | :--- |
| **Window Manager** | [Hyprland](https://hyprland.org/) |
| **Shell** | [Fish](https://fishshell.com/) + [Starship](https://starship.rs/) prompt |
| **Terminal** | [Kitty](https://sw.kovidgoyal.net/kitty/) |
| **Editor** | [Neovim](https://neovim.io/) configured with [LazyVim](https://www.lazyvim.org/) |
| **Status Bar & Shell UI** | [Quickshell](https://github.com/outfoxxed/quickshell) (Glyph Rice) |
| **TUI Environment** | [TUIOS](https://github.com/Gaurav-Gosain/tuios) |
| **File Manager** | [Thunar](https://docs.xfce.org/xfce/thunar/start) |
| **Audio** | PipeWire + WirePlumber + [Pavucontrol](https://freedesktop.org/software/pulseaudio/pavucontrol/) |
| **Music Player** | [spotify-player](https://github.com/aome510/spotify-player) & [cava](https://github.com/karlstav/cava) |
| **System Info & Monitor** | [fastfetch](https://github.com/fastfetch-cli/fastfetch) & [btop](https://github.com/aristocratos/btop) |

---

## 📦 Prerequisites

These dotfiles are built on **Arch Linux**. You can install [Glyph-Rice](https://github.com/yasakei/glyph-rice/tree/f78bb7b1c3a30834b068686422b148a79b5fcf2c) and copy my dotfiles to your config folder or Install required core tools and dependencies:

### Core Packages (Pacman)
```bash
sudo pacman -S --needed \
    git stow base-devel \
    hyprland kitty fish starship neovim \
    thunar pavucontrol pipewire wireplumber \
    eza zoxide direnv btop
```

### AUR Helpers & Packages (yay)
```bash
yay -S --needed \
    cava fastfetch tuios \
    spotify-player zen-browser-bin
```

---


## 🚀 Installation

### 1. Clone the repository
Clone into `~/dotfiles`:
```bash
git clone https://github.com/<your-username>/dotfiles.git ~/dotfiles
cd ~/dotfiles
```

### 2. Backup existing configurations
Before applying, back up any conflicting configurations in `~/.config`:
```bash
mkdir -p ~/.config-backup
# Move or backup any existing configurations you wish to preserve
```

### 3. Deploy configs using GNU Stow
Deploy configuration symlinks to your home directory:
```bash
cd ~/dotfiles
stow -v -t ~ .
```

> [!NOTE]
> If you ever want to remove the symlinks created by Stow:
> ```bash
> cd ~/dotfiles
> stow -D -t ~ .
> ```

### 4. Post-Install Steps

#### Set Fish as your default shell
```bash
chsh -s $(which fish)
```

#### Initialize Neovim plugins
Open Neovim and allow LazyVim to automatically download plugins:
```bash
nvim
```

---

## ⌨️ Keybindings Cheatsheet

Below are keybindings configured in the desktop environment:

### Applications
| Keybinding | Action |
| :--- | :--- |
| `Super + T` | Open Terminal (**Kitty**) |
| `Super + W` | Open Web Browser (**Zen**) |
| `Super + Shift + K` | Open Code Editor (**Neovim**) |
| `Super + E` | Open File Manager (**Thunar**) |
| `Ctrl + Alt + V` | Open Audio Mixer (**Pavucontrol**) |

### Window Management
| Keybinding | Action |
| :--- | :--- |
| `Super + Q` | Close active window |
| `Super + F` | Toggle window fullscreen |
| `Super + Alt + Space` | Toggle floating / tiling |
| `Super + Alt + \` | Pin window (Picture-in-Picture) |
| `Super + Z` | Move window mode |
| `Super + X` | Resize window mode |
| `Super + Alt + Arrows` | Resize window dimensions |

### Desktop & Shell Controls
| Keybinding | Action |
| :--- | :--- |
| `Super + /` | Open Keybindings Cheatsheet |
| `Super + Space` | Dashboard / Deck |
| `Super + A` | Quick Settings panel |
| `Super + I` | Settings menu |
| `Super + B` | Toggle Status Bar visibility |
| `Super + Shift + W` | Wallpaper picker |
| `Super + L` | Lock screen |
| `Super + Escape` | Power menu (Shutdown / Reboot) |

### Media & Utilities
| Keybinding | Action |
| :--- | :--- |
| `Print` | Take Screenshot |
| `Super + Alt + R` | Screen Recorder |
| `Super + V` | Clipboard History |
| `Super + .` | Emoji & Symbols Picker |
| `Super + Shift + C` | Color Picker (Hex Eyedropper) |
| `Ctrl + Super + Space` | Play / Pause media |
| `Super + S` | Special Scratchpad Workspace |
| `Ctrl + Shift + Esc` | System Monitor Workspace (**btop**) |
| `Super + M` | Music Workspace |

---

## 🐟 Shell Aliases & Abbreviations (Fish)

A few handy git and system abbreviations pre-configured in `config.fish`:

| Abbreviation | Expanded Command |
| :--- | :--- |
| `lg` | `lazygit` |
| `gs` / `gd` | `git status` / `git diff` |
| `ga` / `gc` | `git add .` / `git commit -am` |
| `gp` / `gpl` | `git push` / `git pull` |
| `gsw` / `gsm` | `git switch` / `git switch main` |
| `l` / `ll` / `la` | `eza` (modern `ls` with icons & groupings) |
| `cava` | Dots visualizer matrix |

---

## 📂 Repository Structure

```text
dotfiles/
├── .config/
│   ├── demonshot/        # Hyprland rules, keybinds, idle & kitty theme
│   ├── fish/             # Shell config and functions
│   ├── gtk-3.0/          # GTK 3 custom styling
│   ├── gtk-4.0/          # GTK 4 custom styling
│   ├── menus/            # Application desktop menus
│   ├── nvim/             # LazyVim setup
│   ├── qalculate/        # Qalculate CLI config
│   ├── quickshell/       # Rice and UI widgets
│   ├── spotify-player/   # Terminal Spotify client config
│   ├── systemd/          # User systemd service units
│   ├── Thunar/           # Custom actions and accelerators
│   ├── tuios/            # Terminal workspace & window manager
│   ├── xfce4/            # Thunar/Xfce XML configs
│   ├── mimeapps.list     # Default application associations
│   ├── pavucontrol.ini   # Pavucontrol geometry & audio prefs
│   ├── user-dirs.dirs    # XDG directory structure
│   └── user-dirs.locale  # System user-dirs locale
├── .gitignore            # Excludes sensitive app caches & tokens
├── .stow-local-ignore    # Excludes non-stow & sensitive targets
└── README.md
```

---

## 🔒 Security Note

This repository contains strict ignore configurations (`.stow-local-ignore` and `.gitignore`) to prevent accidental commits of local app runtime data, browser profiles, tokens, or credentials (such as Discord, Spotify, browser profiles, Copilot, or OBS secrets).

---

## 📄 License

This repository is distributed under the MIT License. Feel free to fork and customize for your own workflow!
