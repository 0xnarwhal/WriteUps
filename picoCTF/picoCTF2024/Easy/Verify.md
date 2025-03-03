# Verify (Easy)

## Description

```text
People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.

ssh -p 50659 ctf-player@rhea.picoctf.net

Using the password 6abf4a82. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!

Checksum: b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2

To decrypt the file once you've verified the hash, run ./decrypt.sh files/<file>.
```

## Solving

We can immediately try to do as we are told and SSH into the server and accept the fingerprint.

```bash
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.8.0-1021-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
ctf-player@pico-chall$
```

Reading `checksum.txt` we can verify that it is the same.:

```bash
ctf-player@pico-chall$ cat ./checksum.txt
b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2
```

We can also see that the folder `files` contains many files with a mix of numbers and letters. This is what we want to decrypt. We can further analyse the decrypt script.

```bash
ctf-player@pico-chall$ ls files
0QFPjDGl  4KcKU6Xa  9WLdePls  EwszjufH  JQE8B4Up  OYPSxPCM  SeCAw3kn  XQmQCztH  gKBJEwGs  ml8BheQF  sNGrPNW9  x5pSIkgV
0wKPM7Vk  4S7OA4S1  9XyOtfBh  Exys8oSP  Jq1cYZ8g  OcFa3rqO  T9fmDPnm  XmhfK5Aq  gnoyjDG7  mpB3SJWA  srFcLJ99  xTT3GfqC
10tptfxh  4l0tWwNc  9b7gQszB  EyBcl2bB  JvzvG7Vc  OhmnsfSS  TE8FU1FG  Y08kAtsE  hB16cKX4  mydpiMHQ  sx2fH87w  xkDmEj9c
119zBIIk  5Dpo5Lpk  9d8nFwcg  FAUDGtqU  JwS9q7vh  OkPLXtNq  TPG0sahr  YObSF7u7  hEGhq5DP  n1vcSeUf  tHu44y2r  yCAhbvDl
19TB8pZ3  5b3OmDaM  9sJDOYFY  FC37odB0  KCldRqWv  OonPniJj  TY6AsyPx  ZLIAqMxY  hL8N2SgO  n61Ajy0l  tNRgqUFc  yNyu2uzv
1OUKnRjk  5gbVyEtu  9wIEX6Ap  FCHv0zyb  KWhAd048  PEZRi3Qx  TaBG0B2a  ZT5qZdGA  hOTod2wC  nB8BgvEZ  tyOIINiW  yQ6gSAs0
1P1L0ygq  5oIfd9IJ  AW7wekIn  FCJb9D8b  KYU5dJBV  PTIOjUAO  TcrKRBQh  ZvqyoPUN  hv37OPgb  nEgEYBGO  u6AnP5n8  yao0qUIY
1WcKHuTD  60q4LDsH  AeWfGlLB  FVtBZjMA  KuP4CIgp  PdjdvRzf  Tmbnqy9u  aWo9YugC  hvIjwsas  nU1oL2aA  u8hC52SO  yokR4dAH
1ylhS7Z6  65hhdaTN  ApzPkEpG  FomVLBE8  L06xBBN8  PerdXdmX  Tz0v6vYA  agEHnOGT  izhGFAI2  nYYUwHcx  uEMcyj1c  yqCsXOqL
1zs9Zs50  6HSJkEvn  AxDAiV2s  FsqsVy3q  Lomzo8KF  PrXtVj8G  UB35i7KM  aoamig9W  j1UdH57T  nYqk1CS8  uPw05ctW  z28RdHqr
295tU6Ga  6SsAocNZ  BPRXW4rK  G7Jl9HbP  LpfjpjFP  Psk7CJHK  UeppfEJC  bjT6NSbK  jHDEMmlj  ngGtZvlW  uS8ThjW5  zIiqnki2
2TcWPeh8  6kiru4ve  BS2al2Fb  G8ZDeoVW  LrwcukXM  PuKmA1eP  UnO02Frc  bpIGPWgD  jIKe6Zfx  o5TDRZjh  uXM7xQLM  zQ8S4zxx
2VOltutT  7JZPNEfJ  BS3exq10  GCr8IGJ3  Lwf6P5Kj  Q99Jg4Jp  UujEEh69  c7U1KrcA  jmfr71Fv  oCABmA5i  uY6oCo6R  zTraYrZH
2p5KxTdA  7jb2Imqm  Bm8zsl99  GEcq4lun  Lz03kcSk  QDL15MCI  UzINJ2WT  cAyG03oe  k41e31GY  oLkVCEIL  ucYToezK  zVojuqQn
2pIUNmB1  7ndywIni  COSVSvXt  GSeAwi8t  MPLtzWsV  QHLGtwDe  V3VqDddi  cBV6POlr  kHJFs8HF  ojutsLQ9  uhL7kMRa  zeT6ehJv
2zYguKpI  8EQoMwiP  CUpZfKDA  GYNiwrKN  MQCiGgtX  QUSFNv4Q  V63YcFAp  cLQTUGHU  kUvLqJ4G  otrltBmC  vCDimHt8
34fINKgc  8KKJnhNd  CZAKNO37  GaLnr2As  MTVTG4gg  QVvIXef5  VDQTXMlu  cWmXM172  kgbulnT1  p44Dq1SO  vIvKsEXP
3AGK4MB5  8XAFnxGx  CcSCdqM1  H61uqmwe  MjMbgBEF  QZ5JwuqX  VEPlKaaH  cakrE5Le  kqKs9dUN  p4ngbycR  vg9T5LbS
3MI3phiM  8mDcrT5i  D5EzyM4s  HBsJejHU  N7Su3TaZ  R1hA1txm  VYprzg0m  cf4lMuNt  kzYNVanR  p9czQWyi  viE4fMXT
3VvoBZaT  8vIsQrBk  D7AhYHSs  HNkAl0Wv  NP3YFw2T  R7FAFiUX  Voj9jP6c  dDawndt3  l1I9SlrE  pZmUSlts  vu8ZQzXa
3f9IBKbV  8vPNDGew  DduIkX8T  HlXjxzfY  NPoWK5Mi  R9PUBlcL  VpCCDBvS  ddo7McIO  lJ0BQ2Wq  pmvuhDPp  w17zkUuj
3uK74LSS  8wqM09n0  DhaIB5aS  Iv7SD7gz  Nc49l2EU  RMO0PzgH  W6HJyLNP  ewYxe6yI  lLGVJakI  qLRvinCQ  wBzvlLFE
451fd69b  96lBoWaU  E5Y6zplS  IvHedMU7  Nel9Qkh9  S0ZumPXR  W6injFLn  fAijPDvG  lNCXHhQD  r8rSf0xW  wIqKXeki
4AVsbijj  98tbiuSQ  EMW8xsyg  J2C3jKRR  NqHkUxDY  SC2gThOs  Wraq7ZVn  flHrhjvC  lP1vtSZx  ro6pmtK2  wRApz452
4GLVcGAT  9Lg5sIdT  EUrDQxDU  J2taODo4  NvZsOWbG  SIFatJfR  XNYpvkxx  fmPAeitt  la1Cjzyx  rprBM8iU  wlgmaCgQ
4J715L0D  9LyIv77J  EZUfAdt0  J5TeIktX  OAqU3ZEC  SVB3p5ql  XP1tFwB7  gGs1IK8o  ld5v1JVF  rrNGwJSR  wuh7Cgbl
```

