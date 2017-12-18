
Found these build instruction on Google Groups

   https://groups.google.com/forum/#!topic/trelby/_u7-h46c4x8

They describing building for Raspbian, also worked for Ubuntu 17.10
I've have updated them to match my own practices. - RSD 2017-12-17

```shell
    sudo apt-get install xsltproc docbook-xsl python-wxtools devscripts debhelper python-all python-mock
    git clone https://github.com/oskusalerma/trelby/ src/github.com/oskusalerma/trelby
    cd src/github.com/oskusalerma/trelby
    vi Makefile       # See changes needed below
    vi debian/control # See changes needed below
    make names.txt.gz dict_en.dat.gz manual.html trelby.1.gz
    make clean
    make deb
    cd ..
    dpkg -i trelby_2.3-dev_all.deb
```

You need to make to following changes in the Makefile and the debian 
control file.

+ Makefile
    + change section "manual.html: doc/*" to
        `make -C doc html # && mv doc/manual.html`
    + change section ""trelby.1.gz: doc/*" to
        `make -C doc manpage # && mv doc/trelby.1.gz`
+ debian/control
    + change "python-wxgtk2.8" to "python-wxgtk3.0"

