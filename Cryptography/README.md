# Cryptography
## Scrumbled and encrypted text

 There are a lot cryptography tools online. Some of good tool are made offline like OpenSSL.
Classic cipher / Simple decoder online tool
https://quipqiup.com - quipqiup is a fast and automated cryptogram solver
https://www.base64decode.org/ - base64 decoder
https://www.urldecoder.org/ - URL decoder
https://emn178.github.io/online-tools/base32_decode.html -  Base32 decoder
https://cryptii.com/ - All in one tool
https://www.guballa.de/substitution-solver - Substitution solver
https://www.guballa.de/vigenere-solver - Vigenere solver
https://rot13.com/ - Rot 1 - 25 decryptor
https://www.dcode.fr -  All in one tool
http://rumkin.com/tools/cipher/ -  All in one tool
http://www.unit-conversion.info/texttools/morse-code/ - Morse code decoder
https://cryptii.com/pipes/ascii85-encoding - ASCII85 decoder
https://github.com/Ciphey/Ciphey -Ciphey
Modern cryptography
https://gchq.github.io/CyberChef/ - All in one tool
https://crackstation.net/ - Crack hash
Cryptool
John the Ripper 
Hashcat
OpenSSL cheatsheet
Decrypt a file using RSA private key
openssl rsautl -decrypt -inkey pub_priv.key -in ciphertext.file -out decrypted.file
Decrypt a file using AES-256-CBC and a keyfile
openssl enc -d -aes-256-cbc -in ciphertext.file -out cleartext.file -pass file:./key.file
Decrypt a file using AES-256-CBC
openssl enc -aes-256-cbc -d -in file.txt.enc -out file.txt
Decrypt a file using AES-256-CBC with base64 encoded
openssl enc -aes-256-cbc -d -a -in file.txt.enc -out file.txt
Others reference
https://gist.github.com/dreikanter/c7e85598664901afae03fedff308736b#file-encrypt_openssl-md
Cracking compressed file
John the Ripper - john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
fcrackzip - fcrackzip -D -u -p rockyou.txt  filename.zip

Note:
Sometimes there are some challenges that require you to develop your own decryptor for that particular challenge. Just make sure you have a good scripting/programming language to solve the challenges.