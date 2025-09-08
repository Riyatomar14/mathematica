## Regular Falsi 
### Question no -1
```matlab
x0 = 0;
x1 = 2.0;
Nmax = 20;
eps = 0.0001;
f[x_] := Cos[x];
If[N[f[x0]]*N[f[x1]]> 0,
	Print["These values do not satisfy the IVP so change the value."],
	For [i=1, i <= Nmax, i++,  
		x2 = N[x1-f[x1]*(x1 - x0)/(f[x1]- f[x0])];
		If [Abs[x1-x0]<eps,Return[N[x2]],
			Print[i,"th iterations value is: ", N[x2]];
			Print["Estimated error in ",i," th iteration is : ",N[x1 - x0]]];
	If[f[x2]*f[x1]>0,x1=x2,x0=x2]];
		Print["Root is :",N[x2]];
		Print["Estimated error in ",i," th iteration is : ",N[x1 - x0]]];
		If[N[f[x0]]*N[f[x1]]< 0,Plot[f[x],{x,-1,3}]]	

```
