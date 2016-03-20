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
`fst R = [R, id]` - eg for `fst R ; mult`, the `mult` will take its first input as the output of R and its second input as the second value inputted from stdin.

####  [rdr.jpg](rdr.jpg) and [rdl.jpg](rdl.jpg)
`rdl` and `rdr` can be useful for aggregating functions (eg. `add`) on lists of values. They require input types of `<a, <x1, x2, x3, ... >>` and `<<x1, x2, x3,...> ,a>` respectively, due to the sizes of their domain/range, as seen in the images.

Inductive definition:

`rdr_1 R = fst[-]^~1;R.`

`rdr_(n+1) = fst (apr_n)^~1 ; lsh ; snd R ; rdr_n R.`

[inductiverdr.jpg](inductiverdr.jpg)


#### [parity.rby](parity.rby) and [parity.jpg](parity.jpg)
This is the parity code from eg9 of [egs.rby](egs.rby) and an image showing why `apl^~1` is neccessary to get the input into the correct format to match the `rdl` (ie. one item in the left-domain, and a list of three in the top-domain).

#### [convolver.rby](convolver.rby) and [convolver.jpg](convolver.jpg)
This is the convolver code from eg10 of [egs.rby](egs.rby) and an image showing its diagram. Its input is of the type `<x, <w1, w2, w3>>` Note that `` `D` ``refers to the delay block. Also remeber that since delays are involved, you have to specify the inputs at each clock cycle using a `;` like this: 

    re "
    x0 w0 w1 w2 w3 ; 
    x1 w0 w1 w2 w3 ;
    x2 w0 w1 w2 w3 ; 
    x3 w0 w1 w2 w3 ; 
    x4 w0 w1 w2 w3 "
    
#### Pipelining
To properly pipeline a block, put a `D` at every domain connection and a `D^-1` at every range connection of every element of the block. [Using the rule (A;B)^n == A^n ; B^n](pipeline_horner.png) you can rearrange the delay elements to put the antidelays at the inputs/outputs of the block, where they can be ignored. Then [draw contours](pipeline_contours.png) through the delay elements, making sure each contour crosses an equal number of delays/antidelays, that each delay element is not crossed by more than one contour, and that contours do not cross each other. These are your pipeline stages. It is up to you to find an efficient way to arrange the contours.

#### Definition of Triangle /\
Triangle is defined inductively as `/\ n+1 R = (apr n)^~1 ; [/\ n R , R^n] ; apr n.` To understand why the `apr`s are needed, you have to consider that with them, the domain/range look like `<-,-,-,-> ~ <-,-,-,->`, and without them they look like `<<-,-,->,-> ~ <<-,-,->,->`, so they are needed to keep the types consistent. Remember that `apr n` takes a list of n and a single element, and appends it to the right end of the list, and so `(apr n)^~1` splits a list of size n+1 into a list of size n and and a sngle element. See the diagrams for triangle [with `apr`s](trianglewithapr.jpg)and [without `apr`s](trianglewithoutapr.jpg) to see more clearly the difference.  
#### Miscellaneous
 - #####*Horner's Rule:* if `[P, Q] ; R = R ; Q` then `[/\ n P, Q^n]; rdr n R = rdr n (snd Q ; R)`. ie. [this](hornersrule.jpg).  That `/\ 2 Q` can also be `snd Q`, they are equivalent.

  
 - Put parameters of functions in angle brackets if there are more than one, eg . ``VAR x y . <x, y> $rel <`mult` <x,y>>.``
 inputted from stdin.
 - `/\ 3 R = [R^0, R^1, R^2] = [id, R, R^2]`
