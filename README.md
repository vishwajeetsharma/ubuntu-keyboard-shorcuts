# Ubuntu Keyboard Shortcuts

This repository stores my custom GNOME/Ubuntu keyboard shortcut configurations (such as mapping `Ctrl + Tab` to switch windows) so they can be quickly restored on a fresh Ubuntu installation.

## Files Included

* **`wm-keybindings.conf`**: Window manager navigation shortcuts (window switching, workspace movement, tiling, etc.).
* **`media-keys.conf`**: System, media, and custom user-defined shortcuts.

---

## Restore Shortcuts (Fresh Install)

1. Clone this repository and navigate into the folder:
   ```bash
   git clone <your-repo-url>
   cd <your-repo-folder>
   ```

2. Load the shortcut configurations into GNOME using `dconf`:
   ```bash
   dconf load /org/gnome/desktop/wm/keybindings/ < wm-keybindings.conf
   dconf load /org/gnome/settings-daemon/plugins/media-keys/ < media-keys.conf
   ```

*Changes take effect immediately—no logout or reboot required.*

---

## Update Backup (After Changing Shortcuts)

Whenever you add or modify shortcuts in **Settings > Keyboard**, export the updated configuration and push to Git:

```bash
dconf dump /org/gnome/desktop/wm/keybindings/ > wm-keybindings.conf
dconf dump /org/gnome/settings-daemon/plugins/media-keys/ > media-keys.conf

git add .
git commit -m "Update Ubuntu keyboard shortcuts"
git push
```

## Reset to Ubuntu Defaults (Optional)

If you ever want to revert all shortcuts back to factory settings:

```bash
dconf reset -f /org/gnome/desktop/wm/keybindings/
dconf reset -f /org/gnome/settings-daemon/plugins/media-keys/
```

### Restore Input Remapper 2
```bash
rm -rf ~/.config/input-remapper-2
ln -s ~/dotfiles/ubuntu/input-remapper-2 ~/.config/input-remapper-2
sudo systemctl restart input-remapper
```
