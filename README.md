# ThinkPad UEFI firmware patches collection

## Applying

1. Obtain a UEFI dump 
  - Dump your firmware with an SPI flasher 
  - or get a `bios` region binary from Lenovo's update package
2. Download appropiate patches.txt and comment/uncomment wanted patches in patches file for your model.
3. Use [LongSoft's UEFIPatch](https://github.com/LongSoft/UEFITool/releases) to apply them to your rom.
4. Fix tamper protection
  - To get a working TPM use [Thrimbor's uefi-sign](https://github.com/thrimbor/thinkpad-uefi-sign) for xx20, xx30, and xx40 ThinkPads. 
  - For xx75, xx85 [sibrazdic's utility](https://github.com/sibradzic/UEFI-playground/blob/master/fix_vendor_hashes.py)
  - For soldered xx40 and onwards replace `4C 4E 56 42 42 53 45 43 FB` with `4C 4E 56 42 42 53 45 43 FF` on the previously patched binary with a hex editor such as [HxD](https://mh-nexus.de/en/hxd/) or [wxHexEditor](https://www.wxhexeditor.org/)
5. Flash back your successfully patched binary



## xx50 LCD
[./xx50-lcd](https://github.com/digmorepaka/thinkpad-firmware-patches/tree/master/xx50-lcd)


## Compatibility WIP

| Model/Series | Supported | Notes | TPM |
| --- | --- | --- | --- |
| T430 | Yes | Internal flash | Yes |
| T530 | Yes | Internal flash | Yes |
| T430s | Yes | Internal flash | Yes |
| W530 | Yes | Internal flash | Yes |
| X230 | Yes | Internal flash | Yes|
| X230t | Yes | Different Whitelist patch, Internal flash | Yes |
| S230u | Yes | No whitelist patch at the moment, Internal flash | Yes |
| X131e | Yes | Different Whitelist patch | ? |
| L430/L530 | Yes | Shared board and firmware, Internal flash | Yes |
| X1C1 | ? | N/A | Yes |
| T440p | Yes | N/A | Yes |
| W540/W541 | Yes | Different stock trackpad and PS/2 ID | Yes |
| T540p | Yes | N/A | Yes |
| T440 | Yes | N/A | No |
| T440s | Yes | N/A | No |
| X240 | Yes | N/A | No |
| X1C2 | Yes | N/A | No |
| L540 | Yes | N/A | ? |
| L440 | Yes | Shared firmware with L540 | ? |
| T450s | Yes | N/A | No |
| T450 | Probably | N/A | No |
| T550/W550s | Probably | Shared board | No |
| X250 | ? | N/A | No |
| X1C3 | ? | N/A | No |
| T460 | Yes | N/A | No |
| T460s | Probably | N/A | No |
| T560/P50s | Yes | Shared board | No |
| P50 | Yes | N/A | No |
| X260 | Yes | N/A | No |
| X1C4 | ? | N/A | No |
| Yoga 460 | Yes | N/A | No |
| TP13-1 | Yes | WLAN untested | No |
| T470 | Yes | Flash chip next to SOC, Don't touch memory settings | No |
| T470s | Yes | N/A | No |
| T570/P51s | Yes | USB wwan whitelist version | No |
| P51 | Yes | N/A | No |
| X270 | Yes | N/A | No |
| X1C5 | ? | N/A | No |
| T480 | Yes | Flash chip next to SOC, Don't touch memory settings | No |
| A485 | Yes | N/A | Yes |
| A285 | Yes | N/A | Yes |
| T480s | Yes | N/A | No |
| T580/P52s | Yes | Shared board | No |
| P52 | Yes | N/A | No |
| X280 | Yes | N/A | No |
| X380Y | Yes | N/A | No |
| X1C6 | Yes | Don't touch memory settings | No |
| X1Y2 | Yes | Flash chip near LTE card, Don't touch memory settings | No |
| TP11e-6 | Yes | N/A | No |
| T490/T590/P43s/P53s | No | Shared board | ? |
| T495 | Yes | 1.8V flash, in-system programming is problematic | Yes |
| T490s/X390 | No | Shared board | ? |
| T495s/X395 | Yes | Shared board | Yes |
| X1C7 | No | N/A | No |
| T14/T15/P14s/P15s Intel 1st gen | No | Shared board | ? |
| T14/P14s AMD 1st gen | No | Shared Board | ? |
| T14s/X13 Intel 1st gen | No | Shared board | ? |
| T14s/X13 AMD 1st gen | No | Shared board | ? |
| X1C8 | No | N/A | No |
| T14/T15/P14s/P15s Intel 2nd gen | No | Shared board | ? |
| T14/P14s AMD 2nd gen | No | Shared Board | ? |
| T14s/X13 Intel 2nd gen | No | Shared board | ? |
| T14s/X13 AMD 2nd gen | No | Shared board | ? |
| X1C9 | No | N/A | No |
| X1 Tablet Gen 3 | Yes | Internal Flash | Yes | 

## Reporting compatibility

Open a new issue with the following table:

| Model | T430 |
| --- | --- |
| Patchset | Default for generation |
| TPM | Yes, thinkpad-uefi-sign |
| Notes | DDR3-1066/800 speed limiter makes machine unbootable and is a non-volatile setting | 


## Submitting patchset

Open a pull request with the patchset added and the following table in comment:

| Model | X131e |
| --- | --- |
| TPM | Haven't tested |
| Notes | Different whitelist patch | 


Patches are standard UEFIPatch format, mention what it does, what machine it is for, who made it(your name if you did, if you found it on a forum mention OP's name) for special patchsets make sure they are uncommented by default. Example:

```
# LenovoWmaPolicyDxe | WL removal | ripped from nephiel | x131e 3.01
# uncomment to use
#79E0EDD7-9D1D-4F41-AE1A-F896169E5216 10 P:100BC841390B0F84:100BC841390B90E9 
#79E0EDD7-9D1D-4F41-AE1A-F896169E5216 10 P:00000045390B0F84:00000045390B90E9 
#79E0EDD7-9D1D-4F41-AE1A-F896169E5216 10 P:100BC841394B0474:100BC841394B04EB 
#79E0EDD7-9D1D-4F41-AE1A-F896169E5216 10 P:0F846CFFFFFFEBAF:9090909090909090
```


## What does it mean "TPM yes?", or "Internal flash".. etc

Check out [this comment](https://github.com/digmorepaka/thinkpad-firmware-patches/issues/3#issuecomment-730474066) for clarification on TPM and Internal flashing.


### Credits

xx
paranoidbashthot
dudu2002
leokim
nephiel

