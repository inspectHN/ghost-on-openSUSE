ghost-on-openSUSE
=================

############
## Github ##
############
url: https://github.com/inspectHN/ghost-on-openSUSE  
ssh: git@github.com:inspectHN/ghost-on-openSUSE.git  
svn: https://github.com/inspectHN/ghost-on-openSUSE

======
Provides files to help ghost blogging platform run on openSUSE

IMPORTANT: This script must be called by its full path, calling it using "service" will not work.
example: Use '/etc/init.d/ghost start' instead of 'service ghost start'.

The init.d script was created by using the Ubuntu based init.d script provided here (https://raw.github.com/TryGhost/Ghost-Config/blob/master/init.d/ghost), and the nginx init.d script that is installed by default when installing nginx on openSUSE through repositories.  It was then re-written due to limitations with the startproc command.

Because startproc does not include an option such as '--chdir' for the start-stop-daemon command on Ubuntu, ghost will not find a config file unless it is placed in the root directory '/' of the filesystem.  Therefore, some code was added to the <ghost-root>/index.js file, and the <ghost-root>/core/config-loader.js file.  Another issue, is that when uploading content, such as pictures, the ghost blog will think that the <ghost-root> is "/", and attempt to create a /content directory to place the images in, which fails due to invalid permissions.  For this reason the script was completely re-written to not use startproc, killproc, or checkproc as is normal for openSUSE init.d script.

### To Get This Working ###
- Place the init.d script, ghost, in /etc/init.d/
- chmod +x /etc/init.d/ghost
- Edit /etc/init.d/ghost to match your install, particularly changing:
    - GHOST_ROOT variable
    - GHOST_GROUP variable
    - GHOST_USER variable
- To make it start upon server startup, chkconfig ghost on
- Backup your current version of <ghost-root>/index.js
- Download index.js file from (https://github.com/inspectHN/ghost-on-openSUSE) to <ghost-root>/
- Backup your current version of <ghost-root>/core/config-loader.js
- Download config-loader.js file from (https://github.com/inspectHN/ghost-on-openSUSE) to <ghost-root>/core/
