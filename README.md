ocamlunix — Unix System Programming in OCaml
-------------------------------------------------------------------------------
Release !!VERSION!!

ocamlunix is the english translation of Xavier Leroy and Didier Rémy's
[Unix system programming course][1].

ocamlunix is distributed under a Creative Commons by-nc-sa
license. For the details see the file [`LICENSE`](LICENSE).

[1]: http://gallium.inria.fr/~remy/camlunix/ 

Project home page : http://ocaml.github.io/ocamlunix  
Contact & typos : `Daniel Bünzli daniel.buenzl i@erratique.ch`


## Prerequisites

To generate the documents you will need in your `$PATH` :

1. An OCaml distribution with ocamlbuild (i.e. at least version 3.10).
2. A recent TeX distribution (tested with TeX Live 2008).
3. And for the HTML version: HeVeA (tested with version 1.10),
   ghostscript (tested with version 8.63)


## Document generation

From the root directory of the distribution the following commands can
be issued to build the various versions of the document (ocamlbuild
can be used directly instead of `./build`)

    > ./build ocamlunix.pdf    # PDF version
    > ./build ocamlunix.html   # Monolithic HTML
    > ./build index.html       # HTML by chapters

The results are in the directory `_build/src`. To generate all versions
of the document you can simply type :

    > ./build

The result can be installed in the `$INSTALLDIR` directory by typing :

    > INSTALLDIR=/path/to/instal/dir ./build install

if `$INSTALLDIR` is left unspecified `+ocamlunix` is used. 

The target `install` doesn't install the archive with the sources, use
install-distrib for that. For example to publish to the website do :

     > INSTALLDIR=/path/to/www ./build install-distrib

The `_build` directory can be removed by typing

     > ./build clean


## Quick guide to the distribution

`src/` contains the tex sources from which the HTML version and the
PDF version are generated. Most chapters are in their own file. They
are aggregated by the master file `ocamlunix.tex` which also contains
useful macros common to both versions. This is also the place where
you'll want to comment out chapters while working on a specific one to
reduce compilation times.

Layout and macros distinctions between the HTML and the PDF version
are respectively in the file prelude.hva and prelude.sty. Minor layout
and content distinctions are performed using the macros `\ifhtml`,
`\ifhtmlelse and \ifnothtml`.


### Pictures

Pictures are created with the PGF/TikZ package. For the HTML version
they are first extracted via the preview package (invoke the target
`ocamlunix-image.pdf`) and then converted to pngs with ghostscript
(invoke the target `ocaml-image.pngs`). This is handled automatically
when one of the HTML versions is build.


### Code extraction

The environments listingcodefile and codefile (the contents of the
latter being invisible in the final document) allow to write code in
the file specified as an argument to the environment. This code is in
fact written to the file `_build/src/ocamlunix.code`. By building the
target:

    > ./build ocamlunix.extract

The contents of this file will be extracted to the code/ directory of
the distribution. Once this is done programs can be built e.g. by
typing :

    > ./build echo.native

The result will be in the `_build/code/` directory. If you use the
`build` script (vs. ocamlbuild directly), trying to build a `*.native`
or `*.byte` will automatically build the `ocamlunix.extract` target.


## Translation credits

* Chapter — translator / proofreader
* Generalities — Eliot Handelman / Prashanth Mundkur
* Files — Richard Paradies (reworked by Daniel C. Buenzli) /
  Erik de Castro Lopo
* Processes — Mark Wong-VanHaren / Anil Madhavapeddy
* Signals — Thad Meyer / David Allsopp
* Pipes — Daniel C. Buenzli / John Clements
* Sockets — Till Varoquaux, Priya Hattiangdi and Prashanth Mundkur 
  (reworked by Daniel C. Buenzli) / Prashanth Mundkur
* Threads — Eric Cooper / Prashanth Mundkur
* Remaining text — Daniel C. Buenzli / Prashanth Mundkur





