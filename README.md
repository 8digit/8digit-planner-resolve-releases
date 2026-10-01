# 8digit Planner for DaVinci Resolve

Releases of the 8digit Planner panel for **DaVinci Resolve Studio**: export the current timeline and deliver it to [8digit Planner](https://planner.8digitcreative.com) for client review or as a post, then bring reviewers' comments and drawings back as timeline markers.

This repository only holds signed releases. The source code is private.

## Requirements

- macOS
- **DaVinci Resolve Studio 21** (the free version of Resolve can't load Workflow Integrations)
- An 8digit Planner account with access to the brand you deliver to

## Install

Quit DaVinci Resolve, then run this in Terminal:

```bash
curl -fsSL https://github.com/8digit/8digit-planner-resolve-releases/releases/latest/download/install.sh | bash
```

The installer:

- downloads the latest release and checks its signature and checksum before installing anything;
- asks for your Mac password **once**, only to create the plugin's own folder in Resolve's Workflow Integration Plugins folder and give that folder to you, so later updates don't need it;
- uses the `WorkflowIntegration.node` that ships with your own copy of Resolve;
- never contains passwords, tokens or keys.

Open Resolve, then **Workspace → Workflow Integrations → 8digit Planner** and sign in with Planner. Running the installer again repairs the installation.

## Updates

The panel checks for a new version when it opens and every 6 hours. **Update to x.y.z** in the panel's header installs it after verifying its signature; restart DaVinci Resolve to finish. The previous version is kept, and the panel goes back to it if a new version doesn't start.

## Signatures

Each release has `latest.json` and `latest.json.sig`, an ECDSA P-256 (SHA-256) signature. The panel and the installer only accept releases signed by this key:

- id: `8digit-release-2026-10`
- SHA-256 of the DER public key: `647b56e41e7bbf08edd899ce21c6c8c640510e5ef2662669b59c338cdd3f89ea`

## Uninstall

1. In the panel, sign out (this also revokes the connection in Planner → AI assistants).
2. Quit Resolve and remove the plugin and its local data:

```bash
rm -rf "/Library/Application Support/Blackmagic Design/DaVinci Resolve/Workflow Integration Plugins/com.8digit.planner.resolve"
rm -rf "$HOME/Library/Application Support/8digit-planner-resolve"
```

## Support

[planner.8digitcreative.com/support](https://planner.8digitcreative.com/support)

© 2026 8digit Creative LLC
