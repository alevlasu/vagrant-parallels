---
page_title: "Using Packer"
sidebar_current: "boxes-packer"
---

# Using Packer

<div class="alert alert-warn">
	<p>
		<strong>Warning: Advanced Topic!</strong> If you're not familiar with
		Packer, you should read the <a href="https://packer.io/docs">
		Packer documentation</a> first.
	</p>
</div>

Packer must be properly installed in order to build a new base box using templates. 
Read the installation instruction here: [Install Packer](https://packer.io/docs/installation.html)

## Parallels Virtualization SDK

Packer requires the 'prlsdkapi' Python module from the Parallels Virtualization
SDK to interact with Parallels Desktop and virtual machines. To use Parallels 
builders for Packer you need to download and install this SDK package: 
[The Parallels Virtualization SDK for Mac](https://www.parallels.com/download/pvsdk/)

You can also install it with [Homebrew](https://brew.sh) package manager:

```
$ brew cask install parallels-virtualization-sdk
```

## Packer Templates
Packer is shipped with `parallels-iso` builder, which can be used to create 
base Vagrant boxes for the Parallels provider.

There are two popular projects containing Packer templates for `parallels-iso` builder:

- [Bento](https://github.com/chef/bento)
- [Boxcutter](https://github.com/boxcutter/)

In Parallels we build our [official boxes](https://atlas.hashicorp.com/boxes/search?provider=parallels) 
using templates based on Bento project.

## Building a Box

This is an example how to build Vagrant box for Parallels provider:

```
$ packer build -only=parallels-iso template.json
```

Packer will done everything you need: it will download an ISO image, setup a VM, 
install Parallels Tools, make basic provisioning, and it will export the VM image
to a `*.box` file

You can read more about options which all supported template options here: 
["parallels-iso" builder documentation](https://packer.io/docs/builders/parallels-iso.html)
