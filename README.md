# AX Libs

The UI toolkit and settings framework shared by RL's World of Warcraft addons. Both are based on
**WaypointUI** by **AdaptiveX** and named in their honour.

| Folder | What it is |
|---|---|
| `AX_Modules` | The UI toolkit: a module registry, saved variables, slash commands, UI primitives, animation and more. |
| `AX_Settings` | A settings window and Options → AddOns panel, built from a declarative schema. See [its README](AX_Settings/README.md). |

## Using it in an addon

The libraries are embedded in each addon, not installed on their own. Every file shares the
addon's namespace, so two addons can carry different versions without clashing.

The CurseForge packager pulls this repo into the addon's `libs` folder when it builds a release.
In the addon's `.pkgmeta`:

```yaml
externals:
  libs:
    url: https://github.com/RL-addon-dev/AX_Libs.git
    tag: v1.0.0
```

Pin a tag, so each addon ships the version it was tested with. Then load both from the `.toc`,
as the [AX_Settings README](AX_Settings/README.md#embedding) shows:

```
libs\AX_Modules\packages.xml
...
libs\AX_Settings\AX_Settings.xml
```

For development, clone this repo into the addon's `libs` folder and git-ignore `libs/` in the
addon's repo:

```
git clone https://github.com/RL-addon-dev/AX_Libs.git libs
```

## Changes

Only add, annotate or fix. Never remove or rename anything an addon might use, since every addon
updates on its own schedule. Tag each release (`v1.0.0`, `v1.1.0`, ...) and bump the tag in an
addon's `.pkgmeta` once it's tested there.

## Licence

GPL-3.0, like WaypointUI. Each folder has its own `LICENSE`, and a `NOTICE` that lists what
changed from WaypointUI.
