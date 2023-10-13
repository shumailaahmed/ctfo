# Digital Forensics
Usually organizer will gave us a Digital Image like memory dump like .raw or image file like .e01 and few others more.
Always issuing file <filename> command to whatever file you get first! If the result of the file command is only "data", you must try harder to find the right tool to carve information that contain in the file.
Checkout the EXIF data of the file by using exiftool <filename> command.
Run strings for clues.
Try file carve using foremost <filename>  command. Foremost support all files. But it takes time to extract all file when you face a big size file.
Common locations for various artifacts :-
Web: browsing history, cookies, cache files and others.
Windows OS: registry table, event logs and others.
Linux: configuration files, log files and others.
Mobile phones: app data and others.
Many more!
​
## Tools :-
Volatility. Its a memory extraction utility framework for memory forensic. Use this as your Volatility .
Redline. Another alternative to volatility. But Volatility is the best for me.
Bulk-extractor software. It can extracts features such as email addresses, credit card numbers, URLs, and other types of information from digital evidence files.
FTK Imager. FTK Imager is a data preview and imaging tool that allows you to examine files and folders on local hard drives, network drives, CDs/DVDs, and review the content of forensic images or memory dumps.
Use Autopsy, ProDiscover or EnCase software, function as FTK Imager.
Use e2fsck [mnt image] to fix corrupt filesystem. ext3 and 4.
Recover files using Recuva. They may gave you an image  that you can mount to your machine using FTK Imager. So, go to the drive and try recover the files you want.
RegRipper for registry analysis
Mastering Windows event viewer will give you a plus.
Useful Tools for scanning event log
DeepblueCLI
Chainsaw
WELA
HayaBusa
APTHunter
And many more!