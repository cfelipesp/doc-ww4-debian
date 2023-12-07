Installing Debian in a Virtual Machine
======================================

Create VM in Virtual Manager
----------------------------

Create conexion
~~~~~~~~~~~~~~~


Create machine
~~~~~~~~~~~~~~

* 3 GiB RAM , 2 CPUs
* NIC 1 

  * network source: default NAT
  * device model: virtio

Add a second NIC of isolated kind.

IPv4: 

* 192.168.200.0/24
* DHCP disabled
* isolated

Install Debian 12 in VM
-----------------------

Select only these options for a bare minimum server. No Descktop system or graphical interfaces.

* web server
* SSH server
* standard system utils


Install first packages;

.. code-block :: bash
  
  # apt install sudo vim network-manager

After having installed sudo, we can use it at will.
  

