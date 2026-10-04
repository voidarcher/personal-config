# Things to install with Arch:
----------------------------
### Pacstrap: 
```sh
pacstrap -K /mnt base base-devel linux-lts linux-lts-headers linux-firmware sof-firmware networkmanager reflector fwupd vim git intel/amd-ucode 
```

When you arch-chroot in, make sure to run:
```sh
# systemctl enable NetworkManager
# systemctl start NetworkManager
```

### First pacman after connecting via NetworkManager:
```sh
pacman -Syu sddm wget plasma firefox konsole kate dolphin gwenview anki fcitx5-im fcitx5-mozc noto-fonts-cjk ttf-liberation mgba-qt pacman-contrib man-db ark mpv emacs alsa-utils
```

#### Also, remember to run:
```sh
# systemctl enable sddm
```

### Adding a user
First, as root run:
```sh
# useradd -m -G wheel -s /bin/bash username
# passwd username
```

Then, give yourself sudo permissions with:
```sh
# EDITOR=vim visudo
```
Go down to the bottom and uncomment
```sh
# %wheel ALL=(ALL:ALL) ALL
```

### Setting up systemd-boot:
(Note: If you're using GRUB, see Slackware_Stuff.txt)

```sh
[/boot/loader/loader.conf]
default  arch.conf
timeout  4
console-mode max
editor   no
```
```sh
[/boot/loader/entries/arch.conf]
title    Arch GNU/Linux (Vanilla)
linux    /vmlinuz-linux
initrd   /initramfs-linux.img
initrd   /amd-ucode.img
options  root=UUID=5ac8b344-c999-99a9-c123-22922a9bdeff rw
sort-key 01
```
```sh
[/boot/loader/entries/arch-lts.conf]
title    Arch GNU/Linux (LTS)
linux    /vmlinuz-linux-lts
initrd   /initramfs-linux-lts.img
initrd   /amd-ucode.img
options  root=UUID=5ac8b344-c999-99a9-c123-22922a9bdeff rw
sort-key 02
```
#### make sure you replace the UUID with the correct one (new one every time) 
```sh
[In vim]
:r! blkid
```
When you're finally booted into your system, KDE and all, try out:
```sh
$ sudo pacman -Syu fastfetch
```

### Written on Sunday, October 4, 2026
I don't know why I don't love Arch the way I used to. Maybe I've hit the point
where normal stuff just doesn't hit anymore, and anything familiar just feels
insufficient. This is not an attitude I have towards anything else, where I tend
to love familiarity.

Granted, if that's what I'm looking for, I'd just be running the Debian install
that served me so well for so long. And here I am (I'm writing this text while
on Slackware). 

I'm pretty sure that one day, I'll just end up using Debian forever, but I guess
while I still give a shit, this distro-hopping can't hurt.

Maybe Arch'll be endgame, instead, though. Admittedly, I really do hate any
packages being installed that I'm not aware of, and I do think Arch's general
simplicity is a virtue. Granted, Slackware is simpler still. 

All I know is, I still remember my first time installing Arch Linux. It was on
Thanksgiving 2022. Tipto and Tarif's parents were here. I had that crappy black
Dell Inspiron 15 with the touchpad that fucked off after a few months.

I remember how terrified I was the whole time, and how I forgot to install stuff
like Gwenview and Konsole (figured they would just be included when I installed
KDE lolol), though I fortunately had already learned how to drop into a TTY and
fix that. 

Having only used Ubuntu and Fedora up until then, it was by a mile the most complex
Linux-related thing I'd done to that point. 

At this point, I've installed Arch about 20 or so times over the course of the last
month (distro-hopping is a special kind of disease), so installing it is basically
just an inconvenience. Though I still refuse to use archinstall, so that's really on
me. 

I don't know. My plan for the moment is to just keep using Slackware for a while. 
In my head, I'm a Slacker. But I don't know if that's actually true. There's so
much contrivance in my head, man. I don't think most of this stuff really matters.
But then, I think it's kind of cool that I care about this nonsense. I don't think
I'd like my personality very much if all I cared about were the important things.
Nothing in my head except eating nutrient-dense gruel and going to work. I miss
being a kid and being so taken by every little thing on Earth. I'm glad I still have
a bit of that left in me.
