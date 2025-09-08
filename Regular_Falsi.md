## Regular Falsi 
### Question no -1
```matlab
x0 = Input["enter first guess"];
x1 = Input["Enter secong guess"];
Nmax = Input["enter maximum number of iterations:"];
eps = Input["enter the value of convergence parameter: "];
Print["x0= ", x0];
Print["x1=", x1];
Print["Nmax= ", Nmax];
Print["epsilon=", eps];
f[x_] := Cos[x];
Print["f(x) :=", f[x]];
If[N[f[x0]*f[x1]] > 0,
  Print["these values do not satisfy the IvP so change the values."],
  For[i = 1, i <= Nmax, i++,
   x2 = N[x1 - f[x1]*(x1 - x0)/(f[x1] - f[x0])];
   If [Abs[x1 - x0] < eps, Return [N[x2]],
    Print[i, "th iteration value is:", N[x1 - x0]]];
   If[f[x2]*f[x1] > 0, x1 = x2, x0 = x2]]];
Print["root is:", N[x2]];
Print["estimated error is ", N[x1 - x0]];
Plot[f[x], {x, -1, 3}]

```
### Question no-2
```matlab
x0 = Input["Enter first guess: "];
x1 = Input["Enter second guess: "];
Nmax = Input["Enter maximum number of iterations: "];
eps = Input["Enter the value of convergence parameter (epsilon): "];

Print["x0 = ", x0];
Print["x1 = ", x1];
Print["Nmax = ", Nmax];
Print["epsilon = ", eps];

f[x_] := Cos[x];
Print["f(x) := Cos[x]"];

If[N[f[x0]*f[x1]] > 0, 
  Print["These values do not satisfy the IVP (no sign change). Please \
change the values."], 
  For[i = 1, i <= Nmax, i++, 
   x2 = N[(x0*f[x1] - x1*f[x0])/(f[x1] - f[x0])];
   If[Abs[f[x2]] < eps, Print["Converged after ", i, " iterations."];
    Print["Root is approximately: ", N[x2]];
    Print["Estimated function error: ", N[Abs[f[x2]]]];
    Break[], 
    Print[i, "th iteration: x = ", N[x2], ", f(x) = ", N[f[x2]], 
      ", error estimate = ", N[Abs[f[x2]]]];];
   If[f[x0]*f[x2] < 0, x1 = x2, x0 = x2];];
  If[i > Nmax, Print["Did not converge within ", Nmax, " iterations."];
   Print["Last approximation is: ", x2];
   Print["Estimated function error is: ", N[Abs[f[x2]]]];];
  Plot[f[x], {x, Min[x0, x1] - 1, Max[x0, x1] + 1}, 
   PlotLabel -> "Plot of f(x) = Cos[x]", AxesLabel -> {"x", "f(x)"}]];



```
