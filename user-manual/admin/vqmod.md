vQmod
=====

While strictly modules, product feeds and Arastta extensions should be standalone and modular, some require modifications to the Arastta core. Modifying Arastta core files greatly reduces your ability to upgrade your store to later versions, and can affect other modules and extensions. [vQmod ](https://code.google.com/p/vqmod/)provides a mechanism by which modules requiring Arastta core modifications can be installed without damaging the integrity of your core system for upgrades. vQmod keeps a list of filenames and changes required, in the form of one XML file per extension. These changes are then created as the core files are used, and the resulting files are stored as cached copies which are executed instead of the original, core PHP or TPL file.

If you wish to upgrade your store, or have a [3rd party extension](http://extensions.arastta.pro/) that you have not used before, it is advisable that you use the vQmod system. The vQmod instructions for installation can be found here: [http://code.google.com/p/vqmod/](https://code.google.com/p/vqmod/).

vQmod advises you to set the permissions to writable for the vqmod/vqcache folders, index.php, and admin/index.php. In Filezilla you can right click on a file or folder, select "File Permissions...", and enter 755 or 777 in the "Numeric value" to set it to writable.

![set permission 0755](_images/vqmod-set-permission.png)
