# PsychoPy v2021.2.3 on a Raspberry Pi 4

Below are instructions to install [PsychoPy](https://www.psychopy.org) on a [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/).

Tested with a Raspberry Pi 4 (4 Gb RAM) running a 64bit kernel.

```txt
# uname -a
Linux rpi4 5.10.63-v8+ #1496 SMP PREEMPT Wed Dec 1 15:59:46 GMT 2021 aarch64 GNU/Linux

# lsb_release -a
Distributor ID: Raspbian
Description:    Raspbian GNU/Linux 10 (buster)
Release:    10
Codename:   buster
```

## 1. Install libraries

```sh
sudo apt-get install -y cmake pkg-config dpkg-dev build-essential && \
    libgl1-mesa-dev mesa-common-dev mesa-utils && \
    libhdf5-serial-dev && \
    qt5-default pyqt5-dev pyqt5-dev-tools && \
    libx11-dev libglib2.0-dev libgtk-3-dev libtiff-dev libsndfile1-dev && \
    libusb-1.0.0-dev portaudio19-dev libasound2-dev libportmidi-dev liblo-dev && \
    libwebkitgtk-1.0 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 && \
    libwebkitgtk-dev libgtk2.0-dev libsdl-dev libsdl1.2-dev libnotify-dev && \
    libwebkitgtk-3.0-dev libwebkit2gtk-4.0-dev libxtst-dev libgtk-3-dev && \
    python3-dev python3.7-dev python-xlib && \
    libjpeg-dev libpng-dev libtiff-dev libsm-dev && \
    libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base && \
    gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav && \
    gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-pulseaudio && \
    libgstreamerd-3-dev && \
    freeglut3 freeglut3-dev libglew-dev && \
    python3-wxgtk4.0 libgstreamer-plugins-base0.10-dev libghc-gtk3-dev libwxgtk3.0-gtk3-dev && \
    libegl1-mesa libwayland-egl1-mesa
```

## 2. Set up venv

```sh
python3 -m venv ~/venv/psychopy
source ~/venv/psychopy/bin/activate
```

## 3. Upgrade and install numpy, scipy and pandas

```sh
pip install --upgrade pip setuptools wheel
pip install numpy scipy pandas
```

## 4. Install psychtoolbox

psychtoolbox version 3.0.18.2

```sh
pip install psychtoolbox
```

## 5. Install wxPython

Latest version 4.1.1 fails to install. However, previous version works

```sh
pip install wxpython==4.1.0
```

## 6. Install `pyo` library from source

[pyo](http://ajaxsoundstudio.com/software/pyo/) version: 1.0.4

```sh
brew install liblo libsndfile portaudio portmidi
git clone https://github.com/belangeo/pyo.git
cd pyo
python setup.py install --use-double
```

## 7. Install PsychToolbox from source

[psychtoolbox](http://psychtoolbox.org) version: 3.0.18.3 (BETA)

Download latest [Psychtoolbox](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases) source.

```sh
wget https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/tags/3.0.18.3.tar.gz

tar -xvzf 3.0.18.3.tar.gz
cd Psychtoolbox-3-3.0.18.3

python setup.py install
```

## 8. Install other libraries

```sh
pip install SpeechRecognition
```

## 9. Install PsychoPy

Installing PsychoPy and remaining dependencies.

```sh
pip install psychopy
```

Starting psychopy fails with an error. Seems related to psychtoolbox because uninstalling psychtoolbox fixes the error.

```sh
pip uninstall psychtoolbox
psychopy
```

PsychoPy starts but many demos do not work at the moment. Further testing needed.
