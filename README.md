# `build2`-base build system prototype for CHERI microcontroller development

This is a prototype of a `build2`-base build system for the CHERI
microcontroller development as described in [this thread][spec].

This prototype uses the standard GCC/Clang toolchain and maps the concepts in
the above description as follows:

* library -- static library (`.a`)
* compartment -- shared library (`.so`)
* firmware    -- executable
* firmware linker script -- generated source file with `main()`

The files of interest are [`cherimcu/buildfile`][buildfile] which is what the
user would write and [`build/cherimcu.build`][cherimcu.build] which contains
all the CHERI-specific target types, rules, etc., and which is what CHERI
developers would supply to the user.

To try it yourself, get [`build2`][build2], clone this project, and then run
`b` from the project root:

```
$ git clone https://build2.org/cherimcu.git
$ cd cherimcu
$ b
```

Or, for the out of source build:

```
$ cd ..
$ b cherimcu/@cherimcu-out/
```

Or to configure an out of source build (and also specify the C/C++ toolchain):

```
$ b configure: cherimcu/@cherimcu-clang/ config.cxx=clang++
$ b cherimcu-clang/
$ cd cherimcu-clang/
$ b
```

[spec]: https://lobste.rs/s/xus8hc/when_use_bazel#c_xycjdn
[buildfile]: cherimcu/buildfile
[cherimcu.build]: build/cherimcu.build
[build2]: https://build2.org
