# ThinkPad UEFI firmware patches collection

## Applying

Dump your firmware with an SPI flasher and or get a `bios` region binary from Lenovo.
Comment/Uncomment wanted patches in patches file for your model.
Use [LongSoft's UEFIPatch](https://github.com/LongSoft/UEFITool/releases) to apply them to your rom.
To get a working TPM use [Thrimbor's uefi-sign](https://github.com/thrimbor/thinkpad-uefi-sign) for xx20, xx30, and xx40 ThinkPads. For soldered xx40 and xx50 replace `4C 4E 56 42 42 53 45 43 FB` with `4C 4E 56 42 42 53 45 43 FF` on the previously patched bianry, and [sibrazdic's utility](https://github.com/sibradzic/UEFI-playground/blob/master/fix_vendor_hashes.py) for newer machines.

### Credits

xx
paranoidbashthot
dudu2002
leokim
