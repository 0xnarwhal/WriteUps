# Scan Surprise

## Description

```text
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?

You can download the challenge files here:

challenge.zip

The same files are accessible via SSH here:

ssh -p 54525 ctf-player@atlas.picoctf.net

Using the password 1db87a14. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!
```

Upon downloading the files (or getting it from the server), we can see that it is a QR code. The first obvious is to read the QR code and see it's ASCII output.

After using some online QR code reader tool we get the following:

`picoCTF{p33k_@_b00_19eccd10}`

Solved. Flag: `picoCTF{p33k_@_b00_19eccd10}`.
