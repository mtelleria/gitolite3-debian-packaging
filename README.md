gitolite3-debian-packaging
==========================

This repository holds my personal packing of gitolite version 3 (g3)
for Debian.  

Therefore it merges the upstream work of 

        [https://github.com/sitaramc/gitolite.git]

with the packaging work done in Debian at

        git://git.deb.at/pkg/gitolite.git
        [http://packages.debian.org/source/sid/gitolite]

You can also find a released version of the packages in source and
binary form in my Ubuntu PPA.

        [https://launchpad.net/~snapy/+archive/ppa/+packages]

The package (renamed to "gitolite3") can coexist with the official
Debian package "gitolite" that contains the g2 version.


Branches
--------

The repository includes the following branches:

*   master

    Only basic documentation, README.md and the like.

*   miguel-debian

    "Debian branch" for git-buildpackage in Debian Sid.  It
    starts in the "debian" branch of git.deb.at repo and has merged
    the new upstream content from the miguel-upstream branch. 

*   miguel-upstream

    "Upstream branch" for git-buildpackage.  It started in the
    "master" branch of git.deb.at (which follows g2 development in
    gitolite's upstream).  After the split, I removed all its contents
    (git rm -rf .) and merged the new orphaned g3 branch from
    upstream.  So now it follows upstream g3 development.

*   pristine-tar

    Branch used by git-buildpackage to reproduce the same .orig.tar.gz
    for the upstream versions.

*   miguel-squeeze

    A branch of miguel-debian for creating a Debian Squeeze package.
    So far there is no major difference between this branch and the
    Sid version.

*   miguel-lucid-ppa

    Similar to miguel-squeeze, this branch also originates in
    miguel-debian.  It holds the package version that is placed in my
    PPA.

Changes done in packaging
-------------------------

### Changes in the packaging way.

*   Rework debian/rules to use debhelper 7 facilities (dh * and
    .links, .docs files) rather than doing everything manually as it
    is done in the Debian package.

*   Using quilt-3.0 format with the "unapply-patches" local option (so
    that the patched changes don't mix with git).   This means that
    any explicit mention of quilt dependency or patch/unpatch target
    rules have been removed.

*   Use git-buildpackage to manage upstream and debian branches as
    well as the patch generation with gbp-pq.  I also make use of the
    pristine-tar functionality to rebuild the .orig.tar.gz.

    To make life easier I recommend using the following gbp.conf file
    (stored in the .git directory).

         [DEFAULT]
         # these are upstream and debian branches:
         upstream-branch=miguel-upstream
         debian-branch=miguel-debian

         # use pristine-tar:
         pristine-tar = True

    The `README.source` file contains more information about
    git-buildpackage workflows.

    You can find more info about git-buildpackage here.

http://honk.sigxcpu.org/projects/git-buildpackage/manual-html/gbp.html

*   Renaming source and binary package names from "gitolite" to
    "gitolite3" in order not to have conflicts with the official
    gitolite g2 package.

    See README.gitolite3_2_coexist for more info.

However the debconf work to do the setup phase of gitolite with
`dpkg-reconfigure` remains the same albeit some minor adjustments.


### Changes due to the version 3 of gitolite

*   All g2 content has been removed with a git rm -rf . in order to
    merge upstream's g3 branch.

*   gl-setup is now replaced by gitolite setup run by the gitolite
    user.

*   All Debian patches for version g2 are now of no use in g3.

*   The g3 install script has been patched with a fixed value for the
    VERSION file.


Left TODO
---------

*   Generate html documentation from the .mkd files.

*   Fix all kinds of lintian errors still present.

*   Provide some tools for automatic g2 migration.    
