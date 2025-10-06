``` matlab
GaussSeidelMatrixForm[A0_, b0_, x0_, maxiter_] := 
  Module[{A = N[A0], b = N[b0], xk = x0, k = 0, D, L, U, DLinv, 
    OutputDetails}, D = DiagonalMatrix[Diagonal[A]];
   L = LowerTriangularize[A, -1];
   U = UpperTriangularize[A, 1];
   DLinv = Inverse[D + L];
   OutputDetails = {xk};
   While[k < maxiter, xk = -DLinv.U.xk + DLinv.b;
    OutputDetails = Append[OutputDetails, xk];
    k++;];
   colHeading = Table[Subscript[x, s], {s, 1, Length[x0]}];
   Print[NumberForm[
     TableForm[OutputDetails, TableHeadings -> {None, colHeading}], 
     6]];
   Print["No. of iterations performed: ", maxiter];];
A = {{5, 1, 2}, {-3, 9, 4}, {1, 2, -7}};
b = {10, -14, -33};
X0 = {0, 0, 0};
GaussSeidelMatrixForm[A, b, X0, 15]
```
```matlab
GaussSeidel[A0_, b0_, x0_, maxiter_] := 
  Module[{A = N[A0], b = N[b0], xk = x0, xk1, i, j, k = 0, n, m, 
    OutputDetails, size, colHeading}, size = Dimensions[A];
   n = size[[1]];
   m = size[[2]];
   If[n != m, 
    Print["Not a square matrix, cannot proceed with Gauss-Seidel \
method"];
    Return[]];
   OutputDetails = {xk};
   xk1 = Table[0, {n}]; 
   While[k < maxiter, 
    For[i = 1, i <= n, i++, 
     xk1[[i]] = (1/A[[i, i]])*(b[[i]] - 
         Sum[A[[i, j]]*xk1[[j]], {j, 1, i - 1}] - 
         Sum[A[[i, j]]*xk[[j]], {j, i + 1, n}])];
    xk = xk1; OutputDetails = Append[OutputDetails, xk];
    k++;];
   colHeading = Table[Subscript[x, s], {s, 1, n}];
   Print[NumberForm[
     TableForm[OutputDetails, TableHeadings -> {None, colHeading}], 
     6]];
   Print["No. of iterations performed: ", maxiter];];
A = {{5, 1, 2}, {-3, 9, 4}, {1, 2, -7}};
b = {10, -14, -33};
X0 = {0, 0, 0};
GaussSeidel[A, b, X0, 15];

```
