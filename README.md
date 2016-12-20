# bootycall

A shell nREPL client for boot nREPL and other nREPls.

# Motivation

The main motivation for this script was to make Clojure code callable from the shell by using [nREPL] (https://github.com/clojure/tools.nrepl).
In particular, [boot] (https://github.com/boot-clj/boot) tasks and CLI tasks can be called very fast as the JVM has not to start up for every call.

`bcall` makes a call to the tasks `fire` (see [here] (http://www.braveclojure.com/appendix-b/)) to a running boot nREPL which takes about 0.21s (on a mid-2012 Macbook Pro):
```
% time bcall -v fire --thing pants -p
My pants are on fire!
bcall fire --thing pants -p  0.21s user 0.03s system 92% cpu 0.259 tota
```
Directly calling ```boot``` takes around 7s.
```
% time boot fire --thing pants -p
My pants are on fire!
boot fire --thing pants -p  6.99s user 0.27s system 255% cpu 2.848 total
```

The general idea is to make writing Clojure code for the shell more practical by avoiding the JVM startup time that is needed with every call.

# Installation

You can either clone this repository and call the Python script `bcall.py`
directly or you can install `bootycall` via `pip`:

```pip install bootycall```
