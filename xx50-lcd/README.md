# xx50 screen whitelist
[ORIGINAL POST](https://www.reddit.com/r/thinkpad/comments/ac7u21/tutorial_t450t450sw550st550x250_screen_whitelist/)
I'm just summarizing and reuploading


When you replace the LCD panel on a laptop from this genertaion for one that is not an OEM Lenovo panel, your brightness will be stuck at 100% in Windows.

One way to fix it is to overwrite the EDID vendor to `LEN`, the other is to flash your UEFI and use a GOP module where all of the vendors are approved.
This will cover the latter. 


Once you have your UEFI backed up, open it in UEFITool, and search for GUID:`81334616-86CE-49C2-B6F9-1804E61C73F6`, and GUID:`CC71B046-CF07-4DAE-AEAD-7046845BCD8A`. 

Select "replace as is" and choose the aproppriate replacement module based on filename. 

After that you can save your rom, patch it with any other patches you may want, and flash it. 

