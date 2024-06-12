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

## Atšifrē ziņu ar privāto atslēgu
```
gpg --output message_decrypted.txt --decrypt message.txt.gpg

```


# EXERCISE 2 - Harden SSH Security

## Uzstāda virtualenv
```
123
```


# EXERCISE 3 - Explore SMTP Vulnerabilities

## Uzstāda virtualenv
```
123
```


# EXERCISE 4 - Network Tunnels (using Netcat)

## Uzstāda virtualenv
```
123
```

