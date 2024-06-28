OpenPGP encryption and signing tool.

generate new key: `gpg --gen-key`, will initiate a short dialog to generate a key-pair using default parameters. This also called: `--generate-key`
keys location: *~/.gnupg*

[How to generate a key for github](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)

### Display public key
List keys: `gpg --list-secret-keys --keyid-format long`
Example output:
```shell
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
```
If there's an existing GPG key pair and you want to use it to sign commits and tags, you can display the public key using the following command, substituting in the GPG key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`. So execute: `gpg --armor --export 3AA5C34371567BD2`
This will show the key in ASCII armor format.
