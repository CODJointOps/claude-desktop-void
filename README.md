# claude-desktop (Void template)

Packages Anthropic's **first-party** Claude Desktop for Void Linux.

The distfile is the `.deb` from Anthropic's own signed apt repository
(`downloads.claude.ai/claude-desktop`). Nothing is repacked, patched, or
rebuilt: the installed binaries are bit-for-bit identical to what Anthropic
publishes.

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

## Optional runtime extras

The upstream `.deb` lists these as *Recommends*, which xbps has no equivalent
for. Install them by hand if you want the feature:

- `gnome-keyring` or `kwallet` — a Secret Service provider, or the app cannot
  persist your login.
- `xdg-desktop-portal-gtk` / `-kde` — a portal backend for file pickers and
  screen sharing.
- `qemu`, `virtiofsd` — the Cowork sandbox.

## Auto-update

`.gitea/workflows/update.yml` runs daily. It verifies the apt repository's
`InRelease` against the pinned Anthropic signing key
(`31DD DE24 DDFA B679 F42D 7BD2 BAA9 29FF 1A7E CACE`), checks the index has
not expired, confirms each `Packages` file matches the checksum in that signed
`Release`, and only then copies the new version and per-architecture checksums
into the template. Every value it commits is therefore transitively signed by
Anthropic; if any link in that chain fails, the job fails instead of
publishing.
