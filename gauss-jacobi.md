```matlab
GaussJacobi[A0_, b0_, x0_, maxiter_] := 
  Module[{A = N[A0], b = N[b0], xk = x0, xk1, i, j, k = 0, n, m, 
    OutputDetails},
   size = Dimensions[A];
   n = size[[1]];
   m = size[[2]];
   If[n != m, 
    Print["Not a square matrix, cannot proceed with Gauss-Jacobi \
method"];
    Return[]];
   OutputDetails = {xk};
   xk1 = Table[0, {n}]; 
   While[k < maxiter, 
    For[i = 1, i <= n, i++, 
     xk1[[i]] = (1/A[[i, i]])*(b[[i]] - 
         Sum[A[[i, j]]*xk[[j]], {j, 1, i - 1}] - 
         Sum[A[[i, j]]*xk[[j]], {j, i + 1, n}])];
    k++;
    OutputDetails = Append[OutputDetails, xk1];
    xk = xk1;];
   colHeading = Table[Subscript[x, s], {s, 1, n}];
   Print[NumberForm[
     TableForm[OutputDetails, TableHeadings -> {None, colHeading}], 
     6]];
   Print["No. of iterations performed: ", maxiter];];
A = {{5, 1, 2}, {-3, 9, 4}, {1, 2, -7}};
b = {10, -14, -33};
X0 = {0, 0, 0};

GaussJacobi[A, b, X0, 15]
```

```matlab
GaussJacobi[A0_, b0_, x0_, maxiter_] := 
  Module[{A = N[A0], b = N[b0], xk = x0, xk1, i, j, k = 0, n, m, 
    OutputDetails},
   size = Dimensions[A];
   n = size[[1]];
   m = size[[2]];
   If[n != m, 
    Print["Not a square matrix, cannot proceed with Gauss-Jacobi \
method"];
    Return[]];
   OutputDetails = {xk};
   xk1 = Table[0, {n}]; 
   While[k < maxiter, 
    For[i = 1, i <= n, i++, 
     xk1[[i]] = (1/A[[i, i]])*(b[[i]] - 
         Sum[A[[i, j]]*xk[[j]], {j, 1, i - 1}] - 
         Sum[A[[i, j]]*xk[[j]], {j, i + 1, n}])];
    k++;
    OutputDetails = Append[OutputDetails, xk1];
    xk = xk1;];
   colHeading = Table[Subscript[x, s], {s, 1, n}];
   Print[NumberForm[
     TableForm[OutputDetails, TableHeadings -> {None, colHeading}], 
     6]];
   Print["No. of iterations performed: ", maxiter];];
A = {{4, 1, 1}, {1, 5, 2}, {1, 2, 3}};
b = {2, -6, -4};
X0 = {0.5, -0.5, -0.5};

GaussJacobi[A, b, X0, 15]
```
