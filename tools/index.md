# Tools for C Programming

## Build Tools

### Tools for Building Your Code

* Make
   * [GNU Make](https://www.gnu.org/software/make/)
   * PMake ([tutorial](https://docs-archive.freebsd.org/44doc/psd/12.make/paper.pdf))
   * [A Tutorial on Portable Makefiles](https://nullprogram.com/blog/2017/08/20/)
* Others
   * [CMake](https://cmake.org/)
   * [Bazel](https://bazel.build/)
   * [Meson](https://mesonbuild.com/)
   * [Gradle](https://docs.gradle.org/current/userguide/userguide.html) ([instructions for building native software](https://docs.gradle.org/current/userguide/native_software.html))

### Tools for Portability

* GNU Autotools
   * Autoconf
      * Generates a "configure" script which sets up your makefiles
        and helps your pgoram be portable across many Unix-like and
        Linux systems.
   * Automake
      * Generates Makefiles which work across many systems (the common
        feature set of "make" itself is surprisingly limited)
      * The generated makefiles will automatically track dependencies
   * See [An Introduction to the
     Autotools](https://www.gnu.org/software/automake/manual/automake.html#Autotools-Introduction)
   * GNU Autotools has a reputation for being hard to use.  This is
     fair, but they are also more powerful than any other approach to
     the same set of problems.
* GNU libtool
   * Provides a machine-independent way to build libraries, including
     shared (dynamic link) libraries.
   * The best way to use this is via GNU Autotools.
* [Metaconfig](https://github.com/Perl/metaconfig) is primarily
  intended for building Perl.
* Try Your Build Tool
   * Some build tools, for example CMake, also attempt to solve
     portability challenges, though arguably attempts only a narrower
     scope
* Obsolete
   * GNU Autotools essentially out-competed a number of predecessor
     systems; if you see these in use today you could well have a lot
     of trouble getting them to help you build on modern systems
   * [imake](https://en.wikipedia.org/wiki/Imake) (and xmkmf) has been
     obsolete since the early 2000s.  See [conversion
     guide](https://ivi.fnwi.uva.nl/tcs/pub/bachelortheses/ITamboer.pdf)

## Configuration Management

Software configuration management is a very broad category and
encompasses how you build, version-control and audit your software and
computer systems.  Because of this breadth, it doesn't make much sense
to link to particular tools here.  Instead we link to more specific
categories.

* [Version Control](version-control.md)
  (also known as Revision Control) is probably what most people
  understand when they hear the phrase "Configuration Management".
* Build Management is already covered above
* Software Development Lifecycle Tools
   * These vary from lightweight and flexible to comprehensive and burdensome.
   * Nothing about them is C-specific and many C programmers will not
     need or use these, so we don't list them here.
* Defect and Work Item Tracking
   * Not really specific to C so try some related subreddits:
      * http://www.reddit.com/r/softwaredevelopment ([What issue
        tracking software does your team use? Are you
        satisfied?](https://www.reddit.com/r/softwaredevelopment/comments/vk9ai5/what_issue_tracking_software_does_your_team_use/)
      * http://www.reddit.com/r/QualityAssurance ([tools query](https://www.reddit.com/r/QualityAssurance/search/?q=tools))
      * http://www.reddit.com/r/programming
	  * http://www.reddit.com/r/Agile ([survey](https://www.reddit.com/r/agile/comments/1gxxzv5/positive_experiences_with_jira_alternatives/))


## Working With Source Code

### Online Tools

* Matt Godbolt's [Compiler Explorer](https://godbolt.org/) lets you paste or type code fragments and examine the machine code they compile to.

## Pastebins

* If your source code is long, it is much better to cut down your
  example before posting it (and in any case this will often help you
  debug it!).  But if you really really can't, you could use a
  "pastebin" site.  Beware though, some of these sites can contain
  malicious content.

* [GitHub Gist](https://alternativeto.net/software/github-gist/about/)
* https://pastebin.com/
* https://textbin.net/
* https://ideone.com/ (will compile some programs)
* https://pastecode.io/
* https://pastesio.com/
* More: https://github.com/lorien/awesome-pastebins

### Code Formatters

   * [clang-tidy](https://clang.llvm.org/extra/clang-tidy/)
   * [GNU indent](https://www.gnu.org/software/indent/)
   * Most IDEs can do this automatically, though.

### Style Checkers

See the [static-analysis](static-analysis.md) page.

### Documentation Generators (from source code)

* [clang-doc](https://clang.llvm.org/extra/clang-doc.html)
* [Doxygen](https://www.doxygen.nl/#google_vignette)
* [cweb](http://www.literateprogramming.com/cweb_download.html) (**warning:** not suitable for retro-fitting!)

### Static (Source Code) Analysis

There are a lot of these; see the [static-analysis](static-analysis.md) page.

### Refactoring and Program Transformation

* IDEs often have this feature built-in so you may not need a separate tool for this.
* Some [static analysis](static-analysis.md) tools also have program transformation featurs.
* [Coccinelle](https://github.com/coccinelle/coccinelle)

## Working With Your Compiled Program

### Debugging

* IDEs generally incorporate a debugger.
* Traditional Debuggers
   * [GDB](http://sources.redhat.com/gdb/): The GNU Project Debugger
      * Tutorial: [Beej's Guide to the GNU Debugger
        (GDB)](https://beej.us/guide/bggdb/)
      * If you're not familiar with GDB, learn how to use "TUI mode",
        it is more user-friendly.
      * Debugging remote programs
         * Link the GDB remote debugging stub into your program
         * Run gdbserver on the remote system
* Debugging without Debuggers
   * Logging (i.e. emitting messages about what the program is doing)
     is an enduringly popular debugging strategy
   * Unit tests: if you have a hypothesis about what the problem is,
     you can write a unit test that verifies your program's behaviour.
     If your unit test uncovers the bug, you can fix the bug and keep
     the test.
* See also the Dynamic Analysis section

### Profiling

Profiling (i.e. determining what your program spends its time doing)
is often a feature of the compiler itself, and to "profiling tools"
are often more concerned with the analysis of the output of the
compiler's profiling featuire.

* gprof is part of GNU binutils (as is `ld`, so if you are programming
  on Linux you likely already have this installed)
* [flamegraph](https://www.brendangregg.com/flamegraphs.html) is an
  interactive tool for exploring profiling data

### Code Coverage

The most important use of code coverage tools is to figure out what
parts of your code are not yet covered by tests.  Many coverage tools
use the same techniques as profilers, and often a single tool can do
both jobs.

* gcov
   * gcov is included with GCC
   * clang has a different, compatible, tool with the same name

### Dynamic Analysis

These are tools which deduce problems with your program at runtime.

* Memory Access debugging
   * [Valgrind](https://valgrind.org/)
      * See also their poll on [comparison with Purify and
        Insure++](https://valgrind.org/gallery/survey_03/q4.html) from
        a (years ago) [Valgrind
        survey](https://valgrind.org/gallery/survey_03/summary.html#summary)
   * [DUMA](https://sourceforge.net/projects/duma/)
   * See also Sanitizers
   * See also [Wikipedia list of memory
     debuggers](https://en.wikipedia.org/wiki/Memory_debugger)
* Sanitizers
   * ASAN, MSAN etc. are now part of
     [LLVM](https://github.com/google/sanitizers/) and
     [GCC](http://www.gnu.org/software/gcc), so the [original Google
     project](https://github.com/google/sanitizers/) has been
     archived.

### Inspection Tools (Not Requiring Source Code)

These are tools which inspect the operation of a program without
necessarily requiring source code for it.

* Program Tracing
   * General-prupose
      * [dtrace](https://dtrace.org/) led the way and primarily
        targets FreeBSD and the Solaris family of operating systems.
      * [bpftrace](https://www.brendangregg.com/ebpf.html#bpftrace)
      * [lttng](https://lttng.org/features/)
      * perf
   * System-call tracing
      * [strace](https://strace.io/)
      * truss
   * Library-function call tracing
      * ltrace
* Synthetic Execution
   * [Valgrind](https://valgrind.org/) suite; the analyzers described
     below are all included.
      * Memcheck is Valgrind's default checker; it tells you if your
        program's execution depends on uninitialised values or your
        pogram accesses memory it should not.
      * Cachegrind analyses how your program interacts with a CPUs
        cache and branch predictor
      * Callgrind collects call-graph (which functions call which
        other functions) data; you can visualize the result with
        [Kcachegrind](https://kcachegrind.github.io/html/Home.html).
      * Threading issues
         * Helgrind
         * DRD
      * Heap profiling
         * Massif is a heap profiler (analyzes your program's use of
           heap and, optionally, stack)
         * DHAT

## Inspecting Things Other Than Programs

Sometimes you want to inspect the general state of your system or its
actions to figure out what is happening, as opposed to just inspecting
the actions of your program.

* Linux / Unix
   * [Brendan Gregg gave a good overview at LISA
     2014](https://www.brendangregg.com/linuxperf.html#LISA2014)
   * These tools all have manual pages, so many of them don't need
     links.
   * Network
      * [tcpdump](https://www.tcpdump.org/) works on many Unix-like
        systems, sometimes with slight differences in filter syntax.
         * [Tutorial](https://danielmiessler.com/blog/tcpdump)
         * [Cheat
           Sheet](https://web.archive.org/web/20240227014632/https://packetlife.net/media/library/12/tcpdump.pdf)
      * [wireshark](https://www.wireshark.org/) provides an excellent
        way to analyse packet dumps (generated by, for example,
        tcpdump)
      * netstat, ss, nstat
   * CPU
      * top, htop, atop
      * ps
   * File System
      * iostat
      * lsof
* Windows
   * I'm sure these exist, but I am not familiar with anything that
     post-dates [SoftICE](https://en.wikipedia.org/wiki/SoftICE).
* Embedded
   * Embedded systems with a Linix kernel can take advantage of the
     tools listed above.
   * Bare-Metal
      * Logic Analyzers
      * Oscilloscopes
      * In-Circuit (CPU) Emulators
      * Bare-Metal debugging
         * [Segger
           J-Link](https://www.segger.com/products/debug-probes/j-link/)
           probes
      * Multi-Function Analyzers
         * [Digilent Analog
           Discovery](https://digilent.com/shop/analog-discovery-3/)
      * Protocol Analyzers
         * TCP/IP: You can do TCP/IP analysis on a separate
           computer/device, for example tcpdump on a nearby Linux box.
           You may need an Ethernet switch on which you can configure
           port mirroring.
         * USB: [TotalPhase Beagle](https://www.totalphase.com/products/beagle-usb12/)
         * Multi-Purpose: [HHD Device Monitor Studio](https://hhdsoftware.com/device-monitoring-studio)
