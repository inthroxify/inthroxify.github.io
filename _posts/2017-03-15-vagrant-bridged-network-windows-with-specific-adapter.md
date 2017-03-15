---
layout: post
title: "Vagrant: Getting a bridged network to work on Windows"
---

Add the following to the Vagrantfile. Change the adapter name to that found via `ipconfig`, and change the IPs where appropriate.

    config.vm.network "public_network", bridge: "Broadcom Gigabit Ethernet"
    config.vm.provision "shell", run: "always", inline: "route add default gw 172.16.0.1"
    config.vm.provision "shell", run: "always", inline: "eval `route -n | awk '{ if ($8 ==\"enp0s3\" && $2 != \"0.0.0.0\") print \"route del default gw \" $2; }'`"
    config.vm.provision "shell", run: "always", inline: "sed -i.bak '/10\.0\./d' /etc/resolv.conf"
