# GitHub SSH Key Setup Guide for MacOS

This repository contains a step-by-step tutorial on how to **reset old SSH keys and create a new SSH key** for GitHub on macOS. This can be used as documentation for GitHub repositories to ensure secure SSH access.

## Table of Contents

* [Overview](#overview)
* [Step 1: Remove Old SSH Keys](#step-1-remove-old-ssh-keys)
* [Step 2: Generate a New SSH Key](#step-2-generate-a-new-ssh-key)
* [Step 3: Start SSH Agent and Add Key](#step-3-start-ssh-agent-and-add-key)
* [Step 4: Add SSH Key to GitHub](#step-4-add-ssh-key-to-github)
* [Step 5: Test SSH Connection](#step-5-test-ssh-connection)

## Overview

This tutorial helps you set up a clean SSH environment, remove old keys, and configure a new SSH key for GitHub to enable secure connections for git operations.

## Step 1: Remove Old SSH Keys

Run these commands as your normal macOS user (not root):

```bash
# Stop the ssh-agent
eval "$(ssh-agent -k)"

# Remove old keys from ssh-agent
ssh-add -D

# Remove old key files
rm -i ~/.ssh/id_*

# Optional: Remove known_hosts
rm -i ~/.ssh/known_hosts
```

## Step 2: Generate a New SSH Key

Replace `your_email@example.com` with your real GitHub email:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Press Enter to accept the default filename.
* Optionally set a passphrase.

## Step 3: Start SSH Agent and Add Key

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

## Step 4: Add SSH Key to GitHub

1. Copy your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

2. Go to [GitHub → Settings → SSH and GPG keys](https://github.com/settings/keys)
3. Click **New SSH key**, paste the key, and save it.

## Step 5: Test SSH Connection

```bash
ssh -T git@github.com
```

You should see:

```
Hi <your-username>! You've successfully authenticated, but GitHub does not provide shell access.
```

✅ Your SSH key setup is complete!



git remote add origin git@github.com:x/x.git
git branch -M main
git push -u origin main
