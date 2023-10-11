.. SPDX-License-Identifier: CC0-1.0
.. Author: Huynh Van Tai (aka. taiprogramer)

"""""""""""""""""""""""""""""""""""""""""
Protect data with GPG (GNU Privacy Guard)
"""""""""""""""""""""""""""""""""""""""""

**Disclaimer:**
The document author has published this document with the hope that it may be
helpful to others. However, the author does not guarantee that all information
contained in this document is correct or accurate. There is no warranty,
expressed or implied, of merchantability or fitness for any purpose. The author
does not assume any liability or responsibility for using the information
contained in this document.

Date created: Oct 11 2023

====
Why?
====

- My data is important - I have a lot of things to hide :))
- No body cares about your data until they do - protect the data now.

=====================
Generate new key pair
=====================

We will generate 2 keys: public key & private key.
Public key is used for encrypting, verifying digital signatures. It can be
public and should be public, the world will use this key to encrypt the messages
before sending them to you. On the contrary, the private key is used for
decrypting, signing.

- Install **gpg**: If you're using the GNU/Linux operating system, the software
  should be available. If you're using other OSes, seek the document how to
  install gpg on these systems, make sure you can run gpg in your terminal.
- To generate new key pair:

.. code:: bash

    gpg --full-generate-key

Here is the sample output:

.. sourcecode::


    ❯ gpg --full-generate-key
    gpg (GnuPG) 2.2.41; Copyright (C) 2022 g10 Code GmbH
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Please select what kind of key you want:
    (1) RSA and RSA (default)
    ...
    Your selection? 1

    RSA keys may be between 1024 and 4096 bits long.
    What keysize do you want? (3072) 4096
    Please specify how long the key should be valid.
    0 = key does not expire
    ...
    Key is valid for? (0) 0
    Key does not expire at all
    Is this correct? (y/N) y

    GnuPG needs to construct a user ID to identify your key.

    Real name: Thomas Shelby
    Email address: tommy_shelby@us.mail
    Comment:
    You selected this USER-ID:
    "Thomas Shelby <tommy_shelby@us.mail>"

    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O

**gpg** should ask you the password for encrypting the private key. Make sure to
use the **strong** password.

Notice the USER-ID, we will use it later "Thomas Shelby <tommy_shelby@us.mail>"

======================
Encrypt/Decrypt a file
======================

You can encrypt/decrypt any type of files (it's just a file). I'll demonstrate
with a text file (universal interface).

Create a new text file with your message

.. code:: bash

    cat > for-my-tester.txt << EOT
    I like you a lot. I want to be part of your life, I want to share everything
    I have, I want to protect you. From now on, you're protected by the order of
    the Peaky Blinders.
    EOT

Encrypt the file for 1 recipient (Thomas Shelby <tommy_shelby@us.mail>)

.. code:: bash

    gpg --encrypt --recipient tommy_shelby@us.mail for-my-tester.txt

After the command finishes, you'll see the new .gpg file (that's your encrypted
file).

To decrypt an encrypted file

.. code:: bash

   gpg --decrypt --output for-my-tester.new.txt for-my-tester.txt.gpg

**gpg** will ask you for the passphrase of the private key. After the command
finishes, you'll see the file named for-my-tester.new.txt (that file contains
the original content).

====

This document is licensed under the Creative Commons Zero v1.0 Universal.

Examples, recipes, and other code in this document are additionally licensed
under the Unlicense.

