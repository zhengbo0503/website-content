---
title : "Usage of trapz"
date : 2022-11-04T01:28:35Z
toc : true
tag : ["MATLAB"]
katex : true
---

`trapz` is the Trapezoidal numerical integration. Normally the usage will be

```matlab
x = linspace(0,1,100);
y = x.^2;
I = trapz(x,y)
```

This will approximate the integral

$$
\tag{1}
\int_0^1 x^2~\mathrm{d}x 
$$

## One less known usage

There is one usage of `trapz` can cause problem.
Suppose we want to approximate the same integral $(1)$ again, however instead of the code above, we mistype and write 

```matlab
x = linspace(0,1,100);
y = x.^2;
I = trapz(y);
``` 

This can happen if the code is long and the expression is complicated. However, in this case, we no longer calculate the integral $(1)$, instead we apply the trapzoidal numerical integration on the same set of function value but with $x=1,2,\dots,100$. Therefore, we will definitely not get the same answer:

```matlab
>> x = linspace(0,1,100); y = x.^2; trapz(y)
ans =
   3.3002e+01
```

## MATLAB Documentation

From the [Documentation of `trapz`](https://uk.mathworks.com/help/matlab/ref/trapz.html), we have 
> `Q = trapz(Y)` computes the approximate integral of `Y` via the trapezoidal method with unit spacing. 

It should be better if it can be used like `Q = trapz(Y,"unit")`, or show some message such that the user will recognize what set of data they are using and this will eliminate the confusion. For example

```matlab
switch nargin
    case 2
        fprintf('Two set of data are inputted');
    case 1
        fprintf('Only the function value has been inputted\n');
        fprintf('The trapz will use unit spacing');
```

will be more user friendly. 
