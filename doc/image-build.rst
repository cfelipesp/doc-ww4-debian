==============================
Build a Debian container image
==============================

As stated in the Container Manegement session of the 
`Warewulf User Guide <https://warewulf.org/docs/development/index.html>`_ ,
most containers in Docker Hub are not "bootable" for having a very limited 
version of systemd. 

The following Dockerfile is adaptation of 
`https://github.com/hpcng/warewulf/tree/development/userdocs/debian`_ . 
Here, a few additional packages were added: the vim editor and the compilers 
g++ and gfortran.

.. code-block:: Dockerfile

	FROM debian

	# Disclaimer:
	# this is WIP and subject to change, and feedback is highly appreciated

	# squelsh apt-get
	ENV DEBIAN_FRONTEND noninteractive
	ENV RUNLEVEL 1

	# ----- install vital packages -----
	# 'dbus' might makes sense as well
	RUN apt-get update && apt-get install -y --no-install-recommends \
		kmod \
		systemd-sysv \
		openssh-client \
		openssh-server \
		isc-dhcp-client \
		pciutils \
		strace \
		nfs-common \
		ethtool\
		ifupdown \
		linux-image-amd64 \
		ifmetric \
		netbase && \
		rm -rf /var/lib/apt/lists/*

	ENV DEBIAN_FRONTEND teletype  


