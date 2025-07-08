# Sending and storing secret data and messages securely

Some of us have the desire or necessity to store things in the cloud or send sensitive information or messages to other people, but this comes at a risk of security and privacy, as most likely we don't use any services that are hosted by ourselves, our friends or other people of trust.

Thankfully, regardless of the platform or service, there is a way to send and store secret information. This method relies on encryption, but the trick is in how you do it. There are several other methods of secret communication such as PGP clients, but this guide will focus primarily on using symmetric encryption with 7zip instead.

## The core idea

To obfuscate information we use encryption, and we can symmetrically encrypt files for this. With symmetric encryption, the key or password you use for encryption is the same for decryption. With a strong encryption algorithm and a very strong password, third parties cannot decrypt your file through brute force or dictionary attacks, they will require your key/password.

## Storing files safely

My general method for **storing data for yourself** is as follows:

* Generate or make up a strong password and keep it somewhere safe, preferably a password manager database
* Encrypt your file(s) using this password, with a safe and reliable encryption method such as AES-256
* The file is now safe, you can store it on a local external disk or in the cloud
  * Normally, cloud storage cannot be trusted for storing sensitive information, but with strong encryption this is no longer the problem
  * Regardless it's always preferred if you use a cloud service that encrypts your storage such as Mega

## Sending files safely

My general method for **sending data to other people** is as follows:

* Get 3 different platforms that both you and the other person can use
* Generate or make up a strong password and keep it somewhere safe, preferably a password manager database
  * For text messages, you can save the message in a file then encrypt it, or use a PGP client instead of my method
* Encrypt your file(s) using this password, with a safe and reliable encryption method such as AES-256
* Store it in the cloud or wherever else that is best for you
* On a second platform, send/store the decryption key/password
* On a third platform, send the link to the encrypted file

It is important that the encrypted file, password and link are posted in 3 different platforms, or at the very least have the file in a different place than the password and link. Each platform only has 1 component for the full decryption but the 3 are required: One has the file but no decryption key, one has the link but does not have the file directly nor the key, and one has the key but no file or link.

## Using 7zip for file encryption

7zip is extremely useful for symmetric file encryption with its archive capabilities as well as AES-256 and header encryption. It excells over Zip for being able to encrypt the header, and so filenames and paths are encrypted as well for full secrecy. The 7zip GUI is intuitive enough but it is a Windows-only interface and does not have the full power and flexibility of the CLI.

Here's an example of a 7zip command for file or directory encryption:

```
7z a EncryptedFiles.7z /path/to/directory -mhe -pENCRYPTIONPASSWORD
```
The argument "a" tells 7zip to create a new archive or add files to the archive if it already exists. It is then followed by the name or path of the archive and the name/path of the files and directories.

The argument -mhe enables header encryption, for obfuscating filenames and paths inside the archive.

The argument -p defines the password and enables encryption (AES-256 by default). Replace "ENCRYPTIONPASSWORD" with the password you want to use. If the password has spaces, include this argument inside quotation marks: "-pENCRYPTION PASSWORD"
