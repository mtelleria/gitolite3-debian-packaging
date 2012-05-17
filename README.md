gitolite3-debian-packaging
==========================

Packaging gitolite g3 into Debian based on the existing gitolite g2
package from Debian sid.

        http://packages.debian.org/source/sid/gitolite
        git://git.deb.at/pkg/gitolite.git

This repository contains 3 branches (according to git-buildpackage
with pristine-tar technique) [1].

*  miguel-debian

   Based on the 'debian' branch in Sid's git.deb.at repository
   containing the current extracted source package.

*  miguel-upstream

   Based on the 'master' branch in Sid's git.deb.at repository
   containing the upstream (github[2]) changes (for the g2 branch).

*  pristine-tar

   Branch used internally by git-buildpackage to recreate the
   .orig.tar.gz during package generation.

The branches miguel-debian and miguel-upstream originate from their
git.deb.at counterparts at tags debian/2.3-1 and upstream/2.3
respectively.



[1]
http://honk.sigxcpu.org/projects/git-buildpackage/manual-html/gbp.html

[2] git://github.com/sitaramc/gitolite
HAHA