```bash
ctf-player@pico-chall$ cat decrypt.sh

        #!/bin/bash

        # Check if the user provided a file name as an argument
        if [ $# -eq 0 ]; then
            echo "Expected usage: decrypt.sh <filename>"
            exit 1
        fi

        # Store the provided filename in a variable
        file_name="$1"

        # Check if the provided argument is a file and not a folder
        if [ ! -f "/home/ctf-player/drop-in/$file_name" ]; then
            echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
            exit 1
        fi

        # If there's an error reading the file, print an error message
        if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
            echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
        fi
```

We are meant to pass in the files for the script to decrypt but it seems to be only one file to be the actual flag file. We can brute-force this by going through each file in the folder and trying to decrypt it.

I have made a script to perform this task.

```bash
#!/bin/bash
FILES=/home/ctf-player/drop-in/files/*

for f in $FILES
do
./decrypt files/${f##*/}
done
```

Within the output we can find the flag:

```bash
Error: Failed to decrypt 'files/3f9IBKbV'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3uK74LSS'. This flag is fake! Keep looking!
picoCTF{trust_but_verify_451fd69b}
bad magic number
Error: Failed to decrypt 'files/4AVsbijj'. This flag is fake! Keep looking!
bad magic number
```

Solved. Flag: `picoCTF{trust_but_verify_451fd69b}`.
