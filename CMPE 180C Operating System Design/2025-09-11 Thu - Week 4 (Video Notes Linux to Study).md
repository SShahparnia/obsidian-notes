# Linux Commands and Information
## Ubuntu Linux CLI 
- uname -a 
- lsmod
	- lists the kernel modules that you have installed on your machine
- rmmod 
	- remove modules from the machine
- insmod
	- install new modules on the machine
- modinfo "module-name"
	- module information on the system of specified module
- modprobe
	- loads or removes kernel modules
- EXAMPLE:
	  lsmod | grep fs 
		  lists the modules that have "fs" in