# ViA | KI1 | Informācijas sistēmu drošības inženierija (ISDI)

# EXERCISE 1 - Explore GnuPG

OS : Ubuntu

## Uzstāda GnuPG
```
sudo apt-get update
sudo apt-get install gnupg
```

## Uzģenerē un nokonfigurē savu GPG atslēgu pāri - aris.aldins@gmail.com
```
gpg --full-generate-key
```

```
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1

RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096

Please specify how long the key should be valid.
        0 = key does not expire
     <n>  = key expires in n days
     <n>w = key expires in n weeks
     <n>m = key expires in n months
     <n>y = key expires in n years
Key is valid for? 1y
Key expires at [date 12 months from today]
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Aris Aldins
Email address: aris.aldins@gmail.com
Comment: 
You selected this USER-ID:
    "Aris Aldins <aris.aldins@gmail.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
You need a Passphrase to protect your secret key.

Enter passphrase:
Repeat passphrase:
```

```
gpg: key ABCD1234 marked as ultimately trusted
gpg: directory '/home/username/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/username/.gnupg/openpgp-revocs.d/ABCD1234.rev'
public and secret key created and signed.
```

## Eksportē publisko atslēgu un dalās ar personu/-ām, starp kurām to izmantos
```
gpg --export -a "Aris Aldins" > public_key.asc
```

## Importē publisko atslēgu no personas, ar kuru sazināsies - aris.aldins@va.lv
```
gpg --import otra_public_key.asc
```

## Izveido teksta ziņu un šifrē to ar otra publisko atslēgu
```
echo "Cau, si ir svariga zina!" > message.txt
```

```
gpg --output message.txt.gpg --encrypt --recipient aris.aldins@va.lv message.txt
```

## Atšifrē saņemto ziņu ar privāto atslēgu
```
gpg --output message_decrypted.txt --decrypt message.txt.gpg

```


# EXERCISE 2 - Harden SSH Security

## 1. Konfigurē Timeout Interval
```
sudo nano /etc/ssh/sshd_config
```
```
ClientAliveInterval 300
ClientAliveCountMax 0
```
```
sudo systemctl restart sshd
```

## 2. Limitē SSH pieeju tikai Whitelist lietotājiem
```
sudo nano /etc/ssh/sshd_config
```
```
AllowUsers userA userB userC userD
```
```
sudo systemctl restart sshd
```

## 3. Atslēdz Root loginu
```
sudo nano /etc/ssh/sshd_config
```
```
PermitRootLogin no
```
```
sudo systemctl restart sshd
```

## 4. Konfigurē SSHd uz izvēlēta porta - 2222, atļauj to firewallā
```
sudo nano /etc/ssh/sshd_config
```
```
Port 2222
```
```
sudo ufw allow 2222/tcp
```
```
sudo systemctl restart sshd
```

## 5. Izveido Public/Private Keys priekš autentifikācijas
```
ssh-keygen -t rsa -b 4096 -C "aris.aldins@gmail.com"

```
```
ssh-copy-id -i ~/.ssh/id_rsa.pub aris@95.68.18.10

```
```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```


## 6. Izslēdz autentifikāciju ar parolēm, piespiežot izmantot atslēgas
```
sudo nano /etc/ssh/sshd_config
```
```
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM no
```
```
PubkeyAuthentication yes
```
```
sudo systemctl restart sshd
```


## 7. Uzstāda 2FA ar Google Authenticator PAM 
```
sudo apt-get install libpam-google-authenticator
```
```
google-authenticator
```
```
sudo nano /etc/pam.d/sshd
```
```
auth required pam_google_authenticator.so
```
```
sudo nano /etc/ssh/sshd_config
```
```
ChallengeResponseAuthentication yes
```
```
sudo systemctl restart sshd
```


## 8. Bloķē IP pēc 3 neveiksmīgiem autentifikācijas mēģinājumiem izmantojot iptables
```
sudo apt-get update
sudo apt-get install iptables iptables-persistent
```
```
sudo nano /usr/local/bin/ssh-block.sh
```
```
#!/bin/bash

iptables -F
iptables -X

iptables -N SSH_CHECK

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j SSH_CHECK

iptables -A SSH_CHECK -m recent --name sshattack --update --seconds 60 --hitcount 3 -j LOG --log-prefix "SSH brute force attempt: "
iptables -A SSH_CHECK -m recent --name sshattack --update --seconds 60 --hitcount 3 -j DROP

iptables -A SSH_CHECK -m recent --name sshattack --set -j ACCEPT
```
```
sudo chmod +x /usr/local/bin/ssh-block.sh
```
```
sudo /usr/local/bin/ssh-block.sh
```
```
sudo sh -c "iptables-save > /etc/iptables/rules.v4"
```
```
sudo systemctl enable netfilter-persistent
sudo systemctl start netfilter-persistent
```

# EXERCISE 3 - Explore SMTP Vulnerabilities

## risinajums 1
```
123
```


# EXERCISE 4 - Network Tunnels (using Netcat)

## 1. Tunelis no Windows uz Linux
### Ielādē un uzstāda Netcat uz Win, direktorijā C:\netcat
### Uzstāda Netcat uz Linux
```
sudo apt-get install netcat
```
### Palaiž Netcat listener uz Linux specifiskam portam (5000)
```
nc -l -p 5000
```
### Win CMD iet uz Netcat direktoriju
```
cd C:\netcat
```
### Iniciē konekciju uz Linux hosta IP un portu
```
nc <192.168.1.100> 5000
```

## 2. Tunelis no Linux uz Windows
### Palaiž Netcat listener uz Windows specifiskam portam (5000)
```
cd C:\netcat
```
```
nc -l -p 5000 -v
```
### Iniciē konekciju uz Windows hosta IP un portu
```
nc <95.68.18.10> 5000
```

## 3.1. Ziņu apmaiņa
### Sūta ziņu no Linux
```
echo "Si ir svariga zina!" | nc <95.68.18.10> 5000
```
### Windows saņem ziņu
```
Si ir svariga zina!
```
### Sūta ziņu no Windows
```
echo Si ir svariga zina! | nc <192.168.1.100> 5000
```
### Linux saņem ziņu
```
Si ir svariga zina!
```

## 3.2. Faila pārsūtīšana
```
123
```
## 3.3. Attālināta administrēšana
```
123
```
## 3.4. Pieslēgšanās hostam aiz NAT
```
123
```
## 3.5. Spawn a reverse shell without Netcat
```
123
```
## 3.6. Spawn a reverse shell without Netcat
```
123
```





