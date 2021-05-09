
# Why This Application ?
As our online presence is increasing we are putting more and more of our private
information on net, most of that information is for specific person or entity but
we can’t be sure that our privacy is protected from the platform we share that
information on. For example the new Whatsapp privacy policy allowed whatsapp
to share our metadata with facebook.


# PROPOSED METHODOLOGY
* We have implemented our entire application in Java and Python using Android
Studio and Jupyter Notebook. We have implemented two cryptography algorithm
namely RSA and AES. We have also implemented Quantum Key Distribution
Protocol using Qiskit library and IBM’s quantum computer.

* As we know AES uses symmetric key encryption so we need to exchange key
physically or on some other channel that may not be secure, therefore we have
proposed a communication protocol that uses QKD to distributed the key among the
sender and receiver which can be further use as a symmetric key for AES encryption
or decryption.

* RSA uses asymmetric key encryption in which there are two keys, public and private.
The problem was to distribute the public key among users, so what we have done is
created an account of every user and stored their pubic keys and email ids in a
realtime database. So whenever sender wants to send a message to a specific user the
application retrieve the public key from the realtime database and use that for
encryption also the private key of the user is safe on their device therefore the
communication is secure.


# ALGORITHMS USED
## RSA Algorithm

* RSA (Rivest–Shamir–Adleman): is an algorithm used by modern
computers to encrypt and decrypt messages. RSA algorithm is asymmetric
cryptography algorithm. Asymmetric actually means that it works on two
different keys i.e. Public Key and Private Key. As the name describes that
the Public Key is given to everyone and Private key is kept private.
* The idea of RSA is based on the fact that it is difficult to factorize a
large integer. The public key consists of two numbers where one number is
multiplication of two large prime numbers. And private key is also derived
from the same two prime numbers. So if somebody can factorize the large
number, the private key is compromised. Therefore encryption strength
totally lies on the key size and if we double or triple the key size, the
strength of encryption increases exponentially. RSA keys can be typically
1024 or 2048 bits long, but experts believe that 1024 bit keys could

![RSA_Algo](https://user-images.githubusercontent.com/63945098/117587371-3f698980-b13b-11eb-8594-c0ce91e43266.png)


## AES Algorithm
* AES includes three block cipher: AES-128, AES-192 and AES-256.
AES-128 uses a 128-bit key length to encrypt and decrypt a block of
messages, while AES-192 uses a 192-bit key length and AES-256 a 256-bit
key length to encrypt and decrypt messages. Each cipher encrypts and
decrypts data in blocks of 128 bits using cryptography keys of 128, 192 and
256 bits, respectively.
* Symmetric, also known as secret key, ciphers use the same key for
encrypting and decrypting, so the sender and the receiver must both know --
and use -- the same secret key. The government classifies information in
three categories: Confidential, Secret or Top Secret. All key lengths can be
used to protect the Confidential and Secret level. Top Secret information
requires either 192- or 256-bit key lengths.
* There are 10 rounds for 128-bit keys, 12 rounds for 192-bit keys and 14
rounds for 256-bit keys. A round consists of several processing steps that
13include substitution, transposition and mixing of the input plaintext to
transform it into the final output of ciphertext.
* The AES encryption algorithm defines numerous transformations that are to
be performed on data stored in an array. The first step of the cipher is to put
the data into an array -- after which, the cipher transformations are repeated
over multiple encryption rounds.
* The first transformation in the AES encryption cipher is substitution of data
using a substitution table; the second transformation shifts data rows, and the
third mixes columns. The last transformation is performed on each column
using a different part of the encryption key. Longer keys need more rounds
to complete.

![AES_Algo](https://user-images.githubusercontent.com/63945098/117587315-e863b480-b13a-11eb-9a3d-410d513413b0.png)


# Overall Design(Flowchart)
## User Login/Signup
* Used firebase for authentication and user login using google account.
## RSA
#### Distribution of Public key
* When a user logs in, the application will create his/her unique id and
store that id with thier corresponding public key in the realtime database
hosted using firebase.
#### Encryption Of The Text Message
* The user is asked to enter the receiver’s email ID, the application first
search for the receiver’s email in the database and verify it.
* Then if email exists, it will retrive the receiver’s public key from the
database.
* Then the user is asked to enter the message that user wants to encrypt.
* After that the message will be encrypted using the retrieved public key
and the user can copy or share the cipher text on a less secure
communication channel.
#### Decryption Of The Text Message
* The user is asked to enter the cipher text which he/she recieved from a
less secure communication channel.
* The cipher text will be decrypted using the private key of the user.
## Quantum Key Distribution Protocol
* Protocol designed to share the key among sender and receiver using
concepts of quantum computing and quantum cryptography.
## AES
#### Key Distribution Using Quantum Key Distribution (QKD)
* User will be asked to enter receiver’s email id.
* The application will generate a key that will be distributed among sender
& receiver using QKD protocol through the quantum channel.
#### Encryption Of Message
* Then the user is asked to enter the message that user wants to encrypt.
* After that the message will be encrypted using the key generated using
QKD protocol and the user can copy or share the cipher text on a less
secure communication channel.
#### Decryption Of The Text Message
* The user is asked to enter the cipher text which he/she recieved from a
less secure communication channel.
* The cipher text will be decrypted using the key of the user.

![Overall](https://user-images.githubusercontent.com/63945098/117587343-1ea13400-b13b-11eb-9358-998bb9ebe1cf.png)
