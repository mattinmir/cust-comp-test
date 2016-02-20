# cust-comp-test

### Setup
To set up your directory to run ruby files, ssh into a DoC terminal and run the following:
`source /homes/wl/public/setup.ruby`

### Contents of Repo
The source code and images in this repo are examples I have written to help solidify understanding of Rebecca concepts

#### [constant.jpg](constant.jpg)
To use a constant as input to a block, you need to use `pi1^~1 ; snd const ; ...` (or `pi2^~1 ; fst const ; ...`) as shown.
  
#### [hexprism.rby](hexprism.rby) and [hexprism.jpg](hexprism.jpg)
This is an adaptation of eg5 from [egs.rby] where you calculate the volume of a cylinder, but I wanted to try a program that had two inputs instead of 1, and also figure out how fst/snd work.

####  [rdr.jpg](rdr.jpg) and [rdl.jpg](rdl.jpg)
`rdl` and `rdr` can be useful for aggregating functions (eg. `add`) on lists of values. They require input types of `<a, <x1, x2, x3, ... >>` and `<<x1, x2, x3,...> ,a>` respectively, due to the sizes of their domain/range, as seen in the images.

#### [parity.rby](parity.rby) and [parity.jpg](parity.jpg)
This is the code from eg9 of [egs.rby](egs.rby) and an image showing why `apl^~1` is neccessary to get the input into the correct format to match the `rdl` (ie. one item in the left-domain, and a list of three in the top-domain).

#### Miscellaneous 
 - Put parameters of functions in angle brackets if there are more than one, eg . ``VAR x y . <x, y> $rel <`mult` <x,y>>.``
 - `fst R = [R, id]` - eg `fst R ; mult` will take its first input as the output of R and its second input as the second value inputted from stdin.
 - `/\ 3 R = [R^0, R^1, R^2] = [id, R, R^2]`
