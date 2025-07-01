# Version Control

This page lists version control tools.  If you are new to programming,
you may not yet understand how vital it is that you learn to use these
tools.  But if you ever found that your previous version of the code
worked and you current version doesn't, now you know why you need to
use version control tools.  While almost all version control tools
work for nearly any language (and so, strictly speaking, these tools
are not specific to the C language) they are so important that they
justify a wiki entry here.


## Glossary

* distributed
   * Describes tools that can be used by multiple people in different
     places
   * These tools don't require people to have access to a shared
     storage (drive, folder) and often support asynchronous ways of
     contributing changes (email, pull requests, etc.)
   * Most of these tools allow a develoiper to check in a change
     "locally" without committing to making it visible yet to
     everybody.  This means that you can use the tool to
     version-control work that is not "finished" yet.
* branching
   * Allows you to manage multiple versions of the code at the same
     time, and modify any of them.  For example:
      * If you have two versions of your code in use by customers,
        keeping those on separate beanches allows you to make updates
        to both versions (e.g. bug-fixes for older releases)
      * Tools that suport "local" branches allow you to switch between
        working on multiple things before either is "finished".  For
        example to work on two features in paralle, or to switch from
        working on a feature to making an emergency bug-fix
* merge
   * The act of incorporating the changes on a branch (or just a
     single change) into another branch.
   * Often also describes the process of reconciling two
     apparently-divergent copies of a file when performing a branch
     merge


## Open Source Tools

* [git](https://git-scm.com/)
   * Today, this is the de-facto industry standard.  Essentially
     everybody should learn this even if they also have access to
     something else.
   * This is the tool that powers GitHub, GitLab and so on.
   * [Beej's Guide to Git](https://beej.us/guide/bggit/)
   * [The Git Parable](https://tom.preston-werner.com/2009/05/19/the-git-parable.html)
* [Mercurial](https://www.mercurial-scm.org/)
   * Similar to git in a lot of ways.
   * Some advantages over git for truly vast repositories (and this is
     why Facebook
     ([explanation](https://graphite.dev/blog/why-facebook-doesnt-use-git),
     [article](https://engineering.fb.com/2014/01/07/core-infra/scaling-mercurial-at-facebook/))
     and Google
     ([presentation](https://mercurial.paris/download/Mercurial%20at%20Google.pdf))
     use/used it).
   * Comparison with git: [HackerNews
     thread](https://news.ycombinator.com/item?id=20776781), [Nelson
     Alfonso](https://medium.com/@Nelsonalfonso/git-vs-mercurial-the-battle-of-distributed-version-control-titans-79ffbf3d67d7)


## Proprietary (but generally available) Tools

* Microsoft [Azure DevOps Server](https://en.wikipedia.org/wiki/Azure_DevOps_Server)
   * Can optionally use git, and has other capabilities too.
* [Perforce P4 (Helix
  Core)](https://www.perforce.com/products/helix-core)
   * Papers by Dan Bloch about operating P4 at Google (before the
     switch to Piper)
      * [Life on the Edge: Monitoring and Running A Very Large
        Perforce
        Installation](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/34459.pdf)
      * [2011 article on scaling
        P4](https://www.perforce.com/products/helix-core), interesting
        reference to using a
        [RAM-SAN](https://en.wikipedia.org/wiki/Texas_Memory_Systems#RamSan_product_line).
* [PVCS](https://en.wikipedia.org/wiki/PVCS)
* [ClearCase](https://en.wikipedia.org/wiki/IBM_DevOps_Code_ClearCase)

## Priorietary (and not generally available) Tools

* [Piper](https://en.wikipedia.org/wiki/Piper_(source_control_system)
  ([migration from Perforce
  P4](https://graphite.dev/blog/google-perforce-to-piper-migration));
  many Googlers use
  [Fig](https://mercurial.paris/download/Mercurial%20at%20Google.pdf),
  a Mercurial front-end to Piper.
* [Watchman](https://www.facebook.com/notes/facebook-engineering/watchman-faster-builds-with-large-source-trees/10151457195103920) -
  Meta's add-on for scaling Mercurial

## Historic Tools

### Obsolescent

You can still use these today, and some people do, but apart from inertia there are likely few reasons to select these today for a new project

* Open Souce tools
   * Distributed (or nearly so)
      * [CVS](https://cvs.nongnu.org/)
         * Originally invented by Dick Grune (perhaps otherwise more
           famous for his excellent book [Parsing
           Techniques](https://dickgrune.com/Books/PTAPG_2nd_Edition/))
           in 1986
         * Allows geographically-separated developers to collaborate
           Requires a server, and developers need online access to the
           server to make commits or perform checkouts.
         * Practical issues with access control, availability, safety
           against abuse and CVS's lack of support for private
           branches were some of the things that drove widespread
           adoption of git.
      * [Subversion (svn)](https://subversion.apache.org/)
         * Intended to be "CVS done right", but setup was more
           difficult than CVS.  Perhaps for this reason, failed to
           supplant CSV before git did that.
      * [DARCS](https://darcs.net/) - influential on other systems but
        was never very popular itself.
   * Non-Distributed
      * RCS
        ([Wikipedia](https://en.wikipedia.org/wiki/Revision_Control_System),
        [project page](https://www.gnu.org/software/rcs/))
         * Early 1980s replaacement for SCCS.
         * Still feasible to use this for "local" version-control of
           individual files, but this usage is probably uncommon now
           that so many people understand how to use git.

### Proprietary

Proprietary tools tend to go from "supported" through "end of support
announced" and then to "no support, obsolete" but we don't track
end-of-support announcements so there are no obsolescent proprietary
tools listed here.

### Obsolete

These are mainly useful for strdying preserved souce-code repositories
(for example old versions of Unix). Open-Source tools listed here are
not necessarily lacking support, but there is little reason to choose
to use them for new projects today.

* Open Source Tools
   * [SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System)
      * Invented by Marc Rochkind in the early 1970s.  Shipped with many versions of Unix (but was proprietary)
      * Similar to RCS but designed differently (checkout is O(N) in
        the total number of changes, while for RCS checkout is fast
        for the current version and slow for older versions).
      * Branching support exists but is very basic (e.g. very
        difficult to tell if two versions of two files are on the same
        "branch" - just convention)
      * SCCS was the basis of Sun TeamWare and Sablime.
      * Open-Souce versions:
         * [GNU CSSC](https://www.gnu.org/software/cssc/) ("Compatibly
           Stupid Source Control") ([origin
           story](https://www.gnu.org/software/cssc/early-history.html))
         * [Jörg Schilling's
           SCCS](https://sourceforge.net/projects/sccs/) - direct
           descendant of Unix SCCS, with enhancements
* Proprietary
   * [BitKeeper](https://en.wikipedia.org/wiki/BitKeeper)
   * [Sablime](https://web.archive.org/web/20160722092853/http://sablime.alcatel-lucent.com/)
   * [Sun TeamWare](https://en.wikipedia.org/wiki/Sun_WorkShop_TeamWare)
   * [Microsoft Visual SourceSafe](https://en.wikipedia.org/wiki/Microsoft_Visual_SourceSafe)
