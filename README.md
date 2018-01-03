# maggie-encryptedIM
Maggie P2P encrypted IM module

## Introduction
Maggie APP has a built-in encrypted IM module, which is based on PKI encryption mechanism and third-party IM service provided by *Easemob*. This project contains correlative iOS APP code and RESTful API of server in Java.

## Architecture
As a social platform with attributes of strong authentication and high privacy, Maggie has designed an **encrypted IM mechanism** to fully protect user’s privacy. 
<br/><br/>
User’s private key, which is the most important for privacy, will be generated and stored only at user’s cellphone. Private key will never be sent to server and has to be kept by user himself just like in a **block chain system**. For example, in iOS, user’s private key and certificate will kept in the Keychain, which has a higher secure level than other application storages.
<br/><br/>
Maggie will generate a symmetric key and transfer it between two users for their encrypted P2P session, using **PKI** encryption mechanism.
<br/>
<div align="center">
  <img src="https://github.com/WuShengRan/maggie-encryptedIM/blob/master/pictures/architecture.png" width = "621" height = "595" alt="EncryptedIM_Arch" />
</div>

## Encrypted IM Process
An encrypted P2P IM process is accomplished in Maggie APP as below:
<br/>
![EncryptedIM_Proc](https://github.com/WuShengRan/maggie-login/blob/master/pictures/process.png)
1.	User *A* sends a request for encrypted IM with *B*
2.	User *B* accepts the request
3.	*A* sends request to server to apply for the public key of *B*
4.	*A* gets *B*’s public key, generates a symmetric session key, and encrypts it with public key of *B*
5.	*A* signs a verification information with his private key, and send it to *B*
6.	*B* receives the encrypted session key and verification information, decrypts the session key with his private key, and verifies the signed information with *A*’s public key
7.	User *A* and *B* both enter encrypted IM and start a chat
