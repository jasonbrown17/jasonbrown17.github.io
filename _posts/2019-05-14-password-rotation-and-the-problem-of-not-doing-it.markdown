---
layout: post
title:  "Password Rotation and the Problem of Not Doing It"
date: "2019-05-14 00:00:00 -0400"
categories: Passwords Privacy Security
featured_image: "/images/blog/access-control-lock.png"
---

![Password Pad Lock](/images/blog/access-control-lock.png)

Since the release of NIST SP 800-63-3 I have been asked, “Why does our company still perform password rotation?” This question is easier said than done. It is one that requires user awareness training, implementation of auditing and alerting software, and most importantly – multifactor authentication. All of which are necessary, though it can take months to years to implement depending on a companies resources and regulatory requirements.

#### User Awareness

We still seem to be failing at user awareness training. Our parents, grandparents, kids, co-workers, and yes even us still use easily guessable passwords. Studies have shown that for the past 5+ years the top passwords being used on the internet are, “123456”, “password”, “qwerty”, and “111111.” Talk show host Jimmy Kimmel and his television crew have shown how easy it is to social engineer someone to give up their password. These episodes also show the simplicity of the password with some saying their password is a pets name and a birth date.

Companies such as Microsoft have developed ways to prevent its users from picking simplistic passwords. With its new, “Password Protection for Azure AD” service, it prevents users from creating easily guessable passwords. This is performed by Microsoft’s massive database of commonly used passwords. If a user were to pick a password that was found in the database, the service presents an error message and the user must pick another one.

#### Auditing and Alerting Software

People often make mistakes, that is a given. Companies make similar mistakes as well. Facebook recently announced that the company was storing user passwords in clear text. What can be worse than that you ask? That database had been queried over 9 million times by Facebook staff. Facebook has been on the defensive stating that this was not a breach. While technically no it was not a breach, it shows how lacking they are in their security and privacy.

There are similar cases where companies lax in their security policies. It certainly opens the question of how we can protect ourselves online. With users picking easily guessable passwords, and the reuse of those passwords, auditing and alerting tools are a necessity. Organizations need tools in place to be able to send alerts when an account is being brute forced. They also need to alert when someone is logging in from a country where there is no organizational presence. These are key indicators of account takeovers. Without this in place, a security operations team will never know if an account has been compromised.

#### Multifactor Authentication

Multifactor (also known as 2 factor) is defined as:

* Something you have  
* Something you know  
* Something you are  

To suffice this definition, one must utilize two of the three listed. Something you have and something you are is the most common. How does this protect against account take overs? If one were to use a semi-guessable password and configured multifactor authentication, account take over would be extremely difficult to pull off. The reason is that even if someone were to have your password, that person could still not log into the account as the second factor has not been met. The second factor in most instances is something that you have. Examples of this are a smart app on your mobile device, a hardware device such as a YubiKey, or a text message. Though using text messages as a form of second factor is now highly discouraged. Without having physical access to any of these devices, it can be nearly impossible to log into an account. There is a website dedicated to help in configuring multifactor authentication by heading on over to [Two Factor Auth][two-factor]. This website will show you which popular online services allow for multifactor authentication, and if they do not, you are able to send a message to the service asking them to enable it.

#### Final Thoughts

Password rotation is an evil necessity without properly thinking things through. Yes it does not prevent an account take over, however rotation will eventually keep an attacker from logging in. The use of multifactor authentication, auditing and alerting, coupled with user awareness training are essential to good password hygiene. Without these in place, the organization will be stuck on rotation – like a broken record.

[nist]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-3.pdf
[azure]: https://redmondmag.com/articles/2019/04/02/password-protection-azure-ad.aspx
[facebook]: https://www.pcmag.com/news/367319/facebook-stored-up-to-600m-user-passwords-in-plain-text
[two-factor]: https://twofactorauth.org/
