```code
x0 = 0;
x1 = 2.0;
Nmax = 20;
eps = 0.0001;
f[x_] := Cos[x];
If[N[f[x0]*f[x1]] > 0, 
 Print["Your values do not satisfy the IVP, so change the values."],
 For[i = 1, i <= Nmax, i++, m = (x0 + x1)/2;
  If[Abs[(x1 - x0)/2] < eps, Return[m],
   Print[i, "th iteration value is :", m];
   Print["Estimated error in ", i, "th iteration is :", (x1 - x0)/2];
   If[f[m]*f[x1] > 0, x1 = m, x0 = m]]];
 Print["Root is : ", m]
  Print["Estimated error in ", i, "th iteration is:", (x1 - x0)/2]]
Plot[f[x], {x, -1, 3}, PlotRange -> {-1, 1},
 PlotStyle -> {Red, Thick}, PlotLabel -> "f[x]=" f[x], 
 AxesLabel -> {x, f[x]}]
```

```
x0 = 0;
x1 = 2.0;
Nmax = 20;
eps = 0.00001;
f[x_] := Cos[x] - x*Exp[x];
If[N[f[x0]*f[x1]] > 0, 
 Print["Your values do not satisfy the IVP, so change the values."],
 For[i = 1, i <= Nmax, i++, m = (x0 + x1)/2;
  If[Abs[(x1 - x0)/2] < eps, Return[m],
   Print[i, "th iteration value is :", m];
   Print["Estimated error in ", i, "th iteration is :", (x1 - x0)/2];
   If[f[m]*f[x1] > 0, x1 = m, x0 = m]]];
 Print["Root is : ", m]
  Print["Estimated error in ", i, "th iteration is:", (x1 - x0)/2]]
Plot[f[x], {x, -1, 3}, PlotRange -> {-10, 10},
 PlotStyle -> {Green, Thick}, PlotLabel -> "f[x]=" f[x], 
 AxesLabel -> {x, f[x]}]
```

