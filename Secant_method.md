## Secant_method
### Question -01
```matlab
(*x0 = Input["Enter first guess"];
x1 = Input["Enter Second guess"];
Nmax = Input["Enter Nmax guess"];
eps = Input["Enter approx error"];
f[x_] = Input["Enter Function error"];*)
x0 = 0;
x1 = 1.0;
Nmax = 20;
eps = 0.00001;
f[x_] := Cos[x];
For [i=1, i <= Nmax, i++,  
	x2 =x1-((f[x1]*(x1 - x0))/(f[x1]- f[x0]));
	If[Abs[(x1-x2)]/2 < eps, Return[x2],x0=x1;x1=x2];
		Print[i,"th iteration value is :",x2];
		Print["Estimated error in ",i," th iteration is : ",Abs[x1 - x0]]];
	Print["Root is :",x2];
	Print["Estimated error in ",Abs[x2 - x1]];
	Plot[f[x],{x,-1,3},
	PlotRange -> {-2,2},
	PlotStyle -> {Red, Thick}, 
	PlotLabel -> "f[x] = "f [x], 
	AxesLabel -> {x,f[x]}]
```

### Question -02

```matlab
