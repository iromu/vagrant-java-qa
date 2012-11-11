Description
===========

Sonar and Jenkins CI


Requirements
============

Download Virtualbox [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Download vagrant latest binaries from [http://vagrantup.com](http://vagrantup.com)


Add base image

	$ vagrant box add precise32 http://files.vagrantup.com/precise32.box


Usage
=====


Execute this commands

	$ bundle install
	$ librarian-chef install
	$ vagrant up



TODO
====

Increase tmp size

    $ mount -t tmpfs tmpfs /run -o size=2000M,mode=1777,remount