```text
ClearAll;
x0 = Input["Enter initial guess:"];
Nmax = Input["Enter maximum number of iterations:"];
eps = Input[ "Enter the value of convergence parameter: "];
Print["x0=", x0];
Print["Nmax=", Nmax];
Print["Epsilon =", eps];
f[x_] := Cos[x];
Print["f[x] :=", f[x]];
Print["f[x]:=", D[f[x], x]];
For[i = 1, i <= Nmax, i++,
  x1 = N[x0 - (f[x] /. x -> x0)/(D[f[x], x] /. x -> x0)];
  If[Abs[x1 - x0] < eps, Return[x1], x0p = x0; x0 = x1];
  Print["In", i,
   "th Number of iterations the approximation to root is:", x1];
  Print["Estimated error is :", Abs[x1 - x0p]]];
Print["the final approximation of root is:", x1];
Print["Estimated error is :", Abs[x1 - x0]];
Plot[f[x], {x, -1, 3}]
```

```text
ClearAll;
x0 = Input["Enter initial guess:"];
Nmax = Input["Enter maximum number of iterations:"];
eps = Input[ "Enter the value of convergence parameter: "];
Print["x0=", x0];
Print["Nmax=", Nmax];
Print["Epsilon =", eps];
f[x_] := Cos[x] - x*Exp[x];
Print["f[x] :=", f[x]];
Print["f[x]:=", D[f[x], x]];
For[i = 1, i <= Nmax, i++,
  x1 = N[x0 - (f[x] /. x -> x0)/(D[f[x], x] /. x -> x0)];
  If[Abs[x1 - x0] < eps, Return[x1], x0p = x0; x0 = x1];
  Print["In", i,
   "th Number of iterations the approximation to root is:", x1];
  Print["Estimated error is :", Abs[x1 - x0p]]];
Print["the final approximation of root is:", x1];
Print["Estimated error is :", Abs[x1 - x0]];
Plot[f[x], {x, -1, 3}]
```
