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

The init.d script was created by using the Ubuntu based init.d script provided here (https://raw.github.com/TryGhost/Ghost-Config/blob/master/init.d/ghost), and the nginx init.d script that is installed by default when installing nginx on openSUSE through repositories.

Because startproc does not include an option such as '--chdir' for the start-stop-daemon command on Ubuntu, ghost will not find a config file unless it is placed in the root directory '/' of the filesystem.  Therefore, some code was added to the <ghost-root>/index.js file, and the <ghost-root>/core/config-loader.js file.

### To Get This Working ###
- Place the init.d script, ghost, in /etc/init.d/
- chmod +x /etc/init.d/ghost
- Edit /etc/init.d/ghost to match your install, particularly changing:
    - GHOST_ROOT variable
    - GHOST_GROUP variable
    - GHOST_USER variable
- Backup your current version of <ghost-root>/index.js
- Download index.js file from (https://github.com/inspectHN/ghost-on-openSUSE) to <ghost-root>/
- Backup your current version of <ghost-root>/core/config-loader.js
- Download config-loader.js file from (https://github.com/inspectHN/ghost-on-openSUSE) to <ghost-root>/core/
