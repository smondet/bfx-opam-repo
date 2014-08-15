bfx-opam-repo
=============

Opam repository to install bioinformatics tools (the non-OCaml ones).

Usage
-----

If you got Opam with an OCaml compiler, these packages will work happily in the
middle of any Opam switch:

    opam remote add sm-bfx git@github.com:smondet/bfx-opam-repo
    opam install samtools vcftools

If you got the binary version of Opam, without an OCaml compiler, **and** you
don't want to compile OCaml, you can use the `fake.0.0.1` “compiler”.

For instance, let's say you got Opam with `apt-get install opam` 
(with **@avsm**'s [PPA](https://launchpad.net/~avsm/+archive/ubuntu/ppa)):

    opam init --comp=fake.0.0.1 opamfake git@github.com:smondet/bfx-opam-repo
    eval `opam config env`
    opam install samtools vcftools


Notes
-----

As a proof-of-concept there is a TMux package and its dependency: the library
`libevent`; they work but require the following setup at runtime:

    export LD_LIBRARY_PATH=`opam config var prefix`/lib:$LD_LIBRARY_PATH

