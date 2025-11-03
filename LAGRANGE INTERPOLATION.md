```matlab
LagrangePolynomial[x0_, f0_] := 
 Module[{xi = x0, fi = f0, n, m, polynomial}, n = Length[xi]; 
  m = Length[fi];
  If[n != m,
   Print["List of points and function's values are not of same size"];
   Return[];];
  For[i = 1, i <= n, i++, 
   L[i, x_] = (Product[(x - xi[[j]])/(xi[[i]] - xi[[j]]), {j, 1, 
         i - 1}])*(Product[(x - xi[[j]])/(xi[[i]] - xi[[j]]), {j, 
         i + 1, n}]);];
  polynomial[x_] = Sum[L[k, x]*fi[[k]], {k, 1, n}];
  Return[polynomial[x]];]
```
```matlab
nodes = {0, 1, 3};
values = {1, 3, 55};
LagrangePolynomial[x_] = LagrangePolynomial[nodes, values]

```
```matlab
nodes = {0, 1, 3};
values = {1, 3};
LagrangePolynomial[x_] = LagrangePolynomial[nodes, values]
```
```matlab
nodes = {1, 3, 5, 7, 9};
values = {N[Log[1]], N[Log[3]], N[Log[5]], N[Log[7]], N[Log[9]]};
LagrangePolynomial[x_] = LagrangePolynomial[nodes, values]
Simplify[%]
Plot[{LagrangePolynomial[x], Log[x]}, {x, 1, 10}, 
 Ticks -> {Range[0, 10]}, PlotLegends -> "Expressions"]
```
```matlab
nodes = {-1, 0, 1, 2};
values = {5, 1, 1, 11};
LagrangePolynomial[x_] = LagrangePolynomial[nodes, values]
Simplify[%]
LagrangePolynomial[1.5]
```
