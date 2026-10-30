# Installer Next

![Build Status](https://img.shields.io/github/actions/workflow/status/rushiranpise/InstallerNext/autoci.yml?label=Build&logo=github) [[中文说明文档]](README_CN.md)

An LSPosed/Xposed module that shows the app's package info - package name, version, target SDK,
user - in the package installer, both for installs and updates and for uninstalls.

## Introduction

- Show app's package info for Package Installer.
- See [features](image/README.md)

## Compatibility

Compatible with AOSP-like installers. Tested on:

1. Hydrogen OS Android 7.1.1
2. Oxygen OS Android Q
3. Pixel Experience 11
4. LineageOS Android 12
5. LineageOS Android 13
6. Pixel/AOSP Android 13
7. Pixel/AOSP Android 14
8. Android 16 (v2 installer, QPR2)
9. **Android 17 / One UI 9** - Google Package Installer `17-15544436`

## How it works

The installer has two generations of UI, and the module hooks whichever one the host actually has:

- **v2 installer** (`com.android.packageinstaller.v2.ui`) - hooks `InstallationFragment.updateUI()`
  and `UninstallationFragment.updateUI()`, then reads the view model and repository to find the
  package being installed. This is the path Android 16+ uses.
- **Legacy installer** - hooks `PackageInstallerActivity.startInstallConfirm()` and
  `UninstallerActivity.showConfirmationDialog()`, then `UninstallAlertDialogFragment.onCreateDialog()`.

## Credits

This is a continuation of **InstallerPlus (Installer++)**, originally by
**[NextAlone](https://github.com/NextAlone/InstallerPlus)** - the hooks, the resource injection, the
UI it adds and the whole idea are theirs. Thank you.

It also carries work picked up from the community forks, with the original authorship kept in the
git history:

- **[hxreborn](https://github.com/hxreborn/InstallerPlus)** - Android 16 QPR 2 support, the v2
  installer path this module now relies on.
- **[cbkii](https://github.com/cbkii/InstallerPlusFork)** - fixes cherry-picked here: nullable
  `ApplicationInfo` handling in the Q and N hooks, crash protection in `InstallerHookN`, and the
  host-package fix for resource resolution.
- **[pumPCin](https://github.com/pumPCin/InstallerPlus)** and
  **[TeaqariaWTF](https://github.com/TeaqariaWTF/InstallerPlus)** - consulted while comparing the
  forks; nothing from them was needed in the end.

Original project licence: [AGPL-3.0](./LICENSE.md), unchanged.

### [InstallerPlus End User License Agreement(EULA) (Chinese Only)](./app/src/main/assets/eula.md)
