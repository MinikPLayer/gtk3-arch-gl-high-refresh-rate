# GTK3 PKGBUILD (with high refresh rate patches for the GLArea)
This repository contains a modded GTK3 PKGBUILD repository, which changed the default window refresh / update rate to a higher (165Hz) one.

## Current state
Current method is a bit of a hack and works by changing the timer interval to a different constant.

## Change to another refresh rate
Calcualte a new constant timer by dividing 1000000us by your refresh rate. (For example for 165Hz it's ``1000000 / 165 = ~6060``).
Modify the ``0002-refresh-rate-timer.patch`` file by changing the patched constant (**6060**) to the calculated one.

## Build and Install
```
git checkout {target_refresh_rate_branch}
makepkg -si
```

## Update upstream
```
git remote add upstream https://gitlab.archlinux.org/archlinux/packaging/packages/gtk3
git fetch upstream
git merge upstream/master
```
