# pudlez-tools Gentoo Overlay

Due to sakaki-tools overlay starting to get outdated and throwing extra stuff to the screen, I decided it was time I created my own overlay. I will eventually start adding my own ebuilds that I've made of my Odroid boards over the years... I've used sakaki-tools as a template for my overlay and kept the showem ebuild.

Please note that this overlay is just my collection. I can't guarentee I will fix any issue you're having but please let me know and I can try...



The following are short form instructions. If you haven't already installed **git**(1), do so first:

    # emerge --ask --verbose dev-vcs/git 

Next, create a custom `/etc/portage/repos.conf` entry for the **pudlez-tools** overlay, so Portage knows what to do. Make sure that `/etc/portage/repos.conf` exists, and is a directory. Then, fire up your favorite editor:

    # nano -w /etc/portage/repos.conf/pudlez-tools.conf

and put the following text in the file:
```
[pudlez-tools]
 
# PuDLeZ's collection of ebuilds...
# Maintainer: PuDLeZ (pudlez@pudlez.net)
 
location = /usr/local/portage/pudlez-tools
sync-type = git
sync-uri = https://github.com/pudlez/pudlez-tools.git
priority = 50
auto-sync = yes
```

Then run:

    # emaint sync --repo pudlez-tools

If you are running on the stable branch by default, allow **~amd64** keyword files from this repository. Make sure that `/etc/portage/package.accept_keywords` exists, and is a directory. Then issue:

    # echo "*/*::pudlez-tools ~amd64" >> /etc/portage/package.accept_keywords/pudlez-tools-repo
    
Now you can install packages from the overlay. For example:

    # emerge --ask --verbose app-portage/showem

## Maintainers

* [pudlez](mailto:pudlez@pudlez.net)
