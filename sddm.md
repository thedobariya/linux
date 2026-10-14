Here is a clean Markdown guide you can save as something like `ubuntu-sddm-theme-setup.md` for a fresh Ubuntu 24.04 install.

```markdown
# Install simple-sddm theme on Ubuntu 24.04 (Hyprland setup)

## 1. Install SDDM

```bash
sudo apt update
sudo apt install sddm -y
```

If asked to choose a display manager:

Select:

```
sddm
```

---

## 2. Install required Qt5/QML dependencies

The `simple-sddm` theme uses Qt5 QML modules.

Install:

```bash
sudo add-apt-repository universe
sudo apt update

sudo apt install \
qml-module-qtquick-controls \
qml-module-qtquick-controls2 \
qml-module-qtquick-layouts \
qml-module-qtgraphicaleffects \
qml-module-qtmultimedia -y
```

---

## 3. Clone the theme

Download the theme:

```bash
git clone https://github.com/JaKooLit/simple-sddm.git ~/simple-sddm

# or 

git clone https://github.com/JaKooLit/simple-sddm-2.git ~/simple-sddm-2
```

---

## 4. Copy theme to SDDM themes folder

Move it:

```bash
sudo mv ~/simple-sddm /usr/share/sddm/themes/

# or 
 
sudo mv ~/simple-sddm-2 /usr/share/sddm/themes/
```

Check:

```bash
ls /usr/share/sddm/themes/
```

You should see:

```
simple-sddm
```

---

## 5. Configure SDDM theme

Create the config directory:

```bash
sudo mkdir -p /etc/sddm.conf.d
```

Create config:

```bash
sudo nano /etc/sddm.conf.d/theme.conf.user
```

Add:

```
[Theme]
Current=simple-sddm

# or

[Theme]
Current=simple-sddm-2
```

Save:

```
CTRL + O
ENTER
CTRL + X
```

---

## 6. Restart SDDM

```bash
sudo systemctl restart sddm
```

---

## Troubleshooting

### Error:

```
QtQuick.Layouts is not installed
```

Install:

```bash
sudo apt install qml-module-qtquick-layouts
```

---

### Check SDDM logs

```bash
journalctl -u sddm -b | tail -50
```

---

### Emergency: switch back to TTY

If the login screen breaks:

Press:

```
CTRL + ALT + F3
```

Login and disable the theme:

```bash
sudo nano /etc/sddm.conf.d/theme.conf.user
```

Change:

```
[Theme]
Current=breeze
```

Restart:

```bash
sudo systemctl restart sddm
```

```

This is the exact dependency chain that worked on your Ubuntu 24.04 install.
```
