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
