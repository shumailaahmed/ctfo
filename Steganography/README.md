# Steganography

# Strings
Usually when organizer gave us Image, Music, Video, Zip, EXE, File System, PDF and other files, it a steganography or forensics challenge. Run file command first. 

View all strings in the file with strings `-n 7 -t x filename.png`.
We use -n 7 for strings of length 7+, and -t x to view- their position in the file.
Alternatively, you can view strings on this site once an image has been uploaded.

`strings filename.txt | grep flag`

# Exif
Metadata is important. Checkout the EXIF data of the file by using exiftool [filename] command.
Check image metadata
http://exif.regex.info/exif.cgi

# Binwalk
Try issuing binwalk [filename] on the file. They may hide another file in the file.
To extract, use binwalk -e. 
To extract one specific signature type, use binwalk -D 'png image:png' [filename]. 
To extract all files, run binwalk --dd='.*' [filename].
`binwalk -Me filename.png`

# pngcheck
We can use pngcheck to look for optional/correct broken chunks. This is vital if the image appears corrupt.
Run `pngcheck -vtp7f filename.png` to view all info.

`v` is for verbose, `t` and `7` display tEXt chunks, `p` displays contents of some other optional chunks and `f` forces continuation after major errors are encountered.

Related write-ups:
https://github.com/ctfs/write-ups-2015/tree/master/plaidctf-2015/forensics/png-uncorrupt
https://github.com/ctfs/write-ups-2015/tree/master/seccon-quals-ctf-2015/stegano/steganography-2

# Explore Colour & Bit Planes
Images can be hidden inside of the colour/bit planes. Upload your image to this site here. On the image menu page, explore all options in the top panel (i.e. Full Red, Inverse, LSB etc).

Go to "Browse Bit Planes", and browse through all available planes.

If there appears to be some static at the top of any planes, try extracting the data from them in the "Extract Files/Data" menu.

https://www.doyler.net/security-not-included/image-steganography-microctf-2017
https://github.com/krx/CTF-Writeups/blob/master/CSAW%2016%20Quals/for250%20-%20Watchword/jk_actual_writeup.md
https://github.com/ctfs/write-ups-2014/tree/master/asis-ctf-quals-2014/blocks
https://mokhdzanifaeq.github.io/2016/12/14/cybersocks-regional-2016-color-writeup/

#  Extract LSB Data
As mentioned in step 5, there could be some static in bit planes. If so, navigate to the "Extract Files/Data" page, and select the relevant bits.

# Check RGB Values
ASCII Characters/other data can be hidden in the RGB(A) values of an image.

Upload your image https://stegonline.georgeom.net/upload, and preview the RGBA values. Try converting them to text, and see if any flag is found. It might be worth looking at just the R/G/B/A values on their own.

Related write-ups:
https://github.com/ctfs/write-ups-2015/tree/master/mma-ctf-2015/stego/miyako-350

# Found a password? (Or not)
If you've found a password, the goto application to check should be steghide. Bear in mind that steghide can be used without a password, too.

You can extract data by running `steghide extract -sf filename.png` .

It might also be worth checking some other tools:
https://www.openstego.com/
https://github.com/Baldanos/Stegpy
https://outguess.rbcafe.com/
http://linux01.gwdg.de/~alatham/stego.html

Related write-ups:
http://blog.teambroast.com/2017/03/pragyan-star-wars-steganography-100.html
https://github.com/mzfr/ctf-writeups/tree/master/xiomara-2019/Forensics/Steghide
https://github.com/ctfs/write-ups-2015/tree/master/csaw-ctf-2015/forensics/airport-200
https://blog.compass-security.com/2017/11/write-up-blackalps-y-not-ctf/

