# AT.NetCore.Encipher.Bluefish
The bluefish is the modified encryption/decryption in combination of AES (Advanced Encryption Standard or Rijndael) and MD5 for One way encryption.
This package is compatible with .NetCore 2.2.

# What's in it?
The Bluefish provides the simple functionality to encrypt/decrypt the text. This works on Asymmetric Encryption Method (also called public-key cryptography) and SHA1 is default hash algorithm.
The best thing of this library is that, this is querystring compatible. It means, the excrypted value can be passed as querstring the url and can be easily decrypted at server side.

# Nuget Package
Download the AT.NetCore.Encipher.Bluefish library. 
[![NuGet version (AT.Common)](https://img.shields.io/nuget/v/AT.Common.svg?style=flat-square)](https://www.nuget.org/packages/AT.Common/)

# Example
``` dotnet
Bluefish bluefish = new Bluefish(passPhrase, initVector);
```
By default the encrypted string/text is decryptable. User can make it non-decryptable in two ways:
```
Bluefish bluefish = new Bluefish(passPhrase, initVector, false);
```
```
bluefish.IsDecryptable = false;
```
