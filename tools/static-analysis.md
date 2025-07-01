# Static Analysis and Source Code Analysis Tools

There's a long list by Matthias Endler at
https://github.com/analysis-tools-dev/static-analysis#c

## Linters

A linter's job is to tell you about potential problems in your source
code.  These are not as essential as they once were, since turning on
all the warning messages in your compiler
([example](https://interrupt.memfault.com/blog/best-and-worst-gcc-clang-compiler-flags))
will do much of the same job.

* Using Warnings
   * GCC
      * [Options to Request or Suppress
        Warnings](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html)
   * clang
      * [Options to Control Error and Warning
        Messages](https://clang.llvm.org/docs/UsersManual.html#options-to-control-error-and-warning-messages)
   * Microsoft
      * [Compiler warnings that are off by
        default](https://learn.microsoft.com/en-us/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
   * General advice
      * Different compilers have different warnings.  It is often
        useful to try compiling yoru code with a compiler you don't
        usually use, do get warnings about the things your usual
        compiler misses.
* Linter tools
   * [clang-analyzer](https://clang-analyzer.llvm.org/)
   * [Splint](https://splint.org/) (previously called lclint)
   * [Coverity](https://scan.coverity.com/)
   * [PMD](https://docs.pmd-code.org/latest/index.html) ([source](https://github.com/pmd/pmd/tree/pmd_releases/7.6.0))
   * cppcheck (on [SourceForge](https://cppcheck.sourceforge.io/), on [GitHub](https://github.com/danmar/cppcheck/tree/main))
   * [PC-Lint](https://pclintplus.com/)
   * Special-Purpose Linters
      * [Sparse](https://sparse.docs.kernel.org/en/latest/) for the Linux kernel

## Security Scanners and Software Supply-Chain Analysis

This section needs some contributions from people with expertise and
preferences in this area.

* GitHub
   * GitHub will optionally scan for security issues in your code; see
     the **Security** tab in your project's GitHub page.
* GitLab
   * GitLab apparently has some similar features (please contribute a
     summary if you are familiar with this)
* Other
   * There are a number of other systems, frequently "AI-based", on
     offer.  Some of these require filling in a form to try them out
     and have subscription models or licensing models that don't seem
     amenable to casual trying-out.

## Other Static Analysis Tools

Tools listed here often do "lint-type" checks but in addition have significant other capabilities too.

* NASA [IKOS](https://github.com/NASA-SW-VnV/ikos)
* [Moose](https://modularmoose.org/) has a lot of analysis features in additional to "lint-type" checks.
* [FRAMA-C](https://frama-c.com/)
* [CPAchecker](https://cpachecker.sosy-lab.org/) describes itself more as a software verification platform.
* [CodeAnt AI](https://www.codeant.ai/)
* [CheckMarx](https://checkmarx.com/)
