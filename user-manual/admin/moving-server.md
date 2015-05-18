Moving Arastta
==============

Moving Arastta to a new server
------------------------------

Arastta can be easily migrated to a new web server. The steps are listed below:

1. Copy all the Arastta files from your existing web server to the new web server.
2. Export the Arastta database and import it into the new server.
3. Edit config.php and admin/config.php. These files contain the filesystem paths to Arastta folders, URLs to Arastta frontend and admin, and database access details. The paths and database details will most likely need to be updated, and the URLs will need to be changed only if the Arastta store's domain has changed.