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
1. Volatility. Its a memory extraction utility framework for memory forensic. Use this as your Volatility .
2. Redline. Another alternative to volatility. But Volatility is the best for me.
3. Bulk-extractor software. It can extracts features such as email addresses, credit card numbers, URLs, and other types of information from digital evidence files.
4. FTK Imager. FTK Imager is a data preview and imaging tool that allows you to examine files and folders on local hard drives, network drives, CDs/DVDs, and review the content of forensic 5. Images or memory dumps.
6. Use Autopsy, ProDiscover or EnCase software, function as FTK Imager.
7. Use e2fsck [mnt image] to fix corrupt filesystem. ext3 and 4.
8. Recover files using Recuva. They may gave you an image  that you can mount to your machine using FTK Imager. So, go to the drive and try recover the files you want.
9. RegRipper for registry analysis
10. Mastering Windows event viewer will give you a plus.
11. Useful Tools for scanning event log
12. DeepblueCLI
13. Chainsaw
14. WELA
16. HayaBusa
14. APTHunter
And many more!

https://www.sans.org/blog/the-ultimate-list-of-sans-cheat-sheets/
