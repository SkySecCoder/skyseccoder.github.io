--- 

layout: post 

title: SAML Implementation Vulnerability

description: Security Flaw 

image: assets/images/pic23.jpg 

--- 

A new vulnerability class has been discovered that affects several SAML-based single sign-on(SSO) systems. This particular vulnerability can allow an attacker with authenticated access, to an existing SAML system, to trick SAML systems into authenticating as a different user. By using this vulnerability the attacker does not need to know the victim’s password and can still gain access to all the resources that are assigned to the victim via the SSO.[1]

So what is SAML SSO?

SAML(Security assertion markup language) SSO basically helps users to login to various applications by first authenticating themselves to one identity provider. This identity provider then authenticates the user to several applications that are required by the user. [2] In conclusion the user has to remember one password in order to authenticate to the identity provider, instead of remembering several passwords for each and every application. (P.S. you should never have same passwords for all your applications :P) After the identity provider has authenticated the user a SAML response signature is generated which is sent to the service provider. If the signature is valid then an ID field within the response will help identify and authenticate the specified user.

This vulnerability basically allows a malicious person to manipulate the SAML response, more specifically the response’s “NameID”, that is provided by the Identity Provider and then gain access to services that the victim user had. [1] This vulnerability uses an unexpected behaviour of XML libraries like Python’s lxml or Ruby’s REXML, which do not take comments into considerations while parsing the "NameID"(or any identifier tag specific to an identity provider) of SAML responses. Due to this unexpected extraction an attacker can pose as another user if his/her original SAML response is similar to another user's SAML response. More detail regarding this XML extraction can be found here [1]

This process is somewhat similar to getting someone else’s passport, replacing your picture with the original owner’s picture and then travelling to the original user's country as a citizen :P 

This manipulation basically relies on how the identity provider and the service provider implement the SAML responses and various XML APIs for python, ruby, etc.. If the implementation of the NameID(or any identifier tag specific to an identity provider) in the responses are favourable for the vulnerability then the malicious actor can do some modifications to his/her SAML response NameID due to which the signature would not be affected, and the actor will gain the victim’s access to resources.[1]

One use case could be a malicious contractor who was given an SSO, which limited his/her resources. Now the contractor can change his SAML response NameID so that he/she could get the resources of another user in the company who has more resources. The contractor would not even require the password for the victim employee’s SSO.

Multiple SAML systems were identified with this vulnerability and it is recommended that you update them if an appropriate upgrade has been released:
- OneLogin - python-saml - CVE-2017-11427
- OneLogin - ruby-saml - CVE-2017-11428
- Clever - saml2-js - CVE-2017-11429
- OmniAuth- saml - CVE-2017-11430
- Shibboleth - CVE-2018-0489
- Duo Network Gateway - CVE-2018-7340

<b>References</b>

[1] Duo Labs. “Duo Finds SAML Vulnerabilities affecting multiple implementations”; retrieved from https://duo.com/blog/duo-finds-saml-vulnerabilities-affecting-multiple-implementations
[2] OneLogin. “Dev Overview of SAML”; retrieved from https://developers.onelogin.com/saml


