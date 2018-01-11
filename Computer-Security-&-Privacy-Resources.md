## Password Managers

A password manager keeps track of the various passwords you use for different websites. (And the reason to use a different password for each account, is so that if your password at one place is compromised, it does not affect your other accounts.)

* Commonly recommended password managers are [Lastpass](www.lastpass.com) and [1password](1password.com).
* Lastpass has a free option, but will only sync passwords across similar device-types (e.g. between computers, or between smartphones), but not between computer and smartphone. Paid plans for Lastpass start at $2/month.
* 1password seems to have a nicer interface, but plans start at $2.99/month.
* The common usage for password managers is as browser plug-ins that can remember passwords, generate new random passwords, and autofill.
* Both Lastpass and 1password have secure notes, which allow you to keep track of answers to security questions, in case you want to generate random responses rather than use the middle school you went to, which anyone can look up.
* Apple's iCloud Keychain is another option if you have all Apple devices. Here's a [discussion](https://www.macworld.com/article/3060630/ios/why-not-pick-keychain-instead-of-1password-or-lastpass.html) on the differences with third-party password managers.

### Passphrases

Since the password managers are secured by a single master passphrase (that unlocks all your passwords), it is recommended that you use a strong passphrase.
* One method is to string together random words, possibly with capitalization and special characters added.
* Rather than use a website for this (who knows if it is truly random or recording the output it gives you), you can use [dice and a word list](https://www.eff.org/dice).
* While trying to memorize the passphrase, you might consider having a written copy that you keep somewhere safe.

## Two-Factor Authentication

Two-factor authentication (commonly 2FA or MFA for multi-factor) means identifying yourself using components from at least two different categories:
* something you know (e.g. a password)
* something you have (e.g. a key or phone)
* something you are (e.g. fingerprints, biometrics)
Thus, if someone else has your password, they still can't access your account without e.g. your phone, too.

* Many large sites (e.g. banks, email) with security concerns have 2FA as an option, but it might need to be turned on. For example, here are the instructions for [gmail](https://www.google.com/landing/2step/).
* Common implementations are to send a code by email or text when you log in.
* Some places also support apps or devices that generate rolling codes (e.g. [Google Authenticator](https://support.google.com/accounts/answer/1066447?co=GENIE.Platform%3DAndroid&hl=en)). These generate rolling codes that rotate regularly, for example, every minute. When synced up with a website during 2FA setup, you can also use the rolling code to authenticate.
* Hardware tokens are also possible, for example [Yubikeys](https://www.yubico.com/products/yubikey-hardware/). You will want to check compatibility with services. For instance, the basic U2F key will not work as 2FA for Lastpass, and you also need a paid Lastpass plan.

## Privacy


## Misc.