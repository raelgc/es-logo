![es-logo.png](es-logo.png) 

# EmulationStation Plymouth Theme

This is a [EmulationStation](https://github.com/RetroPie/EmulationStation) splash screen (i.e, a [plymouth](https://wiki.ubuntu.com/Plymouth) theme) for Ubuntu.

It presents a simple EmulationStation logo in a black background with progress dots. It's based on the `ubuntu-logo-scale-2` plymouth.

## Install

We'll use `git` to install, so make sure you have it installed (if not, run `sudo apt install git`).

Then run the following commands to install this theme (if you're under Ubuntu **14.04**, replace all `/usr/share/plymouth` with `/lib/plymouth`):

    cd /usr/share/plymouth/themes
    sudo git clone https://github.com/raelgc/es-logo.git
    sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/es-logo/es-logo.plymouth 100

Now it's installed, but it's **not** the default theme yet.

## Make it the default 

Run the following commands to make it the default `plymouth` theme:

    sudo update-alternatives --config default.plymouth

You'll see a list of available themes like this:

```
There are 2 choices for the alternative default.plymouth (providing /usr/share/plymouth/themes/default.plymouth).

  Selection    Path                                                         Priority   Status
------------------------------------------------------------
* 0            /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
  1            /usr/share/plymouth/themes/es-logo/es-logo.plymouth           100       manual mode
  2            /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press <enter> to keep the current choice[*], or type selection number:
```

Select `es-logo.plymouth` number (in the above sample, `1`) as default and press <kbd>Enter</kbd>.

Now update `initram`:

    sudo update-initramfs -u

Reboot.

## Uninstall

To remove it just run (if you're under Ubuntu **14.04**, replace `/usr/share/plymouth` with `/lib/plymouth`):

    sudo update-alternatives --remove default.plymouth /usr/share/plymouth/themes/es-logo/es-logo.plymouth

And update `initram`:

    sudo update-initramfs -u
