# cust-comp-test

source /homes/wl/public/setup.ruby

 - Put parameters of functions in angle brackets if there are more than one, eg . ``VAR x y . <x, y> $rel <`mult` <x,y>>.``
 - `fst R = [R, id]` - eg `fst R ; mult` will take its first input as the output of R and its second input as the second value inputted from stdin.
 - `/\ 3 R = [R^0, R^1, R^2] = [id, R, R^2]`
 - To use a constant as input to a block, you need to use `pi1^~1 ; snd const ; ...` (or `pi2^~1 ; fst const ; ...`) as shown in [constant.png](constant.PNG).
 - `rdl` and `rdr` can be useful for aggregating functions (eg. `add`) on lists of values. See [rdr.jpg](rdr.jpg) and [rdl.jpg](rdl.jpg) for examples.
