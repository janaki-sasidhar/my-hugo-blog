+++
date = '2026-11-24'
draft = false
title = 'Encrypt it first, then upload it anywhere'
summary = 'If you encrypt a file on your own machine before uploading it, the storage provider only ever holds ciphertext. A password, one command, and a tested backup are enough.'
tags = ['encryption', 'privacy', 'backup', 'cli']
categories = ['tech']
+++

Cloud storage is convenient, but a normal upload gives the provider readable files. Provider-side encryption does not change that much: the provider holds the keys, can generate previews, and can be compelled to produce the data.

The fix is to encrypt on your own machine, before the upload. After that, the provider only holds ciphertext, and the choice between Drive, Dropbox, S3, or any other storage mostly stops mattering for confidentiality.

A useful test: if a service can show you a preview of a file without asking for a password only you know, it can read that file.

## You do not need a public/private key pair

For files only you will ever open, a password is enough. Key pairs solve a different problem: letting other people encrypt data to you, or decrypting on a machine that should not hold the main secret.

Both approaches ultimately protect a randomly generated encryption key:

- A password-based tool derives protection from your passphrase using a deliberately slow key-derivation function.
- A key pair encrypts that random key to your public key, and you protect the private key with a passphrase anyway.

For a personal archive, the key pair adds a file you can lose and a process you have to manage, without adding confidentiality.

## The simple workflow: one encrypted archive

The tool I use for this is [7-Zip](https://www.7-zip.org/), which is free and available on Windows, macOS, and Linux. It turns a folder into a single AES-256 encrypted file:

```bash
7z a -p -mhe=on -mx=0 archive.7z my-files/
```

The flags matter:

- `-p` prompts for the password instead of taking it on the command line, where it would land in your shell history.
- `-mhe=on` encrypts the file names and directory structure, not just the contents. Without it, anyone can list what is inside.
- `-mx=0` skips compression. Photos, videos, and most documents are already compressed, so this avoids wasting time for almost no size saving.

Upload `archive.7z` wherever you like. To open it later, on any machine with 7-Zip:

```bash
7z x archive.7z
```

## Already have a ZIP file?

A common mistake is running `7z a ... existing.zip` expecting it to encrypt that file in place. It does not. The `a` command means "add files to an archive", so the existing ZIP is treated as the archive to update, not as a file to encrypt.

Instead, create a new encrypted archive that contains it:

```bash
7z a -p -mhe=on -mx=0 archive.7z existing.zip
```

Or, if you only want to encrypt a single file as it is, use GPG:

```bash
gpg --symmetric --cipher-algo AES256 -o existing.zip.gpg existing.zip
```

Avoid the legacy ZIP password feature (`zip -e`). That is ZipCrypto, which is weak. An AES-256 `.7z` archive with header encryption is the safer default.

## The password is the security

Anyone who downloads your encrypted file can try passwords offline, with no rate limit and no lockout. That is the whole ballgame:

- Generate a long passphrase instead of inventing a short password. Five or six random words is a good target.
- Make it unique. Never reuse your cloud account password.
- Store it in a password manager, and keep a second copy somewhere separate, such as on paper.
- Do not upload the password, a recovery note, or a hint alongside the encrypted file.

Losing the password means losing the archive. That is not a flaw in the tool; it is what makes the encryption meaningful. It does mean you have to organise recovery before you need it.

## Test before you delete anything

Before deleting the original files, verify the archive and do a real test extraction:

```bash
7z t archive.7z
```

Extract it once into a temporary folder and check that the files open. Only then remove the plaintext copies, and check that no other app has quietly backed those originals up somewhere else.

An encrypted file you have never successfully opened is not a backup yet.

## What encryption does not hide

Client-side encryption hides the contents and, with `-mhe=on`, the names inside the archive. It does not hide:

- The name of the archive file itself, so give it a neutral name.
- Its approximate size, or when you uploaded it.
- Which account uploaded it.
- The file from deletion. A locked, hijacked, or closed account can still destroy your only copy.

So keep at least one other copy, ideally on a local external drive. Encryption protects confidentiality; copies protect availability. You need both.

## When you want a live encrypted folder instead

An archive is best for a snapshot you upload once. If you want a folder that stays synced and opens like a normal drive, look at [Cryptomator](https://cryptomator.org/). It creates an encrypted vault inside a synced folder, encrypts files individually so only changes are uploaded, and shows up as a regular drive while unlocked.

That is more moving parts, though. For a one-time private backup, the single command above is enough.

## Checklist

1. Create an AES-256 encrypted archive with header encryption enabled.
2. Use a generated, unique passphrase and store it in two separate places.
3. Test the archive and extract it once before deleting any originals.
4. Give the uploaded file a neutral name.
5. Keep one additional copy somewhere independent of your cloud account.

Encrypt first, and the storage provider becomes a detail instead of a trust decision.
