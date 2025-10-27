```matlab
NDD[x0_, f0_, startindex_, endindex_] :=
  Module[{x = x0, f = f0, i = startindex, j = endindex, answer},
   If[i == j, Return[f[[i]]], answer =
      (NDD[x, f, i + 1, j] - NDD[x, f, i, j - 1])/(x[[j]] - x[[i]]);
     Return[answer]];];
x = {0.5, 1.5, 3, 5, 6.5, 8};
f = {1.625, 5.875, 31, 131, 282.125, 521};
NDD[x, f, 1, 2]
```
```matlab
NDDP[x0_, f0_] :=
  Module[{x1 = x0, f = f0, n, newtonPolynomial, k, j},
   n = Length[x1];
   newtonPolynomial[y_] = 0;
   For[i = 1, i <= n , i++, prod[y_] = 1;
    For[k = 1, k <= i - 1, k++, prod[y_] = prod[y]*(y - x1[[k]])];
    newtonPolynomial[y_] =
     newtonPolynomial[y] + NDD[x1, f, 1, i]*prod[y]];
   Return[newtonPolynomial[y]];];
nodes = {0, 1, 3};
values = {1, 3, 55};
NDDP[nodes, values]
```
