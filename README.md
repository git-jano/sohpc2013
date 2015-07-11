1st day: user registration

Week | Day | Description | Tutor
--- | --- | --- | ---
1 | 1 | Linux Shell Tutorial or Adv. Scripting | Tamás
1 | 2 | * Basic HPC introduction                 | Gábor
1 | 3 | * Open Grid Scheduler (HPL job test)     | Gábor
1 | 4 | * ARC middleware (HPL job test)          | Gábor
1 | 5 | * VirtualGL/TurboVNC                     | Gábor
2 | 1 | Quantum Espresso                       | Tamás
2 | 2 | Quantum Espresso                       | Tamás
2 | 3 | Siesta                                 | Tamás
2 | 4 | Siesta                                 | Tamás
2 | 5 | VMD                                    | Tamás
3 | 22 July | Compiling and inputs                   |
4 | 29 July | Benchmarking and GPUs                  | 
5 | 5 Aug | Calculations                           |
6 | 12 Aug | Analysis                               |
7 | 18 Aug | Visualization                          |
8 | 26 Aug | Video and report                       |

<!--
########     ###     ######  ##     ## 
##     ##   ## ##   ##    ## ##     ## 
##     ##  ##   ##  ##       ##     ## 
########  ##     ##  ######  ######### 
##     ## #########       ## ##     ## 
##     ## ##     ## ##    ## ##     ## 
########  ##     ##  ######  ##     ## 
-->

module and environment

Try to use Bash, always, as simplw as possible!

[Advanced Bash Scripting](http://www.tldp.org/LDP/abs/html)

    #!/bin/sh
    #!/bin/bash
    #!/usr/bin/perl
    #!/usr/bin/tcl
    #!/bin/sed -f
    #!/bin/awk -f
    #!/usr/bin/env python
    #!/bin/rm
    #!/bin/more
    ...

If you have several versions of Python installed, `/usr/bin/env` will ensure the interpreter used is the first one on your environment's `$PATH`.

[Special characters](http://www.tldp.org/LDP/abs/html/special-chars.html)

    :() {
      echo "The name of this function is "$FUNCNAME"
      # Why use a colon as a function name?
      # It's a way of obfuscating your code.
    }

Namespaces and libraries

    function mother/child/func
    mother_child_func
    ./mother/child/func

Do$$ar is what I need

    $* $! $? $$ $@ ${} $() a=${!b} {}

[Subshells](http://www.tldp.org/LDP/abs/html/subshells.html)

    a=${(which top):-/bin/top}
    (( var0 = var1<98?9:21 ))

Blockparty and [arrays](http://www.tldp.org/LDP/abs/html/arrays.html)

    Array=(element1 element2 element3)
    echo {file1,file2}\ :{\ A," B",' C'}
    ls . | xargs -i -t cp ./{} $1

Test test test

    [] [[]] $[] (())

Redirections ([here documents](http://www.tldp.org/LDP/abs/html/redircb.html))

    < > << >>

[History cheat sheet](http://www.catonmat.net/download/bash-history-cheat-sheet.pdf) and [bash history tagging](http://vignesh.foamsnet.com/2013/06/using-hash-tags-to-organize-bash-history.html)

[Variables](http://www.tldp.org/LDP/abs/html/parameter-substitution.html)

    b=${a/23/BB}
    a=${!b}
    b=${a##c}
    a=$(ls)

Variable scopes

    export local shift $0 $1 $*

[Exit codes](http://www.tldp.org/LDP/abs/html/exitcodes.html#EXITCODESREF)

    exit return
    
    _true_=0
    _false_=1
    function failed(){ return ${_false_}; }
    function success(){ return ${_true_}; }
    if success ; then echo success; fi

Operators. Valid to use constructs like `@@core`.

    ns_op="< + -"
    failure="return ${_false_}"
    success="return ${_true_}"

    function ns/op() {
      local _s="${1}"
      local _m="${2}"
      if empty "${_m}" ; then
        _m="${ns_op}"
      fi

      local o
      for o in ${_m} ; do
        if test "${_s:0:1}" = "${o}" ; then
          $success
        fi
      done
      $failure
    }

[Environment variables](http://www.tldp.org/LDP/abs/html/internalvariables.html) and functions

    nce
    echo $PS1
    set

Use the source Luke!

    source $(dirname $0)/../../bin/functions

TAB complete, rvm prompt.

Shell options

    while getopts hvb: o; do
      case "$o" in
        b) _m="CREATE"; _b=$OPTARG;;
        v) gdbg=true;;
        h|*) help/bmkmgr;;
      esac
    done

Find arghhh

    find ~/ -name '*.txt'
    find ~/mail -type f | xargs grep "Linux"

[Text processing](http://www.tldp.org/LDP/abs/html/textproc.html)

Archiving

    tar [gb]zip diff md5 pv

[Fuuuuuuu](http://www.commandlinefu.com/commands/browse)

Math

    var3=$(bc -l << EOF
    scale = 9
    s ( 1.7 )
    EOF
    )

[Regular expressions](http://www.tldp.org/LDP/abs/html/x17046.html)

[IO redirections](http://www.tldp.org/LDP/abs/html/io-redirection.html)

[On more thing, the most important thing!](http://www.tldp.org/LDP/abs/html/unofficialst.html)

Walk the walk repl the repl or [write frameworks](https://github.com/hornos/shf3)

    cat << EOF > "${rc}"
    source $(dirname ${BASH_SOURCE})/../lib/header
    export PS1='SHF3(\$?)> '
    import gui
    gui/txt "Shell Framework 3 Console" "white"
    check
    EOF
    bash --noprofile --rcfile "${rc}"

SSH rsync parallel rsync measure time

<!--
 ######  #### ########  ######  ########    ###    
##    ##  ##  ##       ##    ##    ##      ## ##   
##        ##  ##       ##          ##     ##   ##  
 ######   ##  ######    ######     ##    ##     ## 
      ##  ##  ##             ##    ##    ######### 
##    ##  ##  ##       ##    ##    ##    ##     ## 
 ######  #### ########  ######     ##    ##     ##
-->

## SIESTA

[How to run SIESTA](http://www.mcc.uiuc.edu/summerschool/2005/week_one_lectures/miguel_pruneda/How_to_run_SIESTA.pdf)

http://www.mcc.uiuc.edu/summerschool/2005/week_one_lectures/miguel_pruneda/

Download the [example files](http://www.mcc.uiuc.edu/summerschool/2005/tutorial/SIESTA/AllSiestaExamples.tar.gz)


## Visualization

http://onlinelibrary.wiley.com/doi/10.1002/qua.24480/abstract

[VMD](https://www-s.ks.uiuc.edu/Training/Tutorials/vmd/tutorial-html)

## Budapest

[Party Map](http://444.hu/2013/05/24/bulinegyed-budapest/)

[Weather](http://www.idokep.hu/elorejelzes)

## HPC manuals

https://conference.niif.hu/event/3/session/23/contribution/25

http://wiki.niif.hu/HPC

https://www.niif.hu/szolgaltatasok/szuperszamitastechnika/niif_szuperszamitogep_szolgaltatas

https://portal.hpc.niif.hu

https://www.youtube.com/user/roczei

https://prezi.com/user/roczei/

https://prezi.com/5xpmabacayop/szuperszamitogep-tutorial/

http://www.training.prace-ri.eu/

