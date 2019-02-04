# WIP flatpak build for OpenSpace

This is a **work in progress** to compile and package [Open Space](https://www.openspaceproject.com/) on Linux.

## Known issues / TODO

* Some planet images are not displaying correctly
* A wrapper script should be included that will take care of setting up the environment

## Prerequisites

Download and install [Flatpak](https://www.flatpak.org/setup/) for your distribution and add **flathub** as an repo. Also install **flatpak-builder**. 

To be able to run and comipile you also need the freedesktop runtime and SDK:

`sudo flatpak install flathub org.freedesktop.Platform//18.08 org.freedesktop.Sdk//18.08`

You would also benefit from atleast **6 GB** of RAM to avoid swapping.

## How to install

A repo will be added later, for now **flatpak-builder** is needed.


## How to compile

If you want to compile and run from local repo, follow these instructions:

* Start the build:
 
`flatpak-builder --repo=repo --force-clean build com.openspaceproject.openspace.json`

* Add repo

`flatpak --user remote-add --no-gpg-verify openspace-local file://path-to-repo`

* Install

`flatpak --user install openspace-local com.openspaceproject.OpenSpace`

## How to run

You have to clone the [OpenSpace repo](https://github.com/OpenSpace/OpenSpace) and copy files to to **~/.var/app/com.openspaceproject.OpenSpace/data**

These files/dirs are needed: 

`cache  config  data  documentation  logs  modules  openspace.cfg  screenshots  scripts  shaders  sync`

You also have to modify **openspace.cfg** and add **BASE = "/var/data/"** to the paths.

To run OpenSpace:

`flatpak run com.openspaceproject.OpenSpace -f /var/data/openspace.cfg`