# Browse Colour Palette
If the PNG is in type 3 for type specs (https://www.w3.org/TR/PNG-Chunks.html), you should look through the colour palette.

This site has a feature for randomizing the colour palette, which may reveal the flag. You can also browse through each colour in the palette, if the flag is the same colour.

It may also be worth looking at the palette indexes themselves, as a string may be visible from there.

Related write-ups:
https://github.com/ctfs/write-ups-2014/tree/master/plaid-ctf-2014/doge-stege

# Pixel Value Differencing (PVD/MPVD)
It would be rare to have a case of PVD where you're not explicitly told that this is the steganographic method, as it's very niche.

However, this is a method where the differences between pixel pairs are measured slightly adjusted in order to hide data.

A full paper on this process can be found here. A PVD feature to this site would be appreciated!

Related write-ups:
https://github.com/zst-ctf/tjctf-2019-writeups/tree/master/Writeups/Planning_Virtual_Distruction
https://github.com/ctfs/write-ups-2015/tree/master/mma-ctf-2015/stego/miyako-350

# Image Hints
Google the images, differentiate the md5hash. If you found same image but have a different md5 hash, it may probably have been altered.
Analyse the header and the content of the file using any hex editor.
Know the file signature. Maybe they gave us corrupt header! So fix it!
Maybe zoom-in and zoom-out method can get the flag.
Use https://www.tineye.com/ to reverse search the image in the internet.
Use imagemagick command tool to do image manipulation.
Use Stegsolve.jar tools. There are so many CTF I've participated that I used this tool to unhide flag from an image.

File carve using steghide --extract -sf <filename>. Try find the password with your own-self. Maybe, the organizer will give hints or the password may in another file.
Check for any corruption on PNG file by using pngcheck <filename.png> command.
Detect stegano-hidden data in PNG & BMP s by issuing zsteg -a <filename.png>.
Use SmartDeblur software to fix blurry on image.
Use stegcracker <filename> <wordlist> tools Steganography brute-force password utility to uncover hidden data inside files.
Use tesseract to scan text in image and convert it to .txt file.
Another powerfool tool is called zsteg.
Steganosuite 
Extract data from image (-x)
Some of online stegano decoder :-
https://futureboy.us/stegano/decinput.html
http://stylesuxx.github.io/steganography/
https://www.mobilefish.com/services/steganography/steganography.php
https://manytools.org/hacker-tools/steganography-encode-text-into-image/
https://steganosaur.us/dissertation/tools/image
https://georgeom.net/StegOnline
http://magiceye.ecksdee.co.uk/

# Compressed file
Unzip it.
Use zipdetails -v command to display details about the internal structure of a Zip file.
Use zipinfo command to know details info about Zip file.
Use zip -FF input.zip --out output.zip attempt to repair a corrupted zip file.
Brute-force the zip password using fcrackzip -D -u -p rockyou.txt  filename.zip

To crack 7z run 7z2hashcat32-1.3.exe filename.7z. Then john --wordlist=/usr/share/wordlists/rockyou.txt hash

# Music Files
Use binwalk first. They may embedded something in the file.
Use Audacity.
Use Sonic Visualizer. Look at spectogram and other few Pane.
Use Deepsound.
Use SilentEye.
Some of online stegano decoder for music:-
https://steganosaur.us/dissertation/tools/audio

# Text
Use http://www.spammimic.com/ that can decode hide message in spam text.

# PDF
PDF
qpdf
PDFStreamdumper
pdfinfo
pdfcrack
pdfimages
pdfdetach
pdf-parser.py -v <file>
pdftotext
peepdf -if <filename>
object <value>
pdfid


# StegCracker
https://github.com/Paradoxis/StegCracker
Don't ever forget about steghide!(http://steghide.sourceforge.net/) This tool can use a password list like rockyou.txt with steghide. SOME IMAGES CAN HAVE MULTIPLE FILED ENCODED WITH MULTIPLE PASSWORDS.

# stegbrute
https://github.com/Va5c0/Steghide-Brute-Force-Tool This is similar to stegcracker above.

https://github.com/Rajchowdhury420/CTF-CheatSheet#steganography




# File Carving 
Try file carve using foremost -v [filename]  command. Foremost support all files