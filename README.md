This repo contains the fixed DSDT tables for GPD P2 Max for it to function correctly under Linux.

Note that the fixes are not specific to Linux. It works fine in Windows simply because the Windows driver does not care about the DSDT definitions as much as the Linux one does. The DSDT itself is broken in its stock state.

You can consult [ArchWiki#DSDT](https://wiki.archlinux.org/index.php/DSDT) for instructions on how to use it. Basically you need to re-compile the DSDT file, package it into a CPIO archive, and append it to your kernel's initrd option.

You can find a pre-built CPIO image named `acpi_override` in the GitHub Release page. Download it and copy to your `/boot` partition, then add something like

```
initrd /acpi_override
```

to your bootloader's configuration. Don't replace the exisiting `initrd` options, just insert it before your original `initrd` option.
