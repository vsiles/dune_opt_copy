# dune_opt_copy
sandbox to test dune optional copy 

# version:
- dune 2.8.2
- (lang dune 2.8)

# Scenario to run:
```
$ dune clean
$ dune build @all
$ ./_build/default/src/main.exe
Hello, world !
# Open optional/dune and remove the commenting `;`
$ vim optional/dune
$ dune clean
$ dune build @all
File "src/dune", line 1, characters 0-0:
Error: No rule found for src/foo.opt.ml
```

Note that if I completely remove the `enabled_if` part in `src/dune`, then it builds and runs correctly.

# Other syntax / errors:

```
$ dune clean && dune build @all
File "src/dune", line 14, characters 22-49:
14 |     (enabled_if (= "%{lib-available:optional_foo}" true))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
Error: %{lib-available:..} isn't allowed in this position
```

# Potential solution: not use `copy` but systems' `cp`

```
(rule
    (target foo.opt.ml)
    (action (system "[[ %{lib-available:optional_foo} ]] && cp ../optional/foo.opt.ml foo.opt.ml"))
)
```
