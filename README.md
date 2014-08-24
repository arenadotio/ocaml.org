OCAML.ORG PROJECT
=================
This is the source code implementing the ocaml.org
website. Information here is relevant only to developers and content
contributors. End-users of the website should simply visit the
website, which is hosted at http://ocaml.org.


DEPENDENCIES
============
Building the html pages requires:

* bash
* curl
* rsync
* GNU make
* ocaml >= 4.01.0 (the presence of ocamlopt is required)
* camlp4orf (comes with the compiler in OPAM, in `camlp4-extra` in Debian)
* ocamlfind
* mpp >= 0.1.2
* omd >= 0.9.7
* opam2web >= 1.3.1
* ocamlnet (>= 3.7.4-1), and syndic (>= 1.1) for rss2html.ml
* lablgtk2 (optional, for the Gtk tutorial)

Implicit dependencies exist and may not be on this list (for instance, opam2web depends on quite a set of packages, so it's strongly adviced to use opam to compute and install automatically such packages).

If you use opam (>= 1.1), the OCaml packages above can be installed by
running:

    opam install ocamlfind mpp omd ssl ocamlnet ocamlrss opam2web

If your opam environment isn't using OCaml 4.01.0, you may switch to it by using this command:

    opam switch 4.01.0

Note that you need `libssl-dev` to be able to compile and use `ssl`.
`libssl-dev` is the name of a debian package, if you're using another system,
it might be available under a different name.

BUILD
=====
The site consists only of static pages, so can be built and run
entirely on a local machine without dependencies on external file or
database servers. Simply run:

    make

(or `make -j` for a faster build on multicore machines.
NB: you might need to limit the number of forks e.g `make -j 8`
[ref](https://github.com/ocaml/ocaml.org/issues/462#issuecomment-40318537)).

This will generate a new folder `ocaml.org` that contains the full
website.  Note that building the site will attempt to connect to the
internet to download the news and latest email conversations.  As
usual, use `make clean` to delete the files generated by the
compilation.

DIRECTORY STRUCTURE
===================
`site` — Main content of the site. Most files are in Markdown syntax
         and converted to HTML by the build scripts.

`template` — Templates governing the overall look and feel of the
             site. These are applied to the pages within site/ when
             the site is built. References to templates within site
             pages should be of the form `template/template-file-name`
             because the build script assumes this directory
             structure.

`script` — Scripts used to build the site.


CONTACTS
========
For general discussion about the site's implementation, you can post
to the [infrastructure](http://lists.ocaml.org/listinfo/infrastructure)
mailing list.

For a specific bug report, content suggestion, or feature request,
please create an issue on
[GitHub](https://github.com/ocaml/ocaml.org). Or best of all, fork the
repo, make changes to your copy, and submit pull requests. It's that
easy!
