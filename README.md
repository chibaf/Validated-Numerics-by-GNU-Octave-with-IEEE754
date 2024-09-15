# Validated-Numerics-by-GNU-Octave-with-FPU-IEEE754
Validated Numerics by GNU Octave with IEEE754

## change rounding mode on GNU Octave

build:

% mkoctfile --mex setround.c

usage:
<pre>
setround(-1): round toward downward

setround(0): round to nearest

setround(1): round toward upward

setround(2): round Round toward zero
</pre>

## example

p106 (*)

<pre>
octave:2> format long
octave:3> setround(-1)
octave:4> xd=[1/10;(-1)/10;1/10]
xd =

   9.999999999999999e-02
  -1.000000000000001e-01
   9.999999999999999e-02

octave:5> yd=[1/10;2/10;(-3)/10]
yd =

   9.999999999999999e-02
   1.999999999999999e-01
  -3.000000000000001e-01

octave:6> setround(1)
octave:7> xu=[1/10;(-1)/10;1/10]
xu =

   0.100000000000001
  -0.099999999999999
   0.100000000000001

octave:8> yu=[1/10;2/10;(-3)/10]
yu =

   0.100000000000001
   0.200000000000001
  -0.299999999999999

octave:9> xc=(xd+xu)/2
xc =

   0.100000000000001
  -0.099999999999999
   0.100000000000001

octave:10> xr=xu-xc
xr =

   0
   0
   0

octave:11> yc=(yd+yu)/2
yc =

   0.100000000000001
   0.200000000000001
  -0.299999999999999

octave:12> yr=yu-yc
yr =

   0
   0
   0

octave:13> zu=xc'*yc+xc'*yr+xr'*yc-xr'*yr
zu = -3.999999999999999e-02
octave:14> setround(-1)
octave:15> zu=xc'*yc-xc'*yr-xr'*yc-xr'*yr
zu = -4.000000000000001e-02
</pre>

the true value is $-0.04$.

 $-0.04 \belong [-4.000000000000001E^{-02}, -3.999999999999999E^{-02}]$
  
## Refferences

Using directed rounding in Octave/Matlab (Kai Torben Ohlhus) 

https://siko1056.github.io/blog/2021/12/23/octave-matlab-directed-rounding.html

Linux 数値計算ツール、大石進一、コロナ社、2000年, in japanese   (*)

https://www.coronasha.co.jp/np/isbn/9784339023787/
