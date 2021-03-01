# dune_opt_copy
sandbox to test dune optional copy 

Scenario to run:
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
