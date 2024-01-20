# Display-Link-Fixes
This will fix display link for linux for newer kernels


# Display Link workaround for linux kernel 6.0 and above

## First thing's first.  Uninstall all dispaly link runtimes.  This should probably include any evdi and dmks installs as well if it was bundled with the display link driver on the [offical website](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)


# Grab the evdi commit on display link's github.  It looks like there is a patch for later kernels but it was never pushed. Neither was dkms.

```git clone git@github.com:DisplayLink/evdi.git
sudo cp -r evdi /usr/src/evdi
cd /usr/src
sudo ln -s evdi/module evdi-1.12.0
sudo dkms install evdi/1.12.0
```
# Next Download the display link software binary.  This will exclude the dependencies that we have already installed above so they are not overridden.

```wget -O displaylink_5.6.1.zip https://www.synaptics.com/sites/default/files/exe_files/2022-08/DisplayLink%20USB%20Graphics%20Software%20for%20Ubuntu5.6.1-EXE.zip
unzip displaylink_5.6.1.zip -d displaylink_5.6.1
cd displaylink_5.6.1
sudo ./displaylink-driver-5.6.1-59.184.run
```
