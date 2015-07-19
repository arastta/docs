Modification System
===================

Arastta ships with an advanced Modification System, able to read/parse both vQmod and OCmod XML files in the core. Extensions written for both can be uploaded from the Extension Installer page and maintained via the Modifications page (from Marketplace).

![modifications](_images/modifications.png)

vQmod
=====

[vQmod](https://github.com/vqmod/vqmod) (aka virtual Quick mod) is a 3rd party system developed by Qphoria and JAY6390. While Arastta can read vQmod files, you can also install vQmod engine separately and in such a case, temporary files created by vQmod will be saved by its own mechanism.

OCmod
=====

OCmod (aka OpenCart mod) was created by OpenCart's developer as a simplified cut down version of vQmod.

How it works
============

Modification System allows you to alter source files without actually editing them. The system reads XML files which contains how and which file should be changed. All changes are saved in a temporary file which is substituted for the original during execution. Both vQmod and OCmod temporary files are stored under the ***system/modification*** folder.

Scripting
=========

Here you can find how the [vQmod](https://github.com/vqmod/vqmod/wiki/Scripting) and [OCmod](https://github.com/opencart/opencart/wiki/Modification-System) XML scripting language works.
