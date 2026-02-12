## Usage

Clone this repo into your `void-packages/srcpkgs` folder:

```bash
cd void-packages/srcpkgs
git clone https://git.deadzone.lol/Wizzard/claude-desktop-void claude-desktop
```

Then build and install:

```bash
cd void-packages
./xbps-src pkg claude-desktop
xi claude-desktop
```

The template auto-updates daily via Gitea CI using pre-patched releases from [claude-desktop-bin](https://github.com/patrickjaja/claude-desktop-bin).
