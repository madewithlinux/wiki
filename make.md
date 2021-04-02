# make

IMHO the killer features of make are:
* specify rules for building a target. rules can have matching wildcards in the inputs and outputs
* only rebuilds when inputs change

but the big problem with make is that make's syntax is garbage, and also so is a lot of the functionality itself (e.g. how do you do paths with spaces?)


# alternatives to make that focus on just running tasks with a DAG structure
* http://gittup.org/tup/
  * lua for scripting
  * can rules be multiple commands? I don't see any examples of that
  * somehow it can detect if a rule didn't actually use a dependency that it declared
    * I think it uses a fuse mount to do this?
  * also it has an inotify monitor option that reruns on changes automatically (neat!)
* https://waf.io
  * is this project live?
* https://github.com/ruby/rake
  * ruby though...
* https://code.google.com/archive/p/make-py/
  * https://github.com/zwegner/make.py
  * probably "dead" but it's small enough that if it's feature complete it probably doesn't matter
  * rules style looks like imperative code that builds a declarative DAG state
* https://github.com/cww0614/make.py
  * (different than the above `make-py`)
  * looks to be almost the same literal functionality as make, but with python syntax
  * this was written surprisingly recently! (Dec 2020)
  * rules are functions annotated with `@rule()` (neat!)
    * rule dependency can be a function that returns a list of dependencies for a target?
  * can use regexes to specify wildcards for rules
  * `VARIABLES = PersistentVariables("variables.json")` that looks handy

# build systems
* https://premake.github.io/
* https://scons.org/
* 


