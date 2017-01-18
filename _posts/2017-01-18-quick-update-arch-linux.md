---
layout: post
title: "arch linux: update an arch linux install like apt-get distupgrade"
---

    pacman -Syy #apt-get update
    pacman -Su #apt-get distupgrade
    pacman -S udev #udev might have got blown up, so fix it
    mkinitcpio -p linux #boot image needs the new stuff from the udev fix
    reboot
