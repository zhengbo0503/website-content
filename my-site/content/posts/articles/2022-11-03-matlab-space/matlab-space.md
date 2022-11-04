---
title: "MATLAB Space"
date: 2022-11-03T01:28:35Z
toc : true
tags : ["MATLAB"]
---
## `vertcat`

When we concentrate two different vectors in MATLAB, for example 

```matlab
a = [1,2,3,4]; b = [3,4,5];
```

Only `[a,b]` is valid, `[a;b]` is not valid, the output is the following

```matlab
>> [a,b]
ans =
     1     2     3     4     3     4     5
>> [a;b]
Error using vertcat
Dimensions of arrays being concatenated are not consistent. 
```

## Interesting Example

Here is an interesting example from my friend's homework,

```matlab
>> f = -3 * 1 -3*(-2); g = 1 + 1 + 1 +1; k = [f;g]
k =
     3
     4
```

Seems trivial, isn't it? How about we try again, but without using the intermidiate variables `f` and `g`?

```matlab
>> k = [-3 * 1 -3*(-2);1 + 1 + 1 +1]
k =
    -3     6
     3     1
```

The exactly same input rise different problem, is this a bug in MATLAB? Clearly not! And by viewing the [vertcat](https://uk.mathworks.com/help/matlab/ref/double.vertcat.html), I notice the error we made in the above example. In MATLAB, it recognizes the two expressions below as the same 

```matlab
>> A = [1,2]
A =
     1     2
>> A = [1 2]
A =
     1     2
```

Hence in the expression `k = [-3 * 1 -3*(-2);1 + 1 + 1 +1]`, it interprets, for example, the former entry as `-3*1` and `-3*(-2)`. Similarly, the latter one is interpreted as `1+1+1` and `+1`. This is probably due to the plus or minus sign have two meanings in MATLAB 

* Binary operator: `a + b`, and 
* Sign: `-a` will be interpret as `-1*a`.

In order to resolve this problem, we just need to **be consistent on the spacing beside binary operators**, like 

```matlab
>> k = [-3 * 1 - 3 * (-2);1 + 1 + 1 + 1]
k =
     3
     4
```

or 

```matlab
>> k = [-3*1-3*(-2);1+1+1+1]
k =
     3
     4
```

and both gives the same answer as expected.

Personally, I will always add spaces beside the binary operator to make the code more readable. This is also consistence with the spacing policy of the *Microsoft Visual Studio*.

