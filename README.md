# lambda-layers

The scripts in this repository make it easy to create Lambda layers with Linux binary packages. It contains the following scripts.

### install_layer.sh

As an example, you can run the following command to install the yum package for git

```bash
./install_layer.sh git
```

Behind the scenes this leverages a docker container that runs yumda. The result is a `git-layer` folder that contains the Linux executable for git

### run.sh

As an example, you can run the following command to run a docker container for git

```bash
./run.sh git
```

This launches a docker container based on lambci/lambda:python3.8 and mounts the `git-layer` directory to the `/opt` directory in the container and launches a bash shell

Within bash, you can access `git` on the command line

### publish_layer.sh

As an example, you can run the following command to publish a lambda layer for git. Be sure to set the AWS_PROFILE environment variable within the script before you run it

```bash
./publish_layer.sh git
```

This zips up the folder created by install_layer.sh, and uploads it into a Lambda layer

### abcmidi_to_layer.sh

If your software is not available in the yumda yum repository, you can still install it if the rpm is available. Download the rpm file to /tmp and run this script.

It leverages the awesome [fpm tool](https://fpm.readthedocs.io/en/latest/index.html) that converts the rpm to a regular zip file. You can then unzip and re-zip this to a format that is suitable for a lambda layer



### list.sh

You can run this command to print a list of available yumda packages

```bash
./list.sh
```

This prints a list similar to the following

```
Loaded plugins: ovl, priorities
Available Packages
GraphicsMagick.x86_64              1.3.34-1.lambda2                      lambda2
GraphicsMagick-c++.x86_64          1.3.34-1.lambda2                      lambda2
ImageMagick.x86_64                 6.9.10.68-3.lambda2.0.1               lambda2
OpenColorIO.x86_64                 1.0.9-4.lambda2                       lambda2
OpenEXR.x86_64                     1.7.1-8.lambda2.0.1                   lambda2
OpenEXR-libs.x86_64                1.7.1-8.lambda2.0.1                   lambda2
OpenImageIO.x86_64                 1.5.24-3.lambda2.1                    lambda2
OpenImageIO-utils.x86_64           1.5.24-3.lambda2.1                    lambda2
SDL.x86_64                         1.2.15-17.lambda2                     lambda2
alsa-lib.x86_64                    1.1.4.1-2.lambda2                     lambda2
apr.x86_64                         1.6.3-5.lambda2.0.2                   lambda2
apr-util.x86_64                    1.6.1-5.lambda2.0.2                   lambda2
apr-util-bdb.x86_64                1.6.1-5.lambda2.0.2                   lambda2
apr-util-ldap.x86_64               1.6.1-5.lambda2.0.2                   lambda2
apr-util-mysql.x86_64              1.6.1-5.lambda2.0.2                   lambda2
apr-util-nss.x86_64                1.6.1-5.lambda2.0.2                   lambda2
apr-util-odbc.x86_64               1.6.1-5.lambda2.0.2                   lambda2
apr-util-openssl.x86_64            1.6.1-5.lambda2.0.2                   lambda2
apr-util-pgsql.x86_64              1.6.1-5.lambda2.0.2                   lambda2
apr-util-sqlite.x86_64             1.6.1-5.lambda2.0.2                   lambda2
arduino-builder.x86_64             1.3.25-1.lambda2                      lambda2
arduino-ctags.x86_64               5.8-8.arduino11.lambda2               lambda2
aspell.x86_64                      12:0.60.6.1-9.lambda2.0.1             lambda2
audispd-plugins.x86_64             2.8.1-3.lambda2.1                     lambda2
audit.x86_64                       2.8.1-3.lambda2.1                     lambda2
audit-libs.x86_64                  2.8.1-3.lambda2.1                     lambda2
autoconf.noarch                    2.69-11.lambda2                       lambda2
autogen.x86_64                     5.18-5.lambda2.0.2                    lambda2
autogen-libopts.x86_64             5.18-5.lambda2.0.2                    lambda2
automake.noarch                    1.13.4-3.1.lambda2                    lambda2
avahi.x86_64                       0.6.31-20.lambda2                     lambda2
avahi-autoipd.x86_64               0.6.31-20.lambda2                     lambda2
avahi-compat-howl.x86_64           0.6.31-20.lambda2                     lambda2
avahi-compat-libdns_sd.x86_64      0.6.31-20.lambda2                     lambda2
avahi-dnsconfd.x86_64              0.6.31-20.lambda2                     lambda2
avahi-glib.x86_64                  0.6.31-20.lambda2                     lambda2
avahi-gobject.x86_64               0.6.31-20.lambda2                     lambda2
avahi-libs.x86_64                  0.6.31-20.lambda2                     lambda2
avahi-tools.x86_64                 0.6.31-20.lambda2                     lambda2
bc.x86_64                          1.06.95-13.lambda2.0.2                lambda2
binutils.x86_64                    2.29.1-30.lambda2                     lambda2
boost.x86_64                       1.53.0-27.lambda2.0.3                 lambda2
boost-atomic.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-chrono.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-context.x86_64               1.53.0-27.lambda2.0.3                 lambda2
boost-date-time.x86_64             1.53.0-27.lambda2.0.3                 lambda2
boost-filesystem.x86_64            1.53.0-27.lambda2.0.3                 lambda2
boost-graph.x86_64                 1.53.0-27.lambda2.0.3                 lambda2
boost-iostreams.x86_64             1.53.0-27.lambda2.0.3                 lambda2
boost-locale.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-math.x86_64                  1.53.0-27.lambda2.0.3                 lambda2
boost-program-options.x86_64       1.53.0-27.lambda2.0.3                 lambda2
boost-python.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-random.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-regex.x86_64                 1.53.0-27.lambda2.0.3                 lambda2
boost-serialization.x86_64         1.53.0-27.lambda2.0.3                 lambda2
boost-signals.x86_64               1.53.0-27.lambda2.0.3                 lambda2
boost-system.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-test.x86_64                  1.53.0-27.lambda2.0.3                 lambda2
boost-thread.x86_64                1.53.0-27.lambda2.0.3                 lambda2
boost-timer.x86_64                 1.53.0-27.lambda2.0.3                 lambda2
boost-wave.x86_64                  1.53.0-27.lambda2.0.3                 lambda2
bsdcpio.x86_64                     3.1.2-14.lambda2                      lambda2
bsdtar.x86_64                      3.1.2-14.lambda2                      lambda2
bzip2.x86_64                       1.0.6-13.lambda2.0.2                  lambda2
bzip2-libs.x86_64                  1.0.6-13.lambda2.0.2                  lambda2
c-ares.x86_64                      1.10.0-3.lambda2.0.2                  lambda2
cairo.x86_64                       1.15.12-4.lambda2                     lambda2
cairo-tools.x86_64                 1.15.12-4.lambda2                     lambda2
cdparanoia.x86_64                  10.2-17.lambda2.0.2                   lambda2
cdparanoia-libs.x86_64             10.2-17.lambda2.0.2                   lambda2
cfitsio.x86_64                     3.370-10.lambda2                      lambda2
cfssl.x86_64                       1.4.1-1.lambda2                       lambda2
clamav.x86_64                      0.102.4-1.lambda2                     lambda2
clamav-data.noarch                 0.102.4-1.lambda2                     lambda2
clamav-filesystem.noarch           0.102.4-1.lambda2                     lambda2
clamav-lib.x86_64                  0.102.4-1.lambda2                     lambda2
clamav-update.x86_64               0.102.4-1.lambda2                     lambda2
compat-gcc-48.x86_64               4.8.5-16.lambda2.0.2                  lambda2
compat-gcc-48-c++.x86_64           4.8.5-16.lambda2.0.2                  lambda2
compat-gcc-48-gfortran.x86_64      4.8.5-16.lambda2.0.2                  lambda2
compat-gcc-48-libgfortran.x86_64   4.8.5-16.lambda2.0.2                  lambda2
compat-libical1.x86_64             1.0.1-2.lambda2.0.1                   lambda2
compat-libmpc.x86_64               1.0.1-3.lambda2.0.2                   lambda2
cpio.x86_64                        2.11-28.lambda2                       lambda2
cpp.x86_64                         7.3.1-9.lambda2                       lambda2
cracklib.x86_64                    2.9.0-11.lambda2.0.2                  lambda2
cracklib-dicts.x86_64              2.9.0-11.lambda2.0.2                  lambda2
cups-libs.x86_64                   1:1.6.3-51.lambda2                    lambda2
curl.x86_64                        7.61.1-12.lambda2.0.2                 lambda2
cyrus-sasl.x86_64                  2.1.26-23.lambda2                     lambda2
cyrus-sasl-gs2.x86_64              2.1.26-23.lambda2                     lambda2
cyrus-sasl-gssapi.x86_64           2.1.26-23.lambda2                     lambda2
cyrus-sasl-ldap.x86_64             2.1.26-23.lambda2                     lambda2
cyrus-sasl-lib.x86_64              2.1.26-23.lambda2                     lambda2
cyrus-sasl-md5.x86_64              2.1.26-23.lambda2                     lambda2
cyrus-sasl-ntlm.x86_64             2.1.26-23.lambda2                     lambda2
cyrus-sasl-plain.x86_64            2.1.26-23.lambda2                     lambda2
cyrus-sasl-scram.x86_64            2.1.26-23.lambda2                     lambda2
cyrus-sasl-sql.x86_64              2.1.26-23.lambda2                     lambda2
dbus.x86_64                        1:1.10.24-7.lambda2                   lambda2
dbus-glib.x86_64                   0.100-7.2.lambda2                     lambda2
dbus-libs.x86_64                   1:1.10.24-7.lambda2                   lambda2
dejavu-fonts-common.noarch         2.33-6.lambda2                        lambda2
dejavu-lgc-sans-fonts.noarch       2.33-6.lambda2                        lambda2
dejavu-lgc-sans-mono-fonts.noarch  2.33-6.lambda2                        lambda2
dejavu-lgc-serif-fonts.noarch      2.33-6.lambda2                        lambda2
dejavu-sans-fonts.noarch           2.33-6.lambda2                        lambda2
dejavu-sans-mono-fonts.noarch      2.33-6.lambda2                        lambda2
dejavu-serif-fonts.noarch          2.33-6.lambda2                        lambda2
diffutils.x86_64                   3.3-5.lambda2                         lambda2
eccodes.x86_64                     2.18.0-1.lambda2                      lambda2
eccodes-data.noarch                2.18.0-1.lambda2                      lambda2
elfutils.x86_64                    0.176-2.lambda2                       lambda2
elfutils-libelf.x86_64             0.176-2.lambda2                       lambda2
elfutils-libs.x86_64               0.176-2.lambda2                       lambda2
enchant.x86_64                     1:1.6.0-8.lambda2.0.2                 lambda2
enchant-aspell.x86_64              1:1.6.0-8.lambda2.0.2                 lambda2
enchant-voikko.x86_64              1:1.6.0-8.lambda2.0.2                 lambda2
expat.x86_64                       2.1.0-12.lambda2                      lambda2
fftw.x86_64                        3.3.3-8.lambda2.0.2                   lambda2
fftw-libs.x86_64                   3.3.3-8.lambda2.0.2                   lambda2
fftw-libs-double.x86_64            3.3.3-8.lambda2.0.2                   lambda2
fftw-libs-long.x86_64              3.3.3-8.lambda2.0.2                   lambda2
fftw-libs-single.x86_64            3.3.3-8.lambda2.0.2                   lambda2
file.x86_64                        5.11-36.lambda2.0.1                   lambda2
file-libs.x86_64                   5.11-36.lambda2.0.1                   lambda2
findutils.x86_64                   1:4.5.11-6.lambda2                    lambda2
fipscheck.x86_64                   1.4.1-6.lambda2.0.2                   lambda2
fipscheck-lib.x86_64               1.4.1-6.lambda2.0.2                   lambda2
flac.x86_64                        1.3.0-5.lambda2.0.2                   lambda2
flac-libs.x86_64                   1.3.0-5.lambda2.0.2                   lambda2
fontconfig.x86_64                  2.13.0-4.3.lambda2                    lambda2
fontpackages-filesystem.noarch     1.44-8.lambda2                        lambda2
fpack.x86_64                       3.370-10.lambda2                      lambda2
freetype.x86_64                    2.8-14.lambda2                        lambda2
fribidi.x86_64                     1.0.2-1.lambda2.1                     lambda2
gc.x86_64                          7.6.4-3.lambda2.0.2                   lambda2
gcc.x86_64                         7.3.1-9.lambda2                       lambda2
gcc-c++.x86_64                     7.3.1-9.lambda2                       lambda2
gcc-gdb-plugin.x86_64              7.3.1-9.lambda2                       lambda2
gcc-gfortran.x86_64                7.3.1-9.lambda2                       lambda2
gcc-gnat.x86_64                    7.3.1-9.lambda2                       lambda2
gcc-go.x86_64                      7.3.1-9.lambda2                       lambda2
gcc-objc.x86_64                    7.3.1-9.lambda2                       lambda2
gcc-objc++.x86_64                  7.3.1-9.lambda2                       lambda2
gd.x86_64                          2.0.35-26.lambda2.0.2                 lambda2
gd-progs.x86_64                    2.0.35-26.lambda2.0.2                 lambda2
gdbm.x86_64                        1:1.13-6.lambda2.0.2                  lambda2
gdbm-devel.x86_64                  1:1.13-6.lambda2.0.2                  lambda2
gdk-pixbuf2.x86_64                 2.36.12-3.lambda2                     lambda2
ghc-Cabal.x86_64                   1.16.0-26.4.lambda2                   lambda2
ghc-HTTP.x86_64                    4000.2.8-33.lambda2                   lambda2
ghc-aeson.x86_64                   0.6.2.1-3.lambda2                     lambda2
ghc-array.x86_64                   0.4.0.1-26.4.lambda2                  lambda2
ghc-attoparsec.x86_64              0.10.4.0-2.lambda2                    lambda2
ghc-base.x86_64                    4.6.0.1-26.4.lambda2                  lambda2
ghc-base-unicode-symbols.x86_64    0.2.2.4-4.lambda2                     lambda2
ghc-base64-bytestring.x86_64       1.0.0.1-3.lambda2                     lambda2
ghc-binary.x86_64                  0.5.1.1-26.4.lambda2                  lambda2
ghc-blaze-builder.x86_64           0.3.1.1-2.lambda2                     lambda2
ghc-blaze-html.x86_64              0.6.1.1-2.lambda2                     lambda2
ghc-blaze-markup.x86_64            0.5.1.5-3.lambda2                     lambda2
ghc-bytestring.x86_64              0.10.0.2-26.4.lambda2                 lambda2
ghc-conduit.x86_64                 1.0.3-2.lambda2                       lambda2
ghc-containers.x86_64              0.5.0.0-26.4.lambda2                  lambda2
ghc-data-default.x86_64            0.5.1-4.lambda2                       lambda2
ghc-deepseq.x86_64                 1.3.0.1-26.4.lambda2                  lambda2
ghc-digest.x86_64                  0.0.1.2-2.lambda2                     lambda2
ghc-directory.x86_64               1.2.0.1-26.4.lambda2                  lambda2
ghc-dlist.x86_64                   0.5-11.lambda2                        lambda2
ghc-extensible-exceptions.x86_64   0.1.1.4-13.lambda2                    lambda2
ghc-filepath.x86_64                1.3.0.1-26.4.lambda2                  lambda2
ghc-ghc.x86_64                     7.6.3-26.4.lambda2                    lambda2
ghc-hashable.x86_64                1.1.2.5-4.lambda2                     lambda2
ghc-haskell2010.x86_64             1.1.1.0-26.4.lambda2                  lambda2
ghc-haskell98.x86_64               2.0.0.2-26.4.lambda2                  lambda2
ghc-highlighting-kate.x86_64       0.5.6-3.lambda2                       lambda2
ghc-hoopl.x86_64                   3.9.0.0-26.4.lambda2                  lambda2
ghc-hpc.x86_64                     0.6.0.0-26.4.lambda2                  lambda2
ghc-hslua.x86_64                   0.3.10-1.1.lambda2                    lambda2
ghc-lifted-base.x86_64             0.2.1.0-2.lambda2                     lambda2
ghc-monad-control.x86_64           0.3.2.1-2.lambda2                     lambda2
ghc-mtl.x86_64                     2.1.2-27.lambda2                      lambda2
ghc-network.x86_64                 2.4.1.2-32.lambda2                    lambda2
ghc-old-locale.x86_64              1.0.0.5-26.4.lambda2                  lambda2
ghc-old-time.x86_64                1.1.0.1-26.4.lambda2                  lambda2
ghc-pandoc.x86_64                  1.12.3.1-2.lambda2                    lambda2
ghc-pandoc-types.x86_64            1.12.3.1-3.lambda2                    lambda2
ghc-parsec.x86_64                  3.1.3-31.lambda2                      lambda2
ghc-pcre-light.x86_64              0.4-13.lambda2                        lambda2
ghc-pretty.x86_64                  1.1.1.0-26.4.lambda2                  lambda2
ghc-primitive.x86_64               0.5.0.1-4.lambda2                     lambda2
ghc-process.x86_64                 1.1.0.2-26.4.lambda2                  lambda2
ghc-random.x86_64                  1.0.1.1-27.lambda2                    lambda2
ghc-resourcet.x86_64               0.4.6-2.lambda2                       lambda2
ghc-semigroups.x86_64              0.8.5-3.lambda2                       lambda2
ghc-syb.x86_64                     0.4.0-35.lambda2                      lambda2
ghc-tagsoup.x86_64                 0.12.8-4.lambda2                      lambda2
ghc-template-haskell.x86_64        2.8.0.0-26.4.lambda2                  lambda2
ghc-temporary.x86_64               1.1.2.4-4.lambda2                     lambda2
ghc-texmath.x86_64                 0.6.6-2.lambda2                       lambda2
ghc-text.x86_64                    0.11.3.1-2.lambda2                    lambda2
ghc-time.x86_64                    1.4.0.1-26.4.lambda2                  lambda2
ghc-transformers.x86_64            0.3.0.0-34.lambda2                    lambda2
ghc-transformers-base.x86_64       0.4.1-9.lambda2                       lambda2
ghc-unix.x86_64                    2.6.0.1-26.4.lambda2                  lambda2
ghc-unordered-containers.x86_64    0.2.3.0-3.lambda2                     lambda2
ghc-utf8-string.x86_64             0.3.7-8.lambda2                       lambda2
ghc-vector.x86_64                  0.10.0.1-7.lambda2                    lambda2
ghc-void.x86_64                    0.5.11-3.lambda2                      lambda2
ghc-xml.x86_64                     1.3.13-2.lambda2                      lambda2
ghc-yaml.x86_64                    0.8.5.3-2.lambda2                     lambda2
ghc-zip-archive.x86_64             0.1.3.4-3.lambda2                     lambda2
ghc-zlib.x86_64                    0.5.4.1-27.lambda2                    lambda2
ghostscript.x86_64                 9.06-8.lambda2.0.5                    lambda2
ghostscript-fonts.noarch           5.50-32.lambda2                       lambda2
giflib.x86_64                      4.1.6-9.lambda2.0.2                   lambda2
giflib-utils.x86_64                4.1.6-9.lambda2.0.2                   lambda2
git.x86_64                         2.29.0-1.lambda2                      lambda2
git-core.x86_64                    2.29.0-1.lambda2                      lambda2
glib-networking.x86_64             2.56.1-1.lambda2                      lambda2
glib2.x86_64                       2.56.1-5.lambda2.0.1                  lambda2
glibc-devel.x86_64                 2.26-37.lambda2                       lambda2
glibc-headers.x86_64               2.26-37.lambda2                       lambda2
glibc-nss-devel.x86_64             2.26-37.lambda2                       lambda2
glibc-utils.x86_64                 2.26-37.lambda2                       lambda2
gnupg2.x86_64                      2.0.22-5.lambda2.0.4                  lambda2
gnupg2-smime.x86_64                2.0.22-5.lambda2.0.4                  lambda2
gnutls.x86_64                      3.3.29-9.lambda2                      lambda2
gnutls-c++.x86_64                  3.3.29-9.lambda2                      lambda2
gnutls-dane.x86_64                 3.3.29-9.lambda2                      lambda2
gnutls-utils.x86_64                3.3.29-9.lambda2                      lambda2
gobject-introspection.x86_64       1.56.1-1.lambda2                      lambda2
gpgme.x86_64                       1.3.2-5.lambda2.0.2                   lambda2
graphite2.x86_64                   1.3.10-1.lambda2.0.2                  lambda2
groff.x86_64                       1.22.2-8.lambda2.0.2                  lambda2
groff-base.x86_64                  1.22.2-8.lambda2.0.2                  lambda2
groff-perl.x86_64                  1.22.2-8.lambda2.0.2                  lambda2
gsettings-desktop-schemas.x86_64   3.28.0-3.lambda2.0.1                  lambda2
gsm.x86_64                         1.0.13-11.lambda2.0.2                 lambda2
gsm-tools.x86_64                   1.0.13-11.lambda2.0.2                 lambda2
gstreamer.x86_64                   0.10.36-7.lambda2.0.2                 lambda2
gstreamer-plugins-base.x86_64      0.10.36-18.lambda2                    lambda2
gstreamer-plugins-base-tools.x86_64
                                   0.10.36-18.lambda2                    lambda2
gstreamer-tools.x86_64             0.10.36-7.lambda2.0.2                 lambda2
gstreamer1.x86_64                  1.10.4-2.lambda2.0.2                  lambda2
guile.x86_64                       5:2.0.14-3.lambda2.0.2                lambda2
gzip.x86_64                        1.5-10.lambda2                        lambda2
harfbuzz.x86_64                    1.7.5-2.lambda2                       lambda2
harfbuzz-icu.x86_64                1.7.5-2.lambda2                       lambda2
hdf5.x86_64                        1.8.12-11.lambda2                     lambda2
httpd.x86_64                       2.4.46-1.lambda2                      lambda2
httpd-filesystem.noarch            2.4.46-1.lambda2                      lambda2
httpd-tools.x86_64                 2.4.46-1.lambda2                      lambda2
hunspell.x86_64                    1.3.2-16.lambda2                      lambda2
hunspell-en.noarch                 0.20121024-6.lambda2.0.1              lambda2
hunspell-en-GB.noarch              0.20121024-6.lambda2.0.1              lambda2
hunspell-en-US.noarch              0.20121024-6.lambda2.0.1              lambda2
hwdata.x86_64                      0.252-9.3.lambda2                     lambda2
icu.x86_64                         50.2-4.lambda2                        lambda2
ilmbase.x86_64                     1.0.3-7.lambda2.0.2                   lambda2
iputils.x86_64                     20160308-10.lambda2.0.2               lambda2
iso-codes.noarch                   3.46-2.lambda2                        lambda2
jansson.x86_64                     2.10-1.lambda2.0.2                    lambda2
jasper.x86_64                      1.900.1-33.lambda2                    lambda2
jasper-libs.x86_64                 1.900.1-33.lambda2                    lambda2
java-1.8.0-openjdk-devel.x86_64    1:1.8.0.265.b01-1.lambda2.0.1         lambda2
java-1.8.0-openjdk-headless.x86_64 1:1.8.0.265.b01-1.lambda2.0.1         lambda2
jbigkit.x86_64                     2.0-11.lambda2.0.2                    lambda2
jbigkit-libs.x86_64                2.0-11.lambda2.0.2                    lambda2
jemalloc.x86_64                    3.6.0-1.lambda2                       lambda2
jp2a.x86_64                        1.0.7-1.lambda2                       lambda2
json-c.x86_64                      0.11-4.lambda2.0.4                    lambda2
kernel-headers.x86_64              4.14.200-155.322.lambda2              lambda2
kmod.x86_64                        25-3.lambda2.0.2                      lambda2
kmod-libs.x86_64                   25-3.lambda2.0.2                      lambda2
lcms2.x86_64                       2.6-3.lambda2.0.2                     lambda2
lcms2-utils.x86_64                 2.6-3.lambda2.0.2                     lambda2
ldb-tools.x86_64                   1.5.4-1.lambda2                       lambda2
lemon.x86_64                       3.7.17-8.lambda2.1.1                  lambda2
less.x86_64                        458-9.lambda2.0.2                     lambda2
libICE.x86_64                      1.0.9-9.lambda2.0.2                   lambda2
libSM.x86_64                       1.2.2-2.lambda2.0.2                   lambda2
libX11.x86_64                      1.6.7-2.lambda2                       lambda2
libX11-common.noarch               1.6.7-2.lambda2                       lambda2
libXau.x86_64                      1.0.8-2.1.lambda2.0.2                 lambda2
libXaw.x86_64                      1.0.13-4.lambda2.0.2                  lambda2
libXcomposite.x86_64               0.4.4-4.1.lambda2.0.2                 lambda2
libXcursor.x86_64                  1.1.15-1.lambda2                      lambda2
libXdamage.x86_64                  1.1.4-4.1.lambda2.0.2                 lambda2
libXdmcp.x86_64                    1.1.2-6.lambda2.0.2                   lambda2
libXext.x86_64                     1.3.3-3.lambda2.0.2                   lambda2
libXfixes.x86_64                   5.0.3-1.lambda2.0.2                   lambda2
libXfont.x86_64                    1.5.4-1.lambda2                       lambda2
libXft.x86_64                      2.3.2-2.lambda2.0.2                   lambda2
libXi.x86_64                       1.7.9-1.lambda2.0.2                   lambda2
libXinerama.x86_64                 1.1.3-2.1.lambda2.0.2                 lambda2
libXmu.x86_64                      1.1.2-2.lambda2.0.2                   lambda2
libXpm.x86_64                      3.5.12-1.lambda2.0.2                  lambda2
libXrandr.x86_64                   1.5.1-2.lambda2.0.3                   lambda2
libXrender.x86_64                  0.9.10-1.lambda2.0.2                  lambda2
libXt.x86_64                       1.1.5-3.lambda2.0.2                   lambda2
libXtst.x86_64                     1.2.3-1.lambda2.0.2                   lambda2
libXv.x86_64                       1.0.11-1.lambda2.0.2                  lambda2
libXxf86vm.x86_64                  1.1.4-1.lambda2.0.2                   lambda2
libaec.x86_64                      1.0.4-1.lambda2                       lambda2
libaio.x86_64                      0.3.109-13.lambda2.0.2                lambda2
libao.x86_64                       1.1.0-8.lambda2.0.2                   lambda2
libarchive.x86_64                  3.1.2-14.lambda2                      lambda2
libart_lgpl.x86_64                 2.3.21-10.lambda2.0.2                 lambda2
libassuan.x86_64                   2.1.0-3.lambda2.0.2                   lambda2
libasyncns.x86_64                  0.8-7.lambda2.0.2                     lambda2
libatomic.x86_64                   7.3.1-9.lambda2                       lambda2
libatomic_ops.x86_64               7.6.2-3.lambda2.0.1                   lambda2
libblkid.x86_64                    2.30.2-2.lambda2.0.4                  lambda2
libcanberra.x86_64                 0.30-5.lambda2.0.3                    lambda2
libcap-ng.x86_64                   0.7.5-4.lambda2.0.4                   lambda2
libcap-ng-python.x86_64            0.7.5-4.lambda2.0.4                   lambda2
libcap-ng-utils.x86_64             0.7.5-4.lambda2.0.4                   lambda2
libcilkrts.x86_64                  7.3.1-9.lambda2                       lambda2
libcroco.x86_64                    0.6.12-6.lambda2                      lambda2
libcrypt.x86_64                    2.26-37.lambda2                       lambda2
libcrypt-nss.x86_64                2.26-37.lambda2                       lambda2
libcurl.x86_64                     7.61.1-12.lambda2.0.2                 lambda2
libdaemon.x86_64                   0.14-7.lambda2.0.2                    lambda2
libdb.x86_64                       5.3.21-24.lambda2.0.3                 lambda2
libdb-cxx.x86_64                   5.3.21-24.lambda2.0.3                 lambda2
libdb-sql.x86_64                   5.3.21-24.lambda2.0.3                 lambda2
libdb-tcl.x86_64                   5.3.21-24.lambda2.0.3                 lambda2
libdb-utils.x86_64                 5.3.21-24.lambda2.0.3                 lambda2
libdb4.x86_64                      4.8.30-13.lambda2                     lambda2
libdb4-cxx.x86_64                  4.8.30-13.lambda2                     lambda2
libdb4-utils.x86_64                4.8.30-13.lambda2                     lambda2
libdrm.x86_64                      2.4.97-2.lambda2                      lambda2
libedit.x86_64                     3.0-12.20121213cvs.lambda2.0.2        lambda2
libepoxy.x86_64                    1.3.1-2.lambda2                       lambda2
libev.x86_64                       4.24-4.lambda2.0.2                    lambda2
libevent.x86_64                    2.0.21-4.lambda2.0.3                  lambda2
libexif.x86_64                     0.6.22-1.lambda2                      lambda2
libfdisk.x86_64                    2.30.2-2.lambda2.0.4                  lambda2
libfontenc.x86_64                  1.1.3-3.lambda2.0.2                   lambda2
libgccjit.x86_64                   7.3.1-9.lambda2                       lambda2
libgcrypt.x86_64                   1.5.3-14.lambda2.0.2                  lambda2
libgfortran.x86_64                 7.3.1-9.lambda2                       lambda2
libglvnd.x86_64                    1:1.0.1-0.1.git5baa1e5.lambda2.0.1    lambda2
libglvnd-egl.x86_64                1:1.0.1-0.1.git5baa1e5.lambda2.0.1    lambda2
libglvnd-gles.x86_64               1:1.0.1-0.1.git5baa1e5.lambda2.0.1    lambda2
libglvnd-glx.x86_64                1:1.0.1-0.1.git5baa1e5.lambda2.0.1    lambda2
libglvnd-opengl.x86_64             1:1.0.1-0.1.git5baa1e5.lambda2.0.1    lambda2
libgnat.x86_64                     7.3.1-9.lambda2                       lambda2
libgo.x86_64                       7.3.1-9.lambda2                       lambda2
libgomp.x86_64                     7.3.1-9.lambda2                       lambda2
libgpg-error.x86_64                1.12-3.lambda2.0.3                    lambda2
libgsf.x86_64                      1.14.26-7.lambda2.0.2                 lambda2
libgudev1.x86_64                   219-57.lambda2.0.12                   lambda2
libical.x86_64                     3.0.3-2.lambda2.0.1                   lambda2
libical-glib.x86_64                3.0.3-2.lambda2.0.1                   lambda2
libidn.x86_64                      1.28-4.lambda2.0.2                    lambda2
libidn2.x86_64                     2.0.4-1.lambda2.0.2                   lambda2
libimagequant.x86_64               2.12.5-1.lambda2                      lambda2
libiscsi.x86_64                    1.9.0-7.lambda2.0.1                   lambda2
libiscsi-utils.x86_64              1.9.0-7.lambda2.0.1                   lambda2
libitm.x86_64                      7.3.1-9.lambda2                       lambda2
libjpeg-turbo.x86_64               1.2.90-6.lambda2.0.3                  lambda2
libjpeg-turbo-utils.x86_64         1.2.90-6.lambda2.0.3                  lambda2
libksba.x86_64                     1.3.0-5.lambda2.0.2                   lambda2
libldb.x86_64                      1.5.4-1.lambda2                       lambda2
libmcrypt.x86_64                   2.5.8-24.lambda2.0.2                  lambda2
libmetalink.x86_64                 0.1.3-13.lambda2                      lambda2
libmodman.x86_64                   2.0.1-8.lambda2.0.2                   lambda2
libmount.x86_64                    2.30.2-2.lambda2.0.4                  lambda2
libmpc.x86_64                      1.0.1-3.lambda2.0.2                   lambda2
libmpx.x86_64                      7.3.1-9.lambda2                       lambda2
libnghttp2.x86_64                  1.41.0-1.lambda2                      lambda2
libnl3.x86_64                      3.2.28-4.lambda2.0.1                  lambda2
libnl3-cli.x86_64                  3.2.28-4.lambda2.0.1                  lambda2
libnotify.x86_64                   0.7.7-1.lambda2.0.2                   lambda2
libobjc.x86_64                     7.3.1-9.lambda2                       lambda2
libogg.x86_64                      2:1.3.0-7.lambda2.0.2                 lambda2
libpcap.x86_64                     14:1.5.3-11.lambda2                   lambda2
libpciaccess.x86_64                0.14-1.lambda2                        lambda2
libpeas.x86_64                     1.20.0-1.lambda2.0.3                  lambda2
libpng.x86_64                      2:1.5.13-8.lambda2                    lambda2
libprelude.x86_64                  5.2.0-2.lambda2                       lambda2
libproxy.x86_64                    0.4.11-10.lambda2.0.3                 lambda2
libproxy-bin.x86_64                0.4.11-10.lambda2.0.3                 lambda2
libpsl.x86_64                      0.7.0-1.lambda2                       lambda2
libpwquality.x86_64                1.2.3-5.lambda2                       lambda2
libquadmath.x86_64                 7.3.1-9.lambda2                       lambda2
librevenge.x86_64                  0.0.2-2.lambda2.0.2                   lambda2
librsvg2.x86_64                    2.40.20-1.lambda2                     lambda2
librsvg2-tools.x86_64              2.40.20-1.lambda2                     lambda2
libsanitizer.x86_64                7.3.1-9.lambda2                       lambda2
libseccomp.x86_64                  2.4.1-1.lambda2                       lambda2
libsecret.x86_64                   0.18.5-2.lambda2.0.2                  lambda2
libsigc++20.x86_64                 2.10.0-1.lambda2.0.2                  lambda2
libsmartcols.x86_64                2.30.2-2.lambda2.0.4                  lambda2
libsndfile.x86_64                  1.0.25-12.lambda2                     lambda2
libsndfile-utils.x86_64            1.0.25-12.lambda2                     lambda2
libsodium.x86_64                   1.0.18-2.lambda2                      lambda2
libsoup.x86_64                     2.56.0-6.lambda2                      lambda2
libssh2.x86_64                     1.4.3-12.lambda2.2.3                  lambda2
libtalloc.x86_64                   2.1.16-1.lambda2                      lambda2
libtdb.x86_64                      1.3.18-1.lambda2                      lambda2
libtevent.x86_64                   0.9.39-1.lambda2                      lambda2
libthai.x86_64                     0.1.14-9.lambda2.0.2                  lambda2
libtheora.x86_64                   1:1.1.1-8.lambda2.0.2                 lambda2
libtiff.x86_64                     4.0.3-35.lambda2                      lambda2
libtiff-tools.x86_64               4.0.3-35.lambda2                      lambda2
libtirpc.x86_64                    0.2.4-0.16.lambda2                    lambda2
libtool.x86_64                     2.4.2-22.2.lambda2.0.2                lambda2
libtool-ltdl.x86_64                2.4.2-22.2.lambda2.0.2                lambda2
libunistring.x86_64                0.9.3-9.lambda2.0.2                   lambda2
libusb.x86_64                      1:0.1.4-3.lambda2.0.2                 lambda2
libusbx.x86_64                     1.0.21-1.lambda2                      lambda2
libuser.x86_64                     0.60-9.lambda2                        lambda2
libutempter.x86_64                 1.1.6-4.lambda2.0.2                   lambda2
libuuid.x86_64                     2.30.2-2.lambda2.0.4                  lambda2
libv4l.x86_64                      0.9.5-4.lambda2.0.1                   lambda2
libvisual.x86_64                   0.4.0-16.lambda2.0.2                  lambda2
libvoikko.x86_64                   4.1.1-1.lambda2                       lambda2
libvorbis.x86_64                   1:1.3.3-8.lambda2.0.2                 lambda2
libwayland-client.x86_64           1.14.0-2.lambda2.0.1                  lambda2
libwayland-cursor.x86_64           1.14.0-2.lambda2.0.1                  lambda2
libwayland-server.x86_64           1.14.0-2.lambda2.0.1                  lambda2
libwebp.x86_64                     0.3.0-7.lambda2                       lambda2
libwebp-tools.x86_64               0.3.0-7.lambda2                       lambda2
libwkhtmltox.x86_64                1:0.12.5-1.lambda2                    lambda2
libwmf.x86_64                      0.2.8.4-44.lambda2.0.1                lambda2
libwmf-lite.x86_64                 0.2.8.4-44.lambda2.0.1                lambda2
libxcb.x86_64                      1.12-1.lambda2.0.2                    lambda2
libxkbcommon.x86_64                0.7.1-3.lambda2                       lambda2
libxkbcommon-x11.x86_64            0.7.1-3.lambda2                       lambda2
libxml2.x86_64                     2.9.1-6.lambda2.5.1                   lambda2
libxshmfence.x86_64                1.2-1.lambda2.0.2                     lambda2
libxslt.x86_64                     1.1.28-6.lambda2                      lambda2
libyaml.x86_64                     0.1.4-11.lambda2.0.2                  lambda2
libzip.x86_64                      1.3.2-1.lambda2.0.1                   lambda2
libzip-tools.x86_64                1.3.2-1.lambda2.0.1                   lambda2
lksctp-tools.x86_64                1.0.17-2.lambda2.0.2                  lambda2
llvm-private.x86_64                6.0.1-2.lambda2                       lambda2
lm_sensors.x86_64                  3.4.0-8.20160601gitf9185e5.lambda2    lambda2
lm_sensors-libs.x86_64             3.4.0-8.20160601gitf9185e5.lambda2    lambda2
lttng-ust.x86_64                   2.4.1-4.lambda2                       lambda2
lua.x86_64                         5.1.4-15.lambda2.0.2                  lambda2
lz4.x86_64                         1.7.5-2.lambda2.0.1                   lambda2
lzo.x86_64                         2.10-1.lambda2                        lambda2
lzo-minilzo.x86_64                 2.10-1.lambda2                        lambda2
m4.x86_64                          1.4.16-10.lambda2.0.2                 lambda2
mailcap.noarch                     2.1.41-2.lambda2                      lambda2
make.x86_64                        1:3.82-24.lambda2                     lambda2
malaga-suomi-voikko.x86_64         1.12-5.lambda2.0.2                    lambda2
mariadb.x86_64                     1:5.5.68-1.lambda2                    lambda2
mariadb-embedded.x86_64            1:5.5.68-1.lambda2                    lambda2
mariadb-libs.x86_64                1:5.5.68-1.lambda2                    lambda2
mariadb-server.x86_64              1:5.5.68-1.lambda2                    lambda2
matio.x86_64                       1.5.17-3.lambda2                      lambda2
memcached.x86_64                   1.5.17-1.lambda2.0.1                  lambda2
mesa-dri-drivers.x86_64            17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-filesystem.x86_64             17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libEGL.x86_64                 17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libGL.x86_64                  17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libGLES.x86_64                17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libOSMesa.x86_64              17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libgbm.x86_64                 17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libglapi.x86_64               17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libwayland-egl.x86_64         17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-libxatracker.x86_64           17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-vdpau-drivers.x86_64          17.2.3-8.20171019.lambda2.0.4         lambda2
mesa-vulkan-drivers.x86_64         17.2.3-8.20171019.lambda2.0.4         lambda2
mod_http2.x86_64                   1.15.14-2.lambda2                     lambda2
mod_ldap.x86_64                    2.4.46-1.lambda2                      lambda2
mod_md.x86_64                      2.4.46-1.lambda2                      lambda2
mod_proxy_html.x86_64              1:2.4.46-1.lambda2                    lambda2
mod_session.x86_64                 2.4.46-1.lambda2                      lambda2
mod_ssl.x86_64                     1:2.4.46-1.lambda2                    lambda2
mpfr.x86_64                        3.1.1-4.lambda2.0.2                   lambda2
net-snmp.x86_64                    1:5.7.2-48.lambda2.1                  lambda2
net-snmp-agent-libs.x86_64         1:5.7.2-48.lambda2.1                  lambda2
net-snmp-libs.x86_64               1:5.7.2-48.lambda2.1                  lambda2
net-snmp-utils.x86_64              1:5.7.2-48.lambda2.1                  lambda2
netcdf.x86_64                      4.3.3.1-5.lambda2                     lambda2
netpbm.x86_64                      10.79.00-7.lambda2                    lambda2
netpbm-progs.x86_64                10.79.00-7.lambda2                    lambda2
nettle.x86_64                      2.7.1-8.lambda2.0.2                   lambda2
nghttp2.x86_64                     1.41.0-1.lambda2                      lambda2
nscd.x86_64                        2.26-37.lambda2                       lambda2
nss.x86_64                         3.44.0-7.lambda2                      lambda2
nss-pem.x86_64                     1.0.3-5.lambda2                       lambda2
nss-softokn.x86_64                 3.44.0-8.lambda2                      lambda2
nss-sysinit.x86_64                 3.44.0-7.lambda2                      lambda2
nss-tools.x86_64                   3.44.0-7.lambda2                      lambda2
nss_db.x86_64                      2.26-37.lambda2                       lambda2
nss_hesiod.x86_64                  2.26-37.lambda2                       lambda2
nss_nis.x86_64                     2.26-37.lambda2                       lambda2
oniguruma.x86_64                   6.8.2-1.lambda2                       lambda2
opencv.x86_64                      2.4.5-3.lambda2.0.2                   lambda2
opencv-core.x86_64                 2.4.5-3.lambda2.0.2                   lambda2
openjpeg.x86_64                    1.5.1-18.lambda2                      lambda2
openjpeg-libs.x86_64               1.5.1-18.lambda2                      lambda2
openjpeg2.x86_64                   2.3.1-1.lambda2                       lambda2
openjpeg2-tools.x86_64             2.3.1-1.lambda2                       lambda2
openldap.x86_64                    2.4.44-22.lambda2                     lambda2
openldap-clients.x86_64            2.4.44-22.lambda2                     lambda2
openldap-servers.x86_64            2.4.44-22.lambda2                     lambda2
openldap-servers-sql.x86_64        2.4.44-22.lambda2                     lambda2
openslide.x86_64                   3.4.1-1.lambda2                       lambda2
openslide-tools.x86_64             3.4.1-1.lambda2                       lambda2
openssh.x86_64                     7.4p1-21.lambda2.0.1                  lambda2
openssh-cavs.x86_64                7.4p1-21.lambda2.0.1                  lambda2
openssh-clients.x86_64             7.4p1-21.lambda2.0.1                  lambda2
openssh-keycat.x86_64              7.4p1-21.lambda2.0.1                  lambda2
openssh-server.x86_64              7.4p1-21.lambda2.0.1                  lambda2
openssl.x86_64                     1:1.0.2k-19.lambda2.0.3               lambda2
orc.x86_64                         0.4.26-1.lambda2.0.2                  lambda2
pam.x86_64                         1.1.8-23.lambda2.0.1                  lambda2
pandoc.x86_64                      1.12.3.1-2.lambda2                    lambda2
pandoc-pdf.x86_64                  1.12.3.1-2.lambda2                    lambda2
pango.x86_64                       1.42.4-4.lambda2                      lambda2
patch.x86_64                       2.7.1-12.lambda2.0.2                  lambda2
pciutils.x86_64                    3.5.1-3.lambda2                       lambda2
pciutils-libs.x86_64               3.5.1-3.lambda2                       lambda2
pcre2.x86_64                       10.23-2.lambda2.0.2                   lambda2
pcre2-tools.x86_64                 10.23-2.lambda2.0.2                   lambda2
pcre2-utf16.x86_64                 10.23-2.lambda2.0.2                   lambda2
pcre2-utf32.x86_64                 10.23-2.lambda2.0.2                   lambda2
perl.x86_64                        4:5.16.3-294.lambda2                  lambda2
perl-Archive-Tar.noarch            1.92-3.lambda2                        lambda2
perl-BSD-Resource.x86_64           1.29.07-1.lambda2                     lambda2
perl-Business-ISBN.noarch          2.06-2.lambda2                        lambda2
perl-Business-ISBN-Data.noarch     20120719.001-2.lambda2                lambda2
perl-CPAN.noarch                   1.9800-294.lambda2                    lambda2
perl-CPAN-Meta-YAML.noarch         0.008-14.lambda2                      lambda2
perl-Carp.noarch                   1.26-244.lambda2                      lambda2
perl-Compress-Raw-Bzip2.x86_64     2.061-3.lambda2.0.2                   lambda2
perl-Compress-Raw-Zlib.x86_64      1:2.061-4.lambda2.0.2                 lambda2
perl-Crypt-OpenSSL-Bignum.x86_64   0.04-18.lambda2.0.2                   lambda2
perl-Crypt-OpenSSL-RSA.x86_64      0.28-7.lambda2.0.2                    lambda2
perl-Crypt-OpenSSL-Random.x86_64   0.04-21.lambda2.0.2                   lambda2
perl-DBD-MySQL.x86_64              4.023-6.lambda2                       lambda2
perl-DBI.x86_64                    1.627-4.lambda2.0.2                   lambda2
perl-DB_File.x86_64                1.830-6.lambda2.0.2                   lambda2
perl-Data-Dumper.x86_64            2.145-3.lambda2.0.2                   lambda2
perl-Digest.noarch                 1.17-245.lambda2                      lambda2
perl-Digest-HMAC.noarch            1.03-5.lambda2                        lambda2
perl-Digest-MD5.x86_64             2.52-3.lambda2.0.2                    lambda2
perl-Digest-SHA.x86_64             1:5.85-4.lambda2.0.2                  lambda2
perl-Encode.x86_64                 2.51-7.lambda2.0.2                    lambda2
perl-Encode-Detect.x86_64          1.01-13.lambda2.0.2                   lambda2
perl-Encode-Locale.noarch          1.03-5.lambda2                        lambda2
perl-Error.noarch                  1:0.17020-2.lambda2                   lambda2
perl-Exporter.noarch               5.68-3.lambda2                        lambda2
perl-ExtUtils-CBuilder.noarch      1:0.28.2.6-294.lambda2                lambda2
perl-ExtUtils-Embed.noarch         1.30-294.lambda2                      lambda2
perl-ExtUtils-Install.noarch       1.58-294.lambda2                      lambda2
perl-ExtUtils-MakeMaker.noarch     6.68-3.lambda2                        lambda2
perl-ExtUtils-Manifest.noarch      1.61-244.lambda2                      lambda2
perl-File-Listing.noarch           6.04-7.lambda2                        lambda2
perl-File-Path.noarch              2.09-2.lambda2                        lambda2
perl-File-Temp.noarch              0.23.01-3.lambda2                     lambda2
perl-Filter.x86_64                 1.49-3.lambda2.0.2                    lambda2
perl-Getopt-Long.noarch            2.40-3.lambda2                        lambda2
perl-HTML-Parser.x86_64            3.71-4.lambda2.0.2                    lambda2
perl-HTML-Tagset.noarch            3.20-15.lambda2                       lambda2
perl-HTTP-Cookies.noarch           6.01-5.lambda2                        lambda2
perl-HTTP-Daemon.noarch            6.01-8.lambda2                        lambda2
perl-HTTP-Date.noarch              6.02-8.lambda2                        lambda2
perl-HTTP-Message.noarch           6.06-6.lambda2                        lambda2
perl-HTTP-Negotiate.noarch         6.01-5.lambda2                        lambda2
perl-HTTP-Tiny.noarch              0.033-3.lambda2                       lambda2
perl-IO-Compress.noarch            2.061-2.lambda2                       lambda2
perl-IO-HTML.noarch                1.00-2.lambda2                        lambda2
perl-IO-Socket-INET6.noarch        2.69-5.lambda2                        lambda2
perl-IO-Socket-IP.noarch           0.21-5.lambda2                        lambda2
perl-IO-Socket-SSL.noarch          1.94-7.lambda2.0.1                    lambda2
perl-IO-Zlib.noarch                1:1.10-294.lambda2                    lambda2
perl-IPC-Cmd.noarch                1:0.80-4.lambda2                      lambda2
perl-JSON-PP.noarch                2.27202-2.lambda2                     lambda2
perl-LWP-MediaTypes.noarch         6.02-2.lambda2                        lambda2
perl-Locale-Maketext.noarch        1.23-3.lambda2                        lambda2
perl-Locale-Maketext-Simple.noarch 1:0.21-294.lambda2                    lambda2
perl-Mail-DKIM.noarch              0.39-8.lambda2                        lambda2
perl-Mail-SPF.noarch               2.8.0-4.lambda2                       lambda2
perl-MailTools.noarch              2.12-2.lambda2                        lambda2
perl-Module-CoreList.noarch        1:2.76.02-294.lambda2                 lambda2
perl-Module-Load.noarch            1:0.24-3.lambda2                      lambda2
perl-Module-Load-Conditional.noarch
                                   0.54-3.lambda2                        lambda2
perl-Module-Loaded.noarch          1:0.08-294.lambda2                    lambda2
perl-Module-Metadata.noarch        1.000018-2.lambda2                    lambda2
perl-Mozilla-CA.noarch             20130114-5.lambda2                    lambda2
perl-Net-CIDR-Lite.noarch          0.21-11.lambda2                       lambda2
perl-Net-DNS.x86_64                0.72-6.lambda2.0.2                    lambda2
perl-Net-DNS-Nameserver.x86_64     0.72-6.lambda2.0.2                    lambda2
perl-Net-Daemon.noarch             0.48-5.lambda2                        lambda2
perl-Net-HTTP.noarch               6.06-2.lambda2                        lambda2
perl-Net-LibIDN.x86_64             0.12-15.lambda2.0.2                   lambda2
perl-Net-SMTP-SSL.noarch           1.01-13.lambda2                       lambda2
perl-Net-SSLeay.x86_64             1.55-6.lambda2.0.1                    lambda2
perl-NetAddr-IP.x86_64             4.069-3.lambda2.0.2                   lambda2
perl-Object-Accessor.noarch        1:0.42-294.lambda2                    lambda2
perl-Package-Constants.noarch      1:0.02-294.lambda2                    lambda2
perl-Params-Check.noarch           1:0.38-2.lambda2                      lambda2
perl-Parse-CPAN-Meta.noarch        1:1.4404-5.lambda2                    lambda2
perl-PathTools.x86_64              3.40-5.lambda2.0.2                    lambda2
perl-Perl-OSType.noarch            1.003-3.lambda2                       lambda2
perl-PlRPC.noarch                  0.2020-14.lambda2                     lambda2
perl-Pod-Escapes.noarch            1:1.04-294.lambda2                    lambda2
perl-Pod-Perldoc.noarch            3.20-4.lambda2                        lambda2
perl-Pod-Simple.noarch             1:3.28-4.lambda2                      lambda2
perl-Pod-Usage.noarch              1.63-3.lambda2                        lambda2
perl-Scalar-List-Utils.x86_64      1.27-248.lambda2.0.2                  lambda2
perl-Socket.x86_64                 2.010-4.lambda2.0.2                   lambda2
perl-Socket6.x86_64                0.23-15.lambda2.0.2                   lambda2
perl-Storable.x86_64               2.45-3.lambda2.0.2                    lambda2
perl-Sys-Syslog.x86_64             0.33-3.lambda2.0.2                    lambda2
perl-Test-Harness.noarch           3.28-3.lambda2                        lambda2
perl-Text-ParseWords.noarch        3.29-4.lambda2                        lambda2
perl-Thread-Queue.noarch           3.02-2.lambda2                        lambda2
perl-Time-HiRes.x86_64             4:1.9725-3.lambda2.0.2                lambda2
perl-Time-Local.noarch             1.2300-2.lambda2                      lambda2
perl-Time-Piece.x86_64             1.20.1-294.lambda2                    lambda2
perl-TimeDate.noarch               1:2.30-2.lambda2                      lambda2
perl-URI.noarch                    1.60-9.lambda2                        lambda2
perl-WWW-RobotRules.noarch         6.02-5.lambda2                        lambda2
perl-constant.noarch               1.27-2.lambda2.0.1                    lambda2
perl-libs.x86_64                   4:5.16.3-294.lambda2                  lambda2
perl-libwww-perl.noarch            6.05-2.lambda2                        lambda2
perl-local-lib.noarch              1.008010-4.lambda2                    lambda2
perl-macros.x86_64                 4:5.16.3-294.lambda2                  lambda2
perl-parent.noarch                 1:0.225-244.lambda2.0.1               lambda2
perl-podlators.noarch              2.5.1-3.lambda2.0.1                   lambda2
perl-threads.x86_64                1.87-4.lambda2.0.2                    lambda2
perl-threads-shared.x86_64         1.43-6.lambda2.0.2                    lambda2
perl-version.x86_64                3:0.99.07-3.lambda2                   lambda2
php.x86_64                         7.3.23-1.lambda2                      lambda2
php-bcmath.x86_64                  7.3.23-1.lambda2                      lambda2
php-cli.x86_64                     7.3.23-1.lambda2                      lambda2
php-common.x86_64                  7.3.23-1.lambda2                      lambda2
php-dba.x86_64                     7.3.23-1.lambda2                      lambda2
php-dbg.x86_64                     7.3.23-1.lambda2                      lambda2
php-devel.x86_64                   7.3.23-1.lambda2                      lambda2
php-embedded.x86_64                7.3.23-1.lambda2                      lambda2
php-enchant.x86_64                 7.3.23-1.lambda2                      lambda2
php-fpm.x86_64                     7.3.23-1.lambda2                      lambda2
php-gd.x86_64                      7.3.23-1.lambda2                      lambda2
php-gmp.x86_64                     7.3.23-1.lambda2                      lambda2
php-intl.x86_64                    7.3.23-1.lambda2                      lambda2
php-json.x86_64                    7.3.23-1.lambda2                      lambda2
php-ldap.x86_64                    7.3.23-1.lambda2                      lambda2
php-mbstring.x86_64                7.3.23-1.lambda2                      lambda2
php-mysqlnd.x86_64                 7.3.23-1.lambda2                      lambda2
php-odbc.x86_64                    7.3.23-1.lambda2                      lambda2
php-opcache.x86_64                 7.3.23-1.lambda2                      lambda2
php-pdo.x86_64                     7.3.23-1.lambda2                      lambda2
php-pgsql.x86_64                   7.3.23-1.lambda2                      lambda2
php-process.x86_64                 7.3.23-1.lambda2                      lambda2
php-pspell.x86_64                  7.3.23-1.lambda2                      lambda2
php-recode.x86_64                  7.3.23-1.lambda2                      lambda2
php-snmp.x86_64                    7.3.23-1.lambda2                      lambda2
php-soap.x86_64                    7.3.23-1.lambda2                      lambda2
php-sodium.x86_64                  7.3.23-1.lambda2                      lambda2
php-xml.x86_64                     7.3.23-1.lambda2                      lambda2
php-xmlrpc.x86_64                  7.3.23-1.lambda2                      lambda2
pinentry.x86_64                    0.8.1-17.lambda2.0.2                  lambda2
pixman.x86_64                      0.34.0-1.lambda2.0.2                  lambda2
pkgconfig.x86_64                   1:0.27.1-4.lambda2.0.2                lambda2
poppler.x86_64                     0.26.5-43.lambda2                     lambda2
poppler-cpp.x86_64                 0.26.5-43.lambda2                     lambda2
poppler-data.noarch                0.4.6-3.lambda2.0.1                   lambda2
poppler-glib.x86_64                0.26.5-43.lambda2                     lambda2
poppler-utils.x86_64               0.26.5-43.lambda2                     lambda2
postgresql.x86_64                  9.2.24-1.lambda2.0.1                  lambda2
postgresql-contrib.x86_64          9.2.24-1.lambda2.0.1                  lambda2
postgresql-libs.x86_64             9.2.24-1.lambda2.0.1                  lambda2
postgresql-server.x86_64           9.2.24-1.lambda2.0.1                  lambda2
prelude-tools.x86_64               5.2.0-2.lambda2                       lambda2
procmail.x86_64                    3.22-36.lambda2.1.2                   lambda2
procps-ng.x86_64                   3.3.10-26.lambda2                     lambda2
procps-ng-i18n.x86_64              3.3.10-26.lambda2                     lambda2
psl.x86_64                         0.7.0-1.lambda2                       lambda2
psmisc.x86_64                      22.20-15.lambda2.0.2                  lambda2
pth.x86_64                         2.0.7-23.lambda2.0.2                  lambda2
pugixml.x86_64                     1.8-1.lambda2                         lambda2
pulseaudio-libs.x86_64             10.0-3.lambda2.0.3                    lambda2
pulseaudio-libs-glib2.x86_64       10.0-3.lambda2.0.3                    lambda2
pulseaudio-utils.x86_64            10.0-3.lambda2.0.3                    lambda2
python.x86_64                      2.7.18-1.lambda2.0.2                  lambda2
python-libs.x86_64                 2.7.18-1.lambda2.0.2                  lambda2
python2-pip.noarch                 9.0.3-1.lambda2.0.1                   lambda2
python2-setuptools.noarch          38.4.0-3.lambda2.0.6                  lambda2
python3.x86_64                     3.7.9-1.lambda2.0.1                   lambda2
python3-libs.x86_64                3.7.9-1.lambda2.0.1                   lambda2
python3-pip.noarch                 9.0.3-1.lambda2.0.1                   lambda2
python3-setuptools.noarch          38.4.0-3.lambda2.0.6                  lambda2
readline.x86_64                    6.2-10.lambda2.0.2                    lambda2
recode.x86_64                      3.6-38.lambda2.0.1                    lambda2
redis.x86_64                       4.0.10-2.lambda2.0.2                  lambda2
redis-trib.noarch                  4.0.10-2.lambda2.0.2                  lambda2
rpm.x86_64                         4.11.3-40.lambda2.0.5                 lambda2
rpm-libs.x86_64                    4.11.3-40.lambda2.0.5                 lambda2
ruby.x86_64                        2.6.6-125.lambda2.0.3                 lambda2
ruby-libs.x86_64                   2.6.6-125.lambda2.0.3                 lambda2
rubygem-bigdecimal.x86_64          1.4.1-125.lambda2.0.3                 lambda2
rubygem-bundler.noarch             1.17.2-125.lambda2.0.3                lambda2
rubygem-did_you_mean.noarch        1.3.0-125.lambda2.0.3                 lambda2
rubygem-io-console.x86_64          0.4.7-125.lambda2.0.3                 lambda2
rubygem-irb.noarch                 1.0.0-125.lambda2.0.3                 lambda2
rubygem-json.x86_64                2.1.0-125.lambda2.0.3                 lambda2
rubygem-minitest.noarch            5.11.3-125.lambda2.0.3                lambda2
rubygem-net-telnet.noarch          0.2.0-125.lambda2.0.3                 lambda2
rubygem-openssl.x86_64             2.1.2-125.lambda2.0.3                 lambda2
rubygem-power_assert.noarch        1.1.3-125.lambda2.0.3                 lambda2
rubygem-psych.x86_64               3.1.0-125.lambda2.0.3                 lambda2
rubygem-rake.noarch                12.3.3-125.lambda2.0.3                lambda2
rubygem-rdoc.noarch                6.1.2-125.lambda2.0.3                 lambda2
rubygem-redis.noarch               3.2.2-5.lambda2                       lambda2
rubygem-test-unit.noarch           3.2.9-125.lambda2.0.3                 lambda2
rubygem-xmlrpc.noarch              0.3.0-125.lambda2.0.3                 lambda2
rubygems.noarch                    3.0.3-125.lambda2.0.3                 lambda2
sgml-common.noarch                 0.6.3-39.lambda2                      lambda2
shared-mime-info.x86_64            1.8-4.lambda2                         lambda2
snappy.x86_64                      1.1.0-3.lambda2.0.2                   lambda2
sound-theme-freedesktop.noarch     0.8-3.lambda2                         lambda2
sox.x86_64                         14.4.1-7.lambda2                      lambda2
spamassassin.x86_64                3.4.3-2.2.lambda2                     lambda2
sqlite.x86_64                      3.7.17-8.lambda2.1.1                  lambda2
sqlite-libs.x86_64                 3.7.17-8.lambda2.1.1                  lambda2
stix-fonts.noarch                  1.1.0-5.lambda2                       lambda2
stix-math-fonts.noarch             1.1.0-5.lambda2                       lambda2
systemd-libs.x86_64                219-57.lambda2.0.12                   lambda2
t1lib.x86_64                       5.1.2-14.lambda2.0.2                  lambda2
tar.x86_64                         2:1.26-35.lambda2                     lambda2
tcp_wrappers.x86_64                7.6-77.lambda2.0.2                    lambda2
tcp_wrappers-libs.x86_64           7.6-77.lambda2.0.2                    lambda2
tdb-tools.x86_64                   1.3.18-1.lambda2                      lambda2
teckit.x86_64                      2.5.1-11.lambda2.0.2                  lambda2
texlive.x86_64                     2:2012-38.20130427_r30134.lambda2.0.5 lambda2
texlive-adjustbox.noarch           2:svn26555.0-38.lambda2.0.5           lambda2
texlive-ae.noarch                  2:svn15878.1.4-38.lambda2.0.5         lambda2
texlive-algorithms.noarch          2:svn15878.0.1-38.lambda2.0.5         lambda2
texlive-amscls.noarch              2:svn29207.0-38.lambda2.0.5           lambda2
texlive-amsfonts.noarch            2:svn29208.3.04-38.lambda2.0.5        lambda2
texlive-amsmath.noarch             2:svn29327.2.14-38.lambda2.0.5        lambda2
texlive-anysize.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-appendix.noarch            2:svn15878.1.2b-38.lambda2.0.5        lambda2
texlive-arabxetex.noarch           2:svn17470.v1.1.4-38.lambda2.0.5      lambda2
texlive-arphic.noarch              2:svn15878.0-38.lambda2.0.5           lambda2
texlive-attachfile.noarch          2:svn21866.v1.5b-38.lambda2.0.5       lambda2
texlive-avantgar.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
texlive-babel.noarch               2:svn24756.3.8m-38.lambda2.0.5        lambda2
texlive-babelbib.noarch            2:svn25245.1.31-38.lambda2.0.5        lambda2
texlive-base.noarch                2:2012-38.20130427_r30134.lambda2.0.5 lambda2
texlive-beamer.noarch              2:svn29349.3.26-38.lambda2.0.5        lambda2
texlive-bera.noarch                2:svn20031.0-38.lambda2.0.5           lambda2
texlive-beton.noarch               2:svn15878.0-38.lambda2.0.5           lambda2
texlive-bibtex.noarch              2:svn26689.0.99d-38.lambda2.0.5       lambda2
texlive-bibtex-bin.x86_64          2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-bibtopic.noarch            2:svn15878.1.1a-38.lambda2.0.5        lambda2
texlive-bidi.noarch                2:svn29650.12.2-38.lambda2.0.5        lambda2
texlive-bigfoot.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-bookman.noarch             2:svn28614.0-38.lambda2.0.5           lambda2
texlive-booktabs.noarch            2:svn15878.1.61803-38.lambda2.0.5     lambda2
texlive-breakurl.noarch            2:svn15878.1.30-38.lambda2.0.5        lambda2
texlive-caption.noarch             2:svn29026.3.3__2013_02_03_-38.lambda2.0.5
                                                                         lambda2
texlive-carlisle.noarch            2:svn18258.0-38.lambda2.0.5           lambda2
texlive-changebar.noarch           2:svn29349.3.5c-38.lambda2.0.5        lambda2
texlive-changepage.noarch          2:svn15878.1.0c-38.lambda2.0.5        lambda2
texlive-charter.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-chngcntr.noarch            2:svn17157.1.0a-38.lambda2.0.5        lambda2
texlive-cite.noarch                2:svn19955.5.3-38.lambda2.0.5         lambda2
texlive-cjk.noarch                 2:svn26296.4.8.3-38.lambda2.0.5       lambda2
texlive-cm.noarch                  2:svn29581.0-38.lambda2.0.5           lambda2
texlive-cm-lgc.noarch              2:svn28250.0.5-38.lambda2.0.5         lambda2
texlive-cm-super.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-cmap.noarch                2:svn26568.0-38.lambda2.0.5           lambda2
texlive-cmextra.noarch             2:svn14075.0-38.lambda2.0.5           lambda2
texlive-cns.noarch                 2:svn15878.0-38.lambda2.0.5           lambda2
texlive-collectbox.noarch          2:svn26557.0-38.lambda2.0.5           lambda2
texlive-collection-basic.noarch    2:svn26314.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-collection-fontsrecommended.noarch
                                   2:svn28082.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-collection-htmlxml.noarch  2:svn28251.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-collection-latex.noarch    2:svn25030.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-collection-latexrecommended.noarch
                                   2:svn25795.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-collection-xetex.noarch    2:svn29634.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-colortbl.noarch            2:svn25394.v1.0a-38.lambda2.0.5       lambda2
texlive-courier.noarch             2:svn28614.0-38.lambda2.0.5           lambda2
texlive-crop.noarch                2:svn15878.1.5-38.lambda2.0.5         lambda2
texlive-csquotes.noarch            2:svn24393.5.1d-38.lambda2.0.5        lambda2
texlive-ctable.noarch              2:svn26694.1.23-38.lambda2.0.5        lambda2
texlive-currfile.noarch            2:svn29012.0.7b-38.lambda2.0.5        lambda2
texlive-datetime.noarch            2:svn19834.2.58-38.lambda2.0.5        lambda2
texlive-dvipdfm.noarch             2:svn26689.0.13.2d-38.lambda2.0.5     lambda2
texlive-dvipdfm-bin.x86_64         2:svn13663.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-dvipdfmx.noarch            2:svn26765.0-38.lambda2.0.5           lambda2
texlive-dvipdfmx-bin.x86_64        2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-dvipdfmx-def.noarch        2:svn15878.0-38.lambda2.0.5           lambda2
texlive-dvipng.noarch              2:svn26689.1.14-38.lambda2.0.5        lambda2
texlive-dvipng-bin.x86_64          2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-dvips.noarch               2:svn29585.0-38.lambda2.0.5           lambda2
texlive-dvips-bin.x86_64           2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-ec.noarch                  2:svn25033.1.0-38.lambda2.0.5         lambda2
texlive-eepic.noarch               2:svn15878.1.1e-38.lambda2.0.5        lambda2
texlive-enctex.noarch              2:svn28602.0-38.lambda2.0.5           lambda2
texlive-enumitem.noarch            2:svn24146.3.5.2-38.lambda2.0.5       lambda2
texlive-epsf.noarch                2:svn21461.2.7.4-38.lambda2.0.5       lambda2
texlive-epstopdf.noarch            2:svn26577.0-38.lambda2.0.5           lambda2
texlive-epstopdf-bin.noarch        2:svn18336.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-eso-pic.noarch             2:svn21515.2.0c-38.lambda2.0.5        lambda2
texlive-etex.noarch                2:svn22198.2.1-38.lambda2.0.5         lambda2
texlive-etex-pkg.noarch            2:svn15878.2.0-38.lambda2.0.5         lambda2
texlive-etoolbox.noarch            2:svn20922.2.1-38.lambda2.0.5         lambda2
texlive-euenc.noarch               2:svn19795.0.1h-38.lambda2.0.5        lambda2
texlive-euler.noarch               2:svn17261.2.5-38.lambda2.0.5         lambda2
texlive-euro.noarch                2:svn22191.1.1-38.lambda2.0.5         lambda2
texlive-eurosym.noarch             2:svn17265.1.4_subrfix-38.lambda2.0.5 lambda2
texlive-extsizes.noarch            2:svn17263.1.4a-38.lambda2.0.5        lambda2
texlive-fancybox.noarch            2:svn18304.1.4-38.lambda2.0.5         lambda2
texlive-fancyhdr.noarch            2:svn15878.3.1-38.lambda2.0.5         lambda2
texlive-fancyref.noarch            2:svn15878.0.9c-38.lambda2.0.5        lambda2
texlive-fancyvrb.noarch            2:svn18492.2.8-38.lambda2.0.5         lambda2
texlive-filecontents.noarch        2:svn24250.1.3-38.lambda2.0.5         lambda2
texlive-filehook.noarch            2:svn24280.0.5d-38.lambda2.0.5        lambda2
texlive-fix2col.noarch             2:svn17133.0-38.lambda2.0.5           lambda2
texlive-fixlatvian.noarch          2:svn21631.1a-38.lambda2.0.5          lambda2
texlive-float.noarch               2:svn15878.1.3d-38.lambda2.0.5        lambda2
texlive-fmtcount.noarch            2:svn28068.2.02-38.lambda2.0.5        lambda2
texlive-fncychap.noarch            2:svn20710.v1.34-38.lambda2.0.5       lambda2
texlive-fontbook.noarch            2:svn23608.0.2-38.lambda2.0.5         lambda2
texlive-fontspec.noarch            2:svn29412.v2.3a-38.lambda2.0.5       lambda2
texlive-fontware.noarch            2:svn26689.0-38.lambda2.0.5           lambda2
texlive-fontware-bin.x86_64        2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-fontwrap.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-footmisc.noarch            2:svn23330.5.5b-38.lambda2.0.5        lambda2
texlive-fp.noarch                  2:svn15878.0-38.lambda2.0.5           lambda2
texlive-fpl.noarch                 2:svn15878.1.002-38.lambda2.0.5       lambda2
texlive-framed.noarch              2:svn26789.0.96-38.lambda2.0.5        lambda2
texlive-garuda-c90.noarch          2:svn15878.0-38.lambda2.0.5           lambda2
texlive-geometry.noarch            2:svn19716.5.6-38.lambda2.0.5         lambda2
texlive-glyphlist.noarch           2:svn28576.0-38.lambda2.0.5           lambda2
texlive-graphics.noarch            2:svn25405.1.0o-38.lambda2.0.5        lambda2
texlive-gsftopk.noarch             2:svn26689.1.19.2-38.lambda2.0.5      lambda2
texlive-gsftopk-bin.x86_64         2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-helvetic.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
texlive-hyperref.noarch            2:svn28213.6.83m-38.lambda2.0.5       lambda2
texlive-hyph-utf8.noarch           2:svn29641.0-38.lambda2.0.5           lambda2
texlive-hyphen-base.noarch         2:svn29197.0-38.lambda2.0.5           lambda2
texlive-hyphenat.noarch            2:svn15878.2.3c-38.lambda2.0.5        lambda2
texlive-ifetex.noarch              2:svn24853.1.2-38.lambda2.0.5         lambda2
texlive-ifluatex.noarch            2:svn26725.1.3-38.lambda2.0.5         lambda2
texlive-ifmtarg.noarch             2:svn19363.1.2a-38.lambda2.0.5        lambda2
texlive-ifoddpage.noarch           2:svn23979.0-38.lambda2.0.5           lambda2
texlive-iftex.noarch               2:svn29654.0.2-38.lambda2.0.5         lambda2
texlive-ifxetex.noarch             2:svn19685.0.5-38.lambda2.0.5         lambda2
texlive-index.noarch               2:svn24099.4.1beta-38.lambda2.0.5     lambda2
texlive-jadetex.noarch             2:svn23409.3.13-38.lambda2.0.5        lambda2
texlive-jadetex-bin.x86_64         2:svn3006.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-jknapltx.noarch            2:svn19440.0-38.lambda2.0.5           lambda2
texlive-kastrup.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-kerkis.noarch              2:svn15878.0-38.lambda2.0.5           lambda2
texlive-koma-script.noarch         2:svn27255.3.11b-38.lambda2.0.5       lambda2
texlive-kpathsea.noarch            2:svn28792.0-38.lambda2.0.5           lambda2
texlive-kpathsea-bin.x86_64        2:svn27347.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-kpathsea-lib.x86_64        2:2012-38.20130427_r30134.lambda2.0.5 lambda2
texlive-l3experimental.noarch      2:svn29361.SVN_4467-38.lambda2.0.5    lambda2
texlive-l3kernel.noarch            2:svn29409.SVN_4469-38.lambda2.0.5    lambda2
texlive-l3packages.noarch          2:svn29361.SVN_4467-38.lambda2.0.5    lambda2
texlive-lastpage.noarch            2:svn28985.1.2l-38.lambda2.0.5        lambda2
texlive-latex.noarch               2:svn27907.0-38.lambda2.0.5           lambda2
texlive-latex-bin.noarch           2:svn26689.0-38.lambda2.0.5           lambda2
texlive-latex-bin-bin.x86_64       2:svn14050.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-latex-fonts.noarch         2:svn28888.0-38.lambda2.0.5           lambda2
texlive-latexconfig.noarch         2:svn28991.0-38.lambda2.0.5           lambda2
texlive-lettrine.noarch            2:svn29391.1.64-38.lambda2.0.5        lambda2
texlive-listings.noarch            2:svn15878.1.4-38.lambda2.0.5         lambda2
texlive-lm.noarch                  2:svn28119.2.004-38.lambda2.0.5       lambda2
texlive-lm-math.noarch             2:svn29044.1.958-38.lambda2.0.5       lambda2
texlive-ltxmisc.noarch             2:svn21927.0-38.lambda2.0.5           lambda2
texlive-lua-alt-getopt.noarch      2:svn29349.0.7.0-38.lambda2.0.5       lambda2
texlive-lualatex-math.noarch       2:svn29346.1.2-38.lambda2.0.5         lambda2
texlive-luaotfload.noarch          2:svn26718.1.26-38.lambda2.0.5        lambda2
texlive-luaotfload-bin.noarch      2:svn18579.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-luatex.noarch              2:svn26689.0.70.1-38.lambda2.0.5      lambda2
texlive-luatex-bin.x86_64          2:svn26912.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-luatexbase.noarch          2:svn22560.0.31-38.lambda2.0.5        lambda2
texlive-makecmds.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-makeindex.noarch           2:svn26689.2.12-38.lambda2.0.5        lambda2
texlive-makeindex-bin.x86_64       2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-marginnote.noarch          2:svn25880.v1.1i-38.lambda2.0.5       lambda2
texlive-marvosym.noarch            2:svn29349.2.2a-38.lambda2.0.5        lambda2
texlive-mathpazo.noarch            2:svn15878.1.003-38.lambda2.0.5       lambda2
texlive-mathspec.noarch            2:svn15878.0.2-38.lambda2.0.5         lambda2
texlive-mdwtools.noarch            2:svn15878.1.05.4-38.lambda2.0.5      lambda2
texlive-memoir.noarch              2:svn21638.3.6j_patch_6.0g-38.lambda2.0.5
                                                                         lambda2
texlive-metafont.noarch            2:svn26689.2.718281-38.lambda2.0.5    lambda2
texlive-metafont-bin.x86_64        2:svn26912.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-metalogo.noarch            2:svn18611.0.12-38.lambda2.0.5        lambda2
texlive-metapost.noarch            2:svn26689.1.212-38.lambda2.0.5       lambda2
texlive-metapost-bin.x86_64        2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-mflogo.noarch              2:svn17487.0-38.lambda2.0.5           lambda2
texlive-mfnfss.noarch              2:svn19410.0-38.lambda2.0.5           lambda2
texlive-mfware.noarch              2:svn26689.0-38.lambda2.0.5           lambda2
texlive-mfware-bin.x86_64          2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-mh.noarch                  2:svn29420.0-38.lambda2.0.5           lambda2
texlive-microtype.noarch           2:svn29392.2.5-38.lambda2.0.5         lambda2
texlive-misc.noarch                2:svn24955.0-38.lambda2.0.5           lambda2
texlive-mnsymbol.noarch            2:svn18651.1.4-38.lambda2.0.5         lambda2
texlive-mparhack.noarch            2:svn15878.1.4-38.lambda2.0.5         lambda2
texlive-mptopdf.noarch             2:svn26689.0-38.lambda2.0.5           lambda2
texlive-mptopdf-bin.noarch         2:svn18674.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-ms.noarch                  2:svn24467.0-38.lambda2.0.5           lambda2
texlive-multido.noarch             2:svn18302.1.42-38.lambda2.0.5        lambda2
texlive-multirow.noarch            2:svn17256.1.6-38.lambda2.0.5         lambda2
texlive-natbib.noarch              2:svn20668.8.31b-38.lambda2.0.5       lambda2
texlive-ncctools.noarch            2:svn15878.3.5-38.lambda2.0.5         lambda2
texlive-ncntrsbk.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
texlive-norasi-c90.noarch          2:svn15878.0-38.lambda2.0.5           lambda2
texlive-ntgclass.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-oberdiek.noarch            2:svn26725.0-38.lambda2.0.5           lambda2
texlive-overpic.noarch             2:svn19712.0.53-38.lambda2.0.5        lambda2
texlive-palatino.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
texlive-paralist.noarch            2:svn15878.2.3b-38.lambda2.0.5        lambda2
texlive-parallel.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-parskip.noarch             2:svn19963.2.0-38.lambda2.0.5         lambda2
texlive-passivetex.noarch          2:svn15878.0-38.lambda2.0.5           lambda2
texlive-pdfpages.noarch            2:svn27574.0.4t-38.lambda2.0.5        lambda2
texlive-pdftex.noarch              2:svn29585.1.40.11-38.lambda2.0.5     lambda2
texlive-pdftex-bin.x86_64          2:svn27321.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-pdftex-def.noarch          2:svn22653.0.06d-38.lambda2.0.5       lambda2
texlive-pgf.noarch                 2:svn22614.2.10-38.lambda2.0.5        lambda2
texlive-philokalia.noarch          2:svn18651.1.1-38.lambda2.0.5         lambda2
texlive-placeins.noarch            2:svn19848.2.2-38.lambda2.0.5         lambda2
texlive-plain.noarch               2:svn26647.0-38.lambda2.0.5           lambda2
texlive-polyglossia.noarch         2:svn26163.v1.2.1-38.lambda2.0.5      lambda2
texlive-powerdot.noarch            2:svn25656.1.4i-38.lambda2.0.5        lambda2
texlive-preprint.noarch            2:svn16085.0-38.lambda2.0.5           lambda2
texlive-psfrag.noarch              2:svn15878.3.04-38.lambda2.0.5        lambda2
texlive-pslatex.noarch             2:svn16416.0-38.lambda2.0.5           lambda2
texlive-psnfss.noarch              2:svn23394.9.2a-38.lambda2.0.5        lambda2
texlive-pspicture.noarch           2:svn15878.0-38.lambda2.0.5           lambda2
texlive-pst-3d.noarch              2:svn17257.1.10-38.lambda2.0.5        lambda2
texlive-pst-blur.noarch            2:svn15878.2.0-38.lambda2.0.5         lambda2
texlive-pst-coil.noarch            2:svn24020.1.06-38.lambda2.0.5        lambda2
texlive-pst-eps.noarch             2:svn15878.1.0-38.lambda2.0.5         lambda2
texlive-pst-fill.noarch            2:svn15878.1.01-38.lambda2.0.5        lambda2
texlive-pst-grad.noarch            2:svn15878.1.06-38.lambda2.0.5        lambda2
texlive-pst-math.noarch            2:svn20176.0.61-38.lambda2.0.5        lambda2
texlive-pst-node.noarch            2:svn27799.1.25-38.lambda2.0.5        lambda2
texlive-pst-plot.noarch            2:svn28729.1.44-38.lambda2.0.5        lambda2
texlive-pst-slpe.noarch            2:svn24391.1.31-38.lambda2.0.5        lambda2
texlive-pst-text.noarch            2:svn15878.1.00-38.lambda2.0.5        lambda2
texlive-pst-tree.noarch            2:svn24142.1.12-38.lambda2.0.5        lambda2
texlive-pstricks.noarch            2:svn29678.2.39-38.lambda2.0.5        lambda2
texlive-pstricks-add.noarch        2:svn28750.3.59-38.lambda2.0.5        lambda2
texlive-ptext.noarch               2:svn28124.1-38.lambda2.0.5           lambda2
texlive-pxfonts.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-qstest.noarch              2:svn15878.0-38.lambda2.0.5           lambda2
texlive-rcs.noarch                 2:svn15878.0-38.lambda2.0.5           lambda2
texlive-realscripts.noarch         2:svn29423.0.3b-38.lambda2.0.5        lambda2
texlive-rotating.noarch            2:svn16832.2.16b-38.lambda2.0.5       lambda2
texlive-rsfs.noarch                2:svn15878.0-38.lambda2.0.5           lambda2
texlive-sansmath.noarch            2:svn17997.1.1-38.lambda2.0.5         lambda2
texlive-sauerj.noarch              2:svn15878.0-38.lambda2.0.5           lambda2
texlive-scheme-basic.noarch        2:svn25923.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-section.noarch             2:svn20180.0-38.lambda2.0.5           lambda2
texlive-sectsty.noarch             2:svn15878.2.0.2-38.lambda2.0.5       lambda2
texlive-seminar.noarch             2:svn18322.1.5-38.lambda2.0.5         lambda2
texlive-sepnum.noarch              2:svn20186.2.0-38.lambda2.0.5         lambda2
texlive-setspace.noarch            2:svn24881.6.7a-38.lambda2.0.5        lambda2
texlive-showexpl.noarch            2:svn27790.v0.3j-38.lambda2.0.5       lambda2
texlive-soul.noarch                2:svn15878.2.4-38.lambda2.0.5         lambda2
texlive-stmaryrd.noarch            2:svn22027.0-38.lambda2.0.5           lambda2
texlive-subfig.noarch              2:svn15878.1.3-38.lambda2.0.5         lambda2
texlive-subfigure.noarch           2:svn15878.2.1.5-38.lambda2.0.5       lambda2
texlive-svn-prov.noarch            2:svn18017.3.1862-38.lambda2.0.5      lambda2
texlive-symbol.noarch              2:svn28614.0-38.lambda2.0.5           lambda2
texlive-t2.noarch                  2:svn29349.0-38.lambda2.0.5           lambda2
texlive-tetex.noarch               2:svn29585.3.0-38.lambda2.0.5         lambda2
texlive-tetex-bin.noarch           2:svn27344.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-tex.noarch                 2:svn26689.3.1415926-38.lambda2.0.5   lambda2
texlive-tex-bin.x86_64             2:svn26912.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-tex-gyre.noarch            2:svn18651.2.004-38.lambda2.0.5       lambda2
texlive-tex-gyre-math.noarch       2:svn29045.0-38.lambda2.0.5           lambda2
texlive-tex4ht.noarch              2:svn29474.0-38.lambda2.0.5           lambda2
texlive-tex4ht-bin.x86_64          2:svn26509.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-texconfig.noarch           2:svn29349.0-38.lambda2.0.5           lambda2
texlive-texconfig-bin.noarch       2:svn27344.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-texlive.infra.noarch       2:svn28217.0-38.lambda2.0.5           lambda2
texlive-texlive.infra-bin.x86_64   2:svn22566.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-textcase.noarch            2:svn15878.0-38.lambda2.0.5           lambda2
texlive-textpos.noarch             2:svn28261.1.7h-38.lambda2.0.5        lambda2
texlive-thailatex.noarch           2:svn29349.0.5.1-38.lambda2.0.5       lambda2
texlive-threeparttable.noarch      2:svn17383.0-38.lambda2.0.5           lambda2
texlive-thumbpdf.noarch            2:svn26689.3.15-38.lambda2.0.5        lambda2
texlive-thumbpdf-bin.noarch        2:svn6898.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-times.noarch               2:svn28614.0-38.lambda2.0.5           lambda2
texlive-tipa.noarch                2:svn29349.1.3-38.lambda2.0.5         lambda2
texlive-titlesec.noarch            2:svn24852.2.10.0-38.lambda2.0.5      lambda2
texlive-titling.noarch             2:svn15878.2.1d-38.lambda2.0.5        lambda2
texlive-tocloft.noarch             2:svn20084.2.3e-38.lambda2.0.5        lambda2
texlive-tools.noarch               2:svn26263.0-38.lambda2.0.5           lambda2
texlive-txfonts.noarch             2:svn15878.0-38.lambda2.0.5           lambda2
texlive-type1cm.noarch             2:svn21820.0-38.lambda2.0.5           lambda2
texlive-typehtml.noarch            2:svn17134.0-38.lambda2.0.5           lambda2
texlive-ucharclasses.noarch        2:svn27820.2.0-38.lambda2.0.5         lambda2
texlive-ucs.noarch                 2:svn27549.2.1-38.lambda2.0.5         lambda2
texlive-uhc.noarch                 2:svn16791.0-38.lambda2.0.5           lambda2
texlive-ulem.noarch                2:svn26785.0-38.lambda2.0.5           lambda2
texlive-underscore.noarch          2:svn18261.0-38.lambda2.0.5           lambda2
texlive-unicode-math.noarch        2:svn29413.0.7d-38.lambda2.0.5        lambda2
texlive-unisugar.noarch            2:svn22357.0.92-38.lambda2.0.5        lambda2
texlive-url.noarch                 2:svn16864.3.2-38.lambda2.0.5         lambda2
texlive-utopia.noarch              2:svn15878.0-38.lambda2.0.5           lambda2
texlive-varwidth.noarch            2:svn24104.0.92-38.lambda2.0.5        lambda2
texlive-wadalab.noarch             2:svn22576.0-38.lambda2.0.5           lambda2
texlive-was.noarch                 2:svn21439.0-38.lambda2.0.5           lambda2
texlive-wasy.noarch                2:svn15878.0-38.lambda2.0.5           lambda2
texlive-wasysym.noarch             2:svn15878.2.0-38.lambda2.0.5         lambda2
texlive-wrapfig.noarch             2:svn22048.3.6-38.lambda2.0.5         lambda2
texlive-xcolor.noarch              2:svn15878.2.11-38.lambda2.0.5        lambda2
texlive-xecjk.noarch               2:svn28816.3.1.2-38.lambda2.0.5       lambda2
texlive-xecolor.noarch             2:svn29660.0.1-38.lambda2.0.5         lambda2
texlive-xecyr.noarch               2:svn20221.1.1-38.lambda2.0.5         lambda2
texlive-xeindex.noarch             2:svn16760.0.2-38.lambda2.0.5         lambda2
texlive-xepersian.noarch           2:svn29661.12.1-38.lambda2.0.5        lambda2
texlive-xesearch.noarch            2:svn16041.0-38.lambda2.0.5           lambda2
texlive-xetex.noarch               2:svn26330.0.9997.5-38.lambda2.0.5    lambda2
texlive-xetex-bin.x86_64           2:svn26912.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-xetex-def.noarch           2:svn29154.0.95-38.lambda2.0.5        lambda2
texlive-xetex-itrans.noarch        2:svn24105.4.0-38.lambda2.0.5         lambda2
texlive-xetex-pstricks.noarch      2:svn17055.0-38.lambda2.0.5           lambda2
texlive-xetex-tibetan.noarch       2:svn28847.0.1-38.lambda2.0.5         lambda2
texlive-xetexconfig.noarch         2:svn28819.0-38.lambda2.0.5           lambda2
texlive-xetexfontinfo.noarch       2:svn15878.0-38.lambda2.0.5           lambda2
texlive-xifthen.noarch             2:svn15878.1.3-38.lambda2.0.5         lambda2
texlive-xkeyval.noarch             2:svn27995.2.6a-38.lambda2.0.5        lambda2
texlive-xltxtra.noarch             2:svn19809.0.5e-38.lambda2.0.5        lambda2
texlive-xmltex.noarch              2:svn28273.0.8-38.lambda2.0.5         lambda2
texlive-xmltex-bin.x86_64          2:svn3006.0-38.20130427_r30134.lambda2.0.5
                                                                         lambda2
texlive-xstring.noarch             2:svn29258.1.7a-38.lambda2.0.5        lambda2
texlive-xtab.noarch                2:svn23347.2.3f-38.lambda2.0.5        lambda2
texlive-xunicode.noarch            2:svn23897.0.981-38.lambda2.0.5       lambda2
texlive-zapfchan.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
texlive-zapfding.noarch            2:svn28614.0-38.lambda2.0.5           lambda2
theora-tools.x86_64                1:1.1.1-8.lambda2.0.2                 lambda2
tinyxml.x86_64                     2.6.2-3.lambda2                       lambda2
tokyocabinet.x86_64                1.4.48-3.lambda2.0.2                  lambda2
transfig.x86_64                    1:3.2.7b-2.lambda2                    lambda2
trousers.x86_64                    0.3.14-2.lambda2.0.2                  lambda2
ttmkfdir.x86_64                    3.0.9-42.lambda2.0.2                  lambda2
turbojpeg.x86_64                   1.2.90-6.lambda2.0.3                  lambda2
tzdata-java.noarch                 2020a-1.lambda2                       lambda2
unbound.x86_64                     1.6.6-5.lambda2                       lambda2
unbound-libs.x86_64                1.6.6-5.lambda2                       lambda2
unixODBC.x86_64                    2.3.1-14.lambda2                      lambda2
unzip.x86_64                       6.0-21.lambda2                        lambda2
urw-fonts.noarch                   2.4-16.lambda2                        lambda2
userspace-rcu.x86_64               0.7.16-1.lambda2.0.1                  lambda2
util-linux.x86_64                  2.30.2-2.lambda2.0.4                  lambda2
util-linux-user.x86_64             2.30.2-2.lambda2.0.4                  lambda2
uuid.x86_64                        1.6.2-26.lambda2.0.1                  lambda2
uuid-c++.x86_64                    1.6.2-26.lambda2.0.1                  lambda2
uuid-dce.x86_64                    1.6.2-26.lambda2.0.1                  lambda2
uuidd.x86_64                       2.30.2-2.lambda2.0.4                  lambda2
vips.x86_64                        8.9.2-1.lambda2                       lambda2
vips-tools.x86_64                  8.9.2-1.lambda2                       lambda2
voikko-tools.x86_64                4.1.1-1.lambda2                       lambda2
vulkan.x86_64                      1.0.61.1-2.lambda2                    lambda2
vulkan-filesystem.noarch           1.0.61.1-2.lambda2                    lambda2
wavpack.x86_64                     4.60.1-9.lambda2.0.1                  lambda2
which.x86_64                       2.20-7.lambda2.0.2                    lambda2
wireguard-tools.x86_64             1.0.20200827-2.lambda2                lambda2
wkhtmltoimage.x86_64               1:0.12.5-1.lambda2                    lambda2
wkhtmltopdf.x86_64                 1:0.12.5-1.lambda2                    lambda2
wkhtmltox.x86_64                   1:0.12.5-1.lambda2                    lambda2
wkhtmltox-devel.x86_64             1:0.12.5-1.lambda2                    lambda2
xkeyboard-config.noarch            2.20-1.lambda2                        lambda2
xml-common.noarch                  0.6.3-39.lambda2                      lambda2
xorg-x11-font-utils.x86_64         1:7.5-21.lambda2                      lambda2
xorg-x11-fonts-100dpi.noarch       7.5-9.lambda2                         lambda2
xorg-x11-fonts-75dpi.noarch        7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-1-100dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-1-75dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-14-100dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-14-75dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-15-100dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-15-75dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-2-100dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-2-75dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-9-100dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-ISO8859-9-75dpi.noarch
                                   7.5-9.lambda2                         lambda2
xorg-x11-fonts-Type1.noarch        7.5-9.lambda2                         lambda2
xorg-x11-fonts-cyrillic.noarch     7.5-9.lambda2                         lambda2
xorg-x11-fonts-ethiopic.noarch     7.5-9.lambda2                         lambda2
xorg-x11-fonts-misc.noarch         7.5-9.lambda2                         lambda2
xz.x86_64                          5.2.2-1.lambda2.0.2                   lambda2
xz-compat-libs.x86_64              5.2.2-1.lambda2.0.2                   lambda2
xz-libs.x86_64                     5.2.2-1.lambda2.0.2                   lambda2
xz-lzma-compat.x86_64              5.2.2-1.lambda2.0.2                   lambda2
yaml-cpp03.x86_64                  0.3.0-4.lambda2                       lambda2
zip.x86_64                         3.0-11.lambda2.0.2                    lambda2
zziplib.x86_64                     0.13.62-12.lambda2                    lambda2
zziplib-utils.x86_64               0.13.62-12.lambda2                    lambda2

```