# Notes about TLS, PKI, certs and keys.

## Everything you should know about certificates and PKI but are too afraid to ask

Good read 😊 by SmallStep

[https://smallstep.com/blog/everything-pki/](https://smallstep.com/blog/everything-pki/)

## Fun facts

PEM stands for Privacy Enhanced Email. It was originally developed to encrypt emails.
It never cought on, though, and the related RFC's were eventually obsoleted by PGP and S/MIME.

## Step CLI

Similar to `openssl` but with better UX.
[https://github.com/smallstep/cli](https://github.com/smallstep/cli)

## ssh-rsa

* [Deprecated by OpenSSL](https://lists.mindrot.org/pipermail/openssh-unix-announce/2020-February/000138.html)
  > It is now possible[1] to perform chosen-prefix attacks against the
  > SHA-1 algorithm for less than USD$50K. For this reason, we will be
  > disabling the "ssh-rsa" public key signature algorithm by default in a
  > near-future release.

* [Blocked in Fedora Linux 33](https://www.reddit.com/r/Fedora/comments/jhxbdh/no_ssh_public_key_auth_after_upgrade_to_fedora_33/)

* Solution: Switch SSH keys to Eliptic Curve ed25519

  * Problem: [Azure DevOps only supports legacy ssh-rsa](https://developercommunity.visualstudio.com/t/support-non-rsa-keys-for-ssh-authentication/365980)
    [Round 2](https://developercommunity.visualstudio.com/t/Git-SSH-access-offers-weak-algorithms-r/1547526)

## EC cryptography for dummies

https://blog.boot.dev/cryptography/elliptic-curve-cryptography/
