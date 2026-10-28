``` bash
john [options] [file path]

--wordlist=[path to wordlist]
--rule=[rule]
--format=raw-md5

john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt 

# Linux pw
unshadow /etc/passwd /etc/shadow > hash.txt

# Single Crack Mode: hash in format "joker:7bf6d9bb82bed1302f331fc6b816aada"
john --format=raw-md5 --single hash07.txt

#crack ZIP
zip2john [options] [zip file] > [output file]
# feed than in john with wordlist

# crack rar
rar2john [rar file] > [output file]

#SSh private key pw
ssh2john [id_rsa private key file] > [output file]


```