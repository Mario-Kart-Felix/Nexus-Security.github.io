---
title: 'GCC-rust: A (WIP) Rust front end for GCC'
date: 2019-12-08T08:10:00+01:00
draft: false
---

![](https://avatars1.githubusercontent.com/u/896766?s=400&v=4 "GitHub - sapir/gcc-rust: a (WIP) Rust frontend for gcc")  

```
Rust frontend for GCC Build instructions: (Be warned, these are currently rather rough.) Build Rust with this patch: [https://github.com/rust-lang/rust/pull/67126](https://github.com/rust-lang/rust/pull/67126) mkdir gcc cd gcc git clone -b rust [https://github.com/sapir/gcc-rust/](https://github.com/sapir/gcc-rust/) gcc-src (cd gcc-src/gcc/rust/gcc-rust; cargo build) mkdir gcc-build cd gcc-build ../gcc-src/configure --prefix=$(pwd)/../gcc-install --enable-languages=c,c++,rust --disable-multilib --disable-bootstrap make make install cd .. gcc-install/bin/gcc whatever.rs -o whatever This directory contains the GNU Compiler Collection (GCC). The GNU Compiler Collection is free software. See the files whose names start with COPYING for copying permission. The manuals, and some of the runtime libraries, are under different terms; see the individual source files for details. The directory INSTALL contains copies of the installation information as HTML and plain text. The source of this information is gcc/doc/install.texi. The installation information includes details of what is included in the GCC sources and what files GCC installs. See the file gcc/doc/gcc.texi (together with other files that it includes) for usage and porting information. An online readable version of the manual is in the files gcc/doc/gcc.info\*. See [http://gcc.gnu.org/bugs/](http://gcc.gnu.org/bugs/) for how to report bugs usefully. Copyright years on GCC source files may be listed using range notation, e.g., 1987-2012, indicating that every year in the range, inclusive, is a copyrightable year that could otherwise be listed individually. 
```

  
  
from Hacker News https://ift.tt/2DUHtj1