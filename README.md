[![Linux](https://svgshare.com/i/Zhy.svg)](https://svgshare.com/i/Zhy.svg)  [![made-with-bash](https://img.shields.io/badge/Made%20with-Bash-1f425f.svg)](https://www.gnu.org/software/bash/) 

# File-Manager-for-Ubntu

This repo includes steps for installing a file manager/explorer for ubntu

I will install [SapceFM](https://github.com/IgnorantGuru/spacefm).

![alt text](https://github.com/Mr-TalhaIlyas/File-Manager-for-Ubntu/blob/main/img.png)

The detailed instructions are give in their homepage, but I encountered seme issues while configuring it so I'll write down steps here for future use.
# Step 1.
------
First make a dir

```
#make
mkdir /tmp/spacefm-build
# move to dir
cd /tmp/spacefm-build
```

then download the file and extract it

```
#download (better to check or download the latest version -visit official webpage-)
wget -O spacefm.tar.gz https://github.com/IgnorantGuru/spacefm/archive/next.tar.gz
#extract
tar xzf spacefm.tar.gz && cd spacefm-*
```
# Step 2.
------
Then configure
```
./configure --prefix=/usr
```
This step might not run in the first try and you might have to install a bunch of software for it so follow
if you get `configure: error: no acceptable C compiler found in $PATH` error.

**So I'd suggest installing all of the follwoing packages (root) before moving to step 3.**

```
sudo apt-get install build-essential
```
then you might have to install `intltool` 
```
sudo apt install intltool
```

then againg run `./configure --prefix=/usr` and if your get `pkg-config script could not be found or is too old` you need to install

```
sudo apt-get install -y pkg-config
```
if this solves problem move ahead else you might get `GTK` error so install
```
sudo apt-get install gtk2.0
sudo apt-get install libudev-dev libsystemd-dev
sudo apt-get install -y libffmpegthumbnailer-dev
```

# Step 3.
------
then run following one be one inside the `tmp/spacefm-build/spacefm-next`

```
make -s
sudo make install
sudo update-mime-database /usr/share/mime > /dev/null
sudo update-desktop-database -q
sudo gtk-update-icon-cache -q -t -f /usr/share/icons/hicolor
sudo gtk-update-icon-cache -q -t -f /usr/share/icons/Faenza

# Remove Temporary Files
cd / && rm -rf /tmp/spacefm-build

```
