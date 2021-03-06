# UnicodeGraphics

[![Build Status](https://travis-ci.org/rafaqz/UnicodeGraphics.jl.svg?branch=master)](https://travis-ci.org/rafaqz/UnicodeGraphics.jl)
[![codecov.io](http://codecov.io/github/rafaqz/UnicodeGraphics.jl/coverage.svg?branch=master)](http://codecov.io/github/rafaqz/UnicodeGraphics.jl?branch=master)

Convert a matrix of Real into a braile or block Unicode string, real fast.

```
pac = [0 0 0 0 0 0 0 1 1 1 1 1 1 0 0 0 0 0 0 0;
       0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0;
       0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0;
       0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0;
       0 0 1 1 1 1 1 1 1 0 0 1 1 1 1 1 1 1 1 0;
       0 1 1 1 1 1 1 1 1 0 0 1 1 1 1 1 1 1 1 0;
       0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0;
       1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0;
       1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0;
       1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0;
       1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 1;
       1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0;
       1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0;
       0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0;
       0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0;
       0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0;
       0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0;
       0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0;
       0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0;
       0 0 0 0 0 0 0 1 1 1 1 1 1 0 0 0 0 0 0 0]

julia> print(blockize(pac))
     ▄▄██████▄▄
  ▄██████████████▄
 ▄███████  ████████
▄██████████████▀▀
███████████▀▀
███████████▄▄      ▀
▀██████████████▄▄
 ▀█████████████████
  ▀██████████████▀
     ▀▀██████▀▀
```

Or braile:

```julia
ghost = [1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0;
         0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0;
         1.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0 0.0 0.0 0.0 0.0 1.0;
         0.0 0.0 0.0 0.0 0.0 0.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 0.0 0.0 0.0 0.0 0.0;
         1.0 0.0 0.0 0.0 0.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 0.0 0.0 0.0 1.0;
         0.0 0.0 0.0 0.0 1.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 0.0 0.0 0.0;
         1.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 1.0 1.0 0.0 0.0 0.0 0.0 1.0 1.0 0.0 0.0 1.0;
         0.0 0.0 0.0 0.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 0.0 0.0 0.0;
         1.0 0.0 0.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 0.0 1.0;
         0.0 0.0 0.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 1.0 0.0 0.0;
         1.0 0.0 0.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 0.0 1.0;
         0.0 0.0 0.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 0.0 0.0;
         1.0 0.0 0.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 0.0 1.0;
         0.0 0.0 0.0 1.0 1.0 0.0 1.0 1.0 1.0 0.0 0.0 1.0 1.0 1.0 0.0 1.0 1.0 0.0 0.0;
         1.0 0.0 0.0 1.0 0.0 0.0 0.0 1.0 1.0 0.0 0.0 1.0 1.0 0.0 0.0 0.0 1.0 0.0 1.0;
         0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0;
         1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0 0.0 1.0]


julia> print(brailize(view(ghost, 2:15, 4:17), 0.5))                                                                         
⠀⣠⣴⣶⣦⣄⠀                                                                                                                
⣨⡄⢹⣯⡄⢹⣇                                                                                                                
⣿⣶⣿⣿⣶⣿⣿                                                                                                                
⠋⠈⠛⠀⠛⠁⠙                                                                                                                
```
