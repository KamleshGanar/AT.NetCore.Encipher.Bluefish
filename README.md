# AT.NetCore.Encipher.Bluefish
The Bluefish is the modified encryption/decryption in combination of AES (Advanced Encryption Standard or Rijndael) and MD5 for One way encryption.
This package is compatible with .NetCore.

# What's in it?
The Bluefish provides the simple functionality to encrypt/decrypt the text. This works on Asymmetric Encryption Method (also called public-key cryptography) and SHA1 is default hash algorithm.
The best thing of this library is that, this is querystring compatible. It means, the encrypted value can be passed as querystring of the url and can be easily decrypted at server side.

# Nuget Package
[![NuGet versions AT.NetCore.Encipher](https://img.shields.io/nuget/AT.NetCore.Encipher.svg?style=flat-square)](https://www.nuget.org/packages/AT.NetCore.Encipher)

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

1. Encryption + Decryption: 
```
bluefish.IsDecryptable = true;
string plainText = "This is plain text";

string encryptStr001 = bluefish.Encrypt(plainText);
Console.WriteLine(encryptStr001);
string encryptStr002 = bluefish.Encrypt(plainText);
Console.WriteLine(encryptStr002);
string encryptStr003 = bluefish.Encrypt(plainText);
Console.WriteLine(encryptStr003);
```
OUTPUT:<br/>
biuYRXlaxfA_Y5WrXcBRQySU_9ZgOFid0I1mNa5k4Vc= <br/>
e8vgCpPl0KR7Z65t2fUJOtzIqsoJOGi_RHvHxd1OFjo= <br/>
o_QP7BplJrgefTBjXxzp322yFXVLFXs18kpXmL2--JUw= <br/>

You can observe that the three output of same plain text is different hence we cannot use this encrypted string for comparision or matching.

Decrypte the above values
```
Console.WriteLine("encryptStr001: " + bluefish.Decrypt(encryptStr001));
Console.WriteLine("encryptStr002: " + bluefish.Decrypt(encryptStr002));
Console.WriteLine("encryptStr003: " + bluefish.Decrypt(encryptStr003));
```
OUTPUT:<br/>
encryptStr001: This is plain text <br/>
encryptStr002: This is plain text <br/>
encryptStr003: This is plain text <br/>

The decryptable is true hence the encrypted string can be revert back and get the original text. 

2. One way Encryption (Non-Decryptable)
```
bluefish.IsDecryptable = false;
string encryptedStr_001 = bluefish.Encrypt(plainText);
string encryptedStr_002 = bluefish.Encrypt(plainText);
Console.WriteLine(encryptedStr_001);
Console.WriteLine(encryptedStr_002);
```
OUTPUT:<br/>
88-2D-37-D6-5A-CC-23-DE-E2-52-DF-22-7A-8B-B2-C7 <br/>
88-2D-37-D6-5A-CC-23-DE-E2-52-DF-22-7A-8B-B2-C7 <br/>

The encrypted string of two variables are same but cannot decrypt. Hence we can use this to compare the encrypted string.

