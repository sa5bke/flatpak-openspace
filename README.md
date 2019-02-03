# WIP flatpak build for OpenSpace

This is a **work in progress** to compile and package [Open Space](https://www.openspaceproject.com/) on Linux.

## Known issues / TODO

* Some planet images are not displaying correctly
* A wrapper script should be included that will take care of setting up the environment

## How to install

A repo will be added later, for now **flatpak-builder** is needed.

## How to run

You have to clone the [OpenSpace repo](https://github.com/OpenSpace/OpenSpace) and copy files to to *~/.var/app/com.openspaceproject.OpenSpace/data*

These files/dirs are needed: 

`cache  config  data  documentation  logs  modules  openspace.cfg  screenshots  scripts  shaders  sync`

Then modify **openspace.cfg** and add **BASE = "/var/data/"** to the Paths.

To run OpenSpace:

`flatpak run com.openspaceproject.OpenSpace -f /var/data/openspace.cfg`


## How to compile

If you want to compile and run from local repo, follow these instructions:

* Start the build:
 
`flatpak-builder --repo=repo --force-clean build com.openspaceproject.openspace.json`

* Add repo

`flatpak --user remote-add --no-gpg-verify openspace-local file://path-to-repo`

* Install

`flatpak install openspace-local com.openspaceproject.OpenSpace`
