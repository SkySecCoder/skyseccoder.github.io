---
layout: post
title: Why isn't cryptography readily accepted by general users?
description: General security
image: assets/images/pic27.jpg
---

The main point of cryptography is to destroy the usability of unauthorised individuals while at the same time make it usable to authorised users. Unfortunately this is true only when the authorised users use cryptography or any other security control in general. How eagerly or regularly does a user use these controls depend on the control’s ease of use, productivity(in terms of throughput and speed) and need of security for the user.

Sometimes the security controls are perceived to be a hinderance rather than an asset to a user, either because they have to perform extra steps, the steps to be performed are not easy, the steps are convoluted/difficult to perform or the steps take a lot of time to be performed.

If we had to perform extra steps like explicitly/manually encrypt traffic whenever we want to use http to communicate with the server, then https would not have been widely adopted and used. Since https is implemented automatically and end-users don’t have to think much of it, it is easy and widely used.

Users must use complicated and long passwords in order to properly secure their systems against brute force and unauthorised access, but since these kinds of passwords are not easy to remember, easier/shorter/brute forcable passwords are used by users.

If we want to exchange messages with another person and want to use a CA(Certification Authority) to make sure that we are talking to the correct person, then this process involves finding a CA, getting/installing a certificate, use the certificate and implement proper protocols to implement such a process. These steps are extremely convoluted and can intimidate a new user from even considering such a secure means of communication.

Due to these usability issues there are ramifications to information assurance in general. Because the users are not using the security controls then it can lead to the IA tenets to be compromised which in turn can lead to damages to a company or an entity. It can also lead to a security control to be not adopted by enough individuals, for it to be a widespread and unified control. 

Another example of a ramification was the failing of PEM(Privacy Enhanced Mails) that was used to secure text emails using certificate. CAs policy guaranteed the uniqueness of names but it was never adopted as users found email addresses more convenient than X.500 names.

In conclusion, if security is not easy to use then it will not be adopted by a user which can lead to the compromise of several IA tenets and the discontinuation of the security control. It is the duty of a security professional to understand the working of their company, accomodate users from all areas within the company, understand security from the perspective of an end user(customer), while at the same time ensure that critical data and infrastructure is secure.