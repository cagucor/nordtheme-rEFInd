![](screenshot.png)

A theme for the [rEFInd UEFI Boot Manager](http://www.rodsbooks.com/refind/) based on the [Nord Colour Theme](https://www.nordtheme.com/)

Icons are included for a variety of Linux distributions, as well as macOS and Windows. 
Note: For some reason the icon for a windows 10 os defaults to the icon label as `os_win8.png`. 

## Installation

1. Find the rEFInd directory on your boot volume. For me, it's `/boot/efi/EFI/refind`. (Note: you will likely need to do this as root)

2. Clone this repository to the `themes` directory inside the rEFInd directory. Make a new directory if needed.

```bash
cd /boot/efi/EFI/refind
mkdir themes
cd themes
git clone https://github.com/cagucor/nordtheme-rEFInd.git
```

3. Add the following line to the bottom of the `refind.conf` file in the 
   rEFInd directory

```bash
include themes/nordtheme-rEFInd/theme.conf
```

## Configuration

By default, rEFInd will create entries for any `.efi` files found in the EFI
directory on your boot volume. 

You can exclude certain directories containing `.efi` files by passing them
to the `dont_scan_dirs` token of the `refind.conf` file:

```bash
# Exclude any .efi files found in /EFI/BOOT and /EFI/old
dont_scan_dirs /EFI/BOOT,/EFI/old
```

You can also exclude specific `.efi` files themselves by passing them to the 
`dont_scan_files` token of the `refind.conf` file:

```bash
# Exclude /EFI/ubuntu/mmx64.efi and any .efi file named shimx64.efi
dont_scan_files /EFI/ubuntu/mmx64.efi,shimx64.efi
```

To simplify the boot-menu, efi entries can also be removed from the rEFInd menu by pressing the delete or minus key while hovering over the entry.

You can also change the icon used for a particular `.efi` file by placing a
`.png` file of the same name in the directory with it:

```bash
$ ls /boot/EFI/BOOT

BOOTX64.EFI BOOTX64.PNG
```

For automatically detected operating systems, change the icons in the icon directory in the theme repository

## Additional Information

Additional information about configuring rEFInd may be found [here](http://www.rodsbooks.com/refind/configfile.html).
