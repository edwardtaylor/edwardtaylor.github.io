---
layout: post
title: "Vagrant + Rails"
date: 2013-11-17 22:56
comments: true
categories: [vagrant, rails]
---

###Vagrant

Over the past year I've been using a Ubuntu VM image for developing all my Rails applications. I've tried installing everything on my Windows box but constantly hit odd scenarios with Gems that didn't *just work* for one reason or another. I finally gave up and switched over to a Ubuntu virtual image and everything has been much more pleasant. In addition, there's a large support group of developers also working on a similar platform so many issues are resolved by a quick search.

**Enter [Vagrant]((http://www.vagrantup.com)**

It's a god-send to RoR developers who must use Windows as their default operating system for whatever reason (e.g. Work policy, .Net projects, shared home system).

Vagrant allows you to:

> "Create and configure lightweight, reproducible, and portable development environments."

Vagrant creates a super light-weight headless virtual machine using your provider of choice (VMWare, VirtualBox, AWS). Rather than allocating a gig or more of RAM to a Ubuntu virtual image, Vagrant only requires the bare minimum of resources required for a headless operating system. Of course you can scale your virtual image up or down depending on your needs. This mixed with Rails development is a phenomenal way to quickly create development images for yourself and your colleagues.

After you have a Vagrant box up and running, a synced folder can be created between your host system and virtual image. This allows the developer to work on the host system while still writing code to the virtual image. In addition, Vagrant can forward ports from the host system to the virtual image allowing http://127.0.0.1:3000 to work like a charm.

There are lots of pre-configured boxes available for Vagrant. I found a Rails vagrant image hosted on GitHub at [https://github.com/railsmn/railsmn-dev-box](https://github.com/railsmn/railsmn-dev-box). Here are the steps I used to setup my Rails 4 environment on Windows.

###Setup Vagrant Image

1.	Download [Vagrant](http://downloads.vagrantup.com/)
2. 	Clone the railsmn-dev-box repo

		mkdir rails
		git clone git://github.com/railsmn/railsmn-dev-box.git rails
		cd rails

3. 	Modify script for Rails 4

	Open `./puppet/manifests/default.pp` and set Rails version. I wanted latest so I removed the current 3.2 version


		exec { "${as_vagrant} 'gem install rails --no-rdoc --no-ri'":
	  		creates => "${home}/.rvm/bin/rails",
	  		require => Exec['install_ruby']
		}

4. 	Add your shared workspace

	Open `./Vagrantfile` and add the following line

		config.vm.synced_folder  "workspace", "/home/vagrant/workspace"

	The first parameter is the host folder relative to the root Vagrantfile. The second parameter is the full path on the virtual system. I created a workspace folder and then clone each project I'm working on underneath the root workspace folder.

	More information: [http://docs.vagrantup.com/v2/synced-folders](http://docs.vagrantup.com/v2/synced-folders)

4. 	Start the image `vagrant up`

5. 	SSH into your client

	I used PuTTY [(download)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download)

	To find out your settings, type the following after the machine boots:

		vagrant ssh

	Here's my output

		Host: 127.0.0.1
		Port: 2222
		Username: vagrant
		Private key: C:/Users/Edward/.vagrant.d/insecure_private_key

	**PuTTY Configuration**

	a. Enter the Host Name: 127.0.0.1
	b. Enter the Port: 2222
	c. Go to Connection\Data
	   Enter the UserName (vagrant) in Auto-login field
    d. Go to Connection\SSH\Auth
	   Browser for you private key at the location listed above
	e. Go to Session
	   Enter a name under Saved Sessions and hit SAVE!

6. Start Session, the default password is `vagrant`

Enjoy!

###Resources:

* [Vagrant]((http://www.vagrantup.com)
* [Official Vagrant Boxes](https://github.com/mitchellh/vagrant/wiki/Available-Vagrant-Boxes)
* [Community Boxes - VagrantBox.es](http://www.vagrantbox.es/)
* [railsmn-dev-box] (https://github.com/railsmn/railsmn-dev-box)