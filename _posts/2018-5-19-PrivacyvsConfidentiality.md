---
layout: post
title: What is the differnce between Privacy and Confidentiality?
description: General security
image: assets/images/pic26.jpg
---

In order to differentiate between confidentiality and privacy, let us first define them individually.

When we say that some information is confidential, we basically mean that the information must be “held in confidence”. This means that the information can be shared with other individuals, provided that the information owner/authorized individual has authorized the other individual to that information. Also the other individual is expected to not share that information unless authorized by appropriate individuals. This basically means that confidential information cannot be shared as pleased, appropriate individuals must authorize the share to individuals who must maintain its secrecy. 

Privacy on the other hand is a Constitutional right, unlike confidentiality, that is specified as “The Fourth Amendment”, in the US Constitution. Privacy is a right of an individual to keep certain information to themselves and not be forced to divulge that information.

Here we see the distinction quite clearly. Privacy is a right of an individual whereas confidentiality is not a right, information can be shared with others and is more focused on the information, rather than an individual.

Cryptography enables privacy, as an individual can encrypt a piece of information with a key such that only he/she can use the key to encrypt/decrypt the data. This way ensures that only the individual who has the key can access the private information (unless the encryption is broken is some way). So if you were to encrypt your data with a key and store the encrypted data on a public server, then you can ensure privacy as only you have access to it via your key. If you want to give access to the encrypted data to someone else then the other person must ensure that he/she will “hold the data in confidence” and not leak the plaintext data or the key to decrypt/encrypt the data. If the other individual does not “hold the data in confidence”, then the data will no longer be confidential. In order to share the data the key must be shared with the other person who will “hold the data in confidence”. The other person can simply access the data by decrypting the data in context. Now this key(assuming symmetric key encryption was used) can be shared in several ways i.e. by writing it down and sharing it, giving a flash drive with the the key or by using Public Key Infrastructure to share the key. In any case it must be ensured that the key must not fall in the hands of individuals, other than the authorized individuals.