---
layout: post
title:  "Smartcard reader in Windows 10 on Mac"
date:   2018-06-04 21:05:50
categories: jekyll update
---

## Step 1: Download Windows 10 image

1. Open <https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/>
2. For "Virtual machine", select "MSEdge on Win10 (x64) Stable (17.17134)"
3. For "Select platform", select "Vagrant"

This is going to take a while.

## Step 2: Install vagrant, virtualbox and virtualbox-extension-pack

We need virtualbox-extension-pack for USB 2.0 or 3.0 support for VirtualBox

```sh
$ brew cask install vagrant virtualbox virtualbox-extension-pack
Warning: Cask 'vagrant' is already installed.

To re-install vagrant, run:
  brew cask reinstall vagrant
Warning: Cask 'virtualbox' is already installed.

To re-install virtualbox, run:
  brew cask reinstall virtualbox
Warning: Cask 'virtualbox-extension-pack' is already installed.

To re-install virtualbox-extension-pack, run:
  brew cask reinstall virtualbox-extension-pack
```

## Step 3: Download pre-configured Vagrantfile

We need the pre-configured Vagrantfile to start our VM.

```sh
$ git clone --depth=1 git@github.com:sharils/Vagrantfile.git /tmp/Vagrantfile
Cloning into '/tmp/Vagrantfile'...
remote: Counting objects: 12, done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 12 (delta 2), reused 7 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), 14.14 KiB | 14.14 MiB/s, done.
Resolving deltas: 100% (2/2), done.
```

## Step 4: Add "MSEdge on Win10 (x64) Stable (17.17134)" image to Vagrant

Unzip first if this doesn't work.

```sh
$ vagrant box add --name "Microsoft/EdgeOnWindows10" <path to the downloaded image file>
```

## Step 5: Start the VM

```sh
$ vagrant up
```

## Step 6: Map your smartcard reader through into the "MSEdge on Win10 (x64) Stable (17.17134)" VM

1. Open VirtualBox
2. Click your Windows 10 VM
3. Click the Machine menu item on the top
4. Move to Close
5. Click Power Off
6. Click the Machine menu item on the top
7. Click Settings...
8. Click Ports
9. Click USB
10. Check Enable USB Controller
11. Select USB 2.0 (EHCI) Controller
12. Click the second Add new USB filter button
13. In the popup menu, select your USB smartcard reader
14. Click OK
15. Click Start

## End

Now your smartcard reader should be accessible from your Windows 10 VM
