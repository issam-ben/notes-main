# Preparation
## Set the console keyboard layout and font
1. List keymaps 
```
localectl list-keymaps
```

	1.set the keymap
```
loadkeys fr
```

## Verify the boot mode
```
cat /sys/firmware/efi/fw_platform_size
```
if the `efi` directory doesn't exist it means the system is booted in BIOS legacy mode.
## Update the system clock
```
timedatectl
```

## Partition the disks
1. List disks
```
fdisk -l
```

2. partition the disk
```
fdisk /dev/vdx
```
The fdisk prompt will appear.
3. Format the disk
```
mkfs.ext4 /dev/vda1
```

## Mount the root file system
we need to mount the root filesystem to /mnt:
```bash
mount /dev/vda4 /mnt
```

4. mount efi and boot partitions to their corresponding location in /mnt
```
mount --mkdir /dev/vda2 /mnt/boot
mount --mkdir /dev/vda1 /mnt/boot/efi
```

# Installation
## Install core packages

```
pacstrap -K /mnt base linux linux-firmware
```

## Install Necessary packages

```
pakstrap -K /mnt amd-ucode networkmanager vim vi nano man-db man-pages texinfo grub efibootmgr os-prober mtools sudo
```

## Configuring the system
### fstab
Generate an [fstab](https://wiki.archlinux.org/title/Fstab "Fstab") file (use `-U` or `-L` to define by [UUID](https://wiki.archlinux.org/title/UUID "UUID") or labels, respectively):
```
genfstab -U /mnt >> /mnt/etc/fstab
```

### Chroot
```bash
arch-chroot /mnt
```

### Time
```bash
ln -sf /usr/share/zoneinfo/Africa/Algiers /etc/localetime
```
This creates a symbolic link from the source file to the destination. -f option to force and overwrite existing `localetime` files.
```bash
hwclock --systohc
```

### Localization
```bash
vim /etc/locale.gen
```
uncomment en_US.UTF-8 and other necessary UTF-8s, and ISOs.

```bash
locale-gen
```

```bash
vim /etc/locale.conf
--or--
echo LANG=en_US.UTF-8 > /etc/locale.conf
----------------------------
LANG=en_US.UTF-8
```

```bash
export LANG=en_US.UTF-8
```

```bash
vim /etc/vconsole.conf
---------------------------
KEYMAP= fr
```
set the keyboard layout permenantly.
### Network Configuratio
```bash
echo hostname > /etc/hostname
```
create hostname file and inside it write your hostname.

edit `/etc/hosts` file.
```config
127.0.0.1       localhost  
::1             localhost  
127.0.1.1       arch-station
```

### Create root Password
```bash
passwd
```


### Install GRUB Bootloader

After mounting the boot partitions to their mount points and creating necessary directories.
```bash
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB
```

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

### Create New User
```bash
useradd -m issam
```

```bash
passwd issam
```

```bash
usermod -aG wheel,audio,video,storage issam
```
- edit sudoers file
```bash
vim /etc/sudoers
```
uncomment
```bash
## Uncomment to allow memebers of group wheel to execute any command
```
### Install Desktop Environment

- install display server and gpu drivers
```bash
pacman -S xorg-server xorg-apps nvidia nvidia-utils
```
- install desktop environment 
```bash
pacman -S plasma
```
- install KDE Applications
```bash
pacman -S kde-applications
```

