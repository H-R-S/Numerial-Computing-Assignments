# [NC Assignments (Solved)](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/README.md)

1 Bisection Method 
### Code:
```
clc
clear all
close all

 
f=inline('(x^3+3*x-5)');
a=1;
b=2;
tol=1e-3;
error=1;
i=1;
while(error>tol)
    disp('___________________')
    i
    a
    b
    c=(a+b)/2
    fc=f(c)
    if(f(c)*f(a)<f(c)*f(b))
       b=c;
    else
        a=c;
    end
    if(i>1)
        error=abs((c-temp)/c)
    end
    temp=c;
    i=i+1;
end

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/bisection_screenshot.png)
### Output:
```
________________
i =
     1
a =
   1
b =
   2
c =
  1.5000
fc =
  2.8750
___________________
i =
2
a =
 1
b =
  1.5000
c =
  1.2500
fc =
0.7031
error =
  0.2000
___________________
i =
  3
a =
  1
b =
 1.2500
c =
  1.1250
fc =
 -0.2012
error =
 0.1111
___________________
i =
 4
a =
 1.1250
b =
 1.2500
c =
  1.1875
fc =
  0.2371
error =
 0.0526
___________________

i =
 5
a =
1.1250
b =
1.1875
c =
 1.1563
fc =
  0.0146
error =
0.0270
___________________
i =
  6
a =
 1.1250
b =
 1.1563
c =
 1.1406
fc =
  -0.0941
error =
 0.0137
___________________
i =
   7
a =
    1.1406
b =
    1.1563
c =
    1.1484
fc =
   -0.0400
error =
    0.0068
___________________
i =
    8
a =
 1.1484
b =
 1.1563
c =
    1.1523
fc =
   -0.0128
error =
  0.0034
___________________
i =
    9
a =
    1.1523
b =
    1.1563
c =
    1.1543
fc =
   8.7725e-04
error =
    0.0017
___________________
i =  
  10
a =
    1.1523
b =
    1.1543
c =
    1.1533
fc =
   -0.0060
error =
   8.4674e-04
>>

```

2 Secant Method
### Code:
```
clc
clear all
close all

f=inline('((3*x)+sin(x)-exp(x))');
a=0;
b=1;
tol=1e-3;
error=1;
i=1;
while(error>tol)
    disp('___________________')
    i
    a
    b
    c=(a*f(b)-b*f(a))/(f(b)-f(a))
    fc=f(c)
    
    if(i==1)
        if(f(c)*f(a)<f(c)*f(b))
           b=c;
           temp=c;
        else
            a=c;
            temp=c;
        end
    else if(i==2)
        a=temp;
        b=c;
        error=abs((b-a)/b);
    else
        a=b;
        b=c;
        error=abs((b-a)/b);
        end
    end
    
    i=i+1;
end

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/secant_screenshot.png)
### Output:
```
___________________
i =
    1
a =
     0
b =
     1
c =
    0.4710
fc =
    0.2652
___________________
i =
     2
a =
     0
b =
   0.4710
c =
    0.3723
fc =
    0.0295
___________________
i =
     3
a =
    0.4710
b =
    0.3723

c =
 0.3599
fc =
   -0.0013
___________________
i =
     4
a =
    0.3723
b =
    0.3599
c =
    0.3604
fc =
   5.5301e-06


___________________
i =
     5
a =
    0.3599
b =
    0.3604
c =
    0.3604
fc =
   1.0213e-09
>>

```

3 Newton Raphson
### Code:
```
clc
clear all
close all
 

f = inline('(3*x) + sin(x) - exp(x)');
fd =inline('3 + cos(x) - exp(x)');
 
x0 = 0.5;
tol = 1e-3;
error = 1;
i = 1;
 
while error > tol
    disp('_____________________')
    disp(i)
    
    x1 = x0 - (f(x0) / fd(x0));
    fx1 = f(x1);
    
    disp('x:')
    disp(x1)
    disp('f(x):')
    disp(fx1)
    
    if i > 1
        error = abs((x1 - x0) / x1);
        disp('Error:')
        disp(error)
    end
    
    x0 = x1;
    i = i + 1;
end

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/newton_raphson_screenshot.png)
### Output:
```
_____________________
     1
x:
    0.3516
f(x):
   -0.0221
_____________________
     2
x:
    0.3604
f(x):
  -6.8143e-05
Error:
    0.0243
_____________________
     3
x:
    0.3604
f(x):
  -6.6267e-10
Error:
   7.5569e-05
>>

```

4 Gauss Seidel
### Code:
```
clc
clear all
close all
 

x = 0;y = 0;z = 0;
error_tol = 1e-3;
error = inf;
iter = 0; 
 
disp('Iteration    x           y          z      Error_x    Error_y   Error_z')
 
while error > error_tol
    x_prev = x;
    y_prev = y;
    z_prev = z;
 
    x = (105 - y - z) / 6;
    y = (155 - 4 * x - 3 * z) / 8;
    z = (-65 + 5 * x + 4 * y) / 10;
 
    error_x = x - x_prev;
    error_y = y - y_prev;
    error_z = z - z_prev;
 
    error = max(abs(error_x), abs(error_y));
    error = max(error, abs(error_z));
 
    iter = iter + 1;
 
    disp([iter, x, y, z, error_x, error_y, error_z])
end
 
disp('Final solution:')
disp([x, y, z])
disp('Iterations:')
disp(iter)
disp('Errors:')
disp([error_x, error_y, error_z])

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/gauss_seidel_screenshot.png)
### Output:
```
Iteration    x              y                z              Error_x    Error_y      Error_z
  1.0000   17.5000   10.6250    6.5000   17.5000   10.6250   6.5000
  2.0000   14.6458    9.6146    4.6688   -2.8542    -1.0104    -1.8312
   3.0000   15.1194   10.0645    5.0855    0.4736    0.4499    0.4168
    4.0000   14.9750    9.9804    4.9797   -0.1444   -0.0841   -0.1058
    5.0000   15.0066   10.0043    5.0050    0.0317    0.0239    0.0254
    6.0000   14.9984    9.9989    4.9988   -0.0082   -0.0054   -0.0063
    7.0000   15.0004   10.0003    5.0003    0.0019    0.0014    0.0015
     8.0000   14.9999    9.9999    4.9999   -0.0005   -0.0003   -0.0004
Final solution:
 14.9999    9.9999    4.9999

Iterations:
   8

Errors:
  1.0e-03 *
  -0.4836   -0.3298   -0.3737

>>

```

5 Jacobi’s
### Code:
```
clc
clear all
close all
 

x = 0; y = 0; z = 0;
error_tol = 1e-3; 
 
error = inf; 
iter = 0; 
 
disp('Iteration    x           y          z      Error_x    Error_y   Error_z')
 
while error > error_tol
    x_prev = x;
    y_prev = y;
    z_prev = z;
 
    x = (105 - y_prev - z_prev) / 6;
    y = (155 - 4 * x_prev - 3 * z_prev) / 8;
    z = (-65 + 5 * x_prev + 4 * y_prev) / 10;
 
    error_x = x - x_prev;
    error_y = y - y_prev;
    error_z = z - z_prev;
 
    error = max(abs(error_x), abs(error_y));
    error = max(error, abs(error_z));
 
    iter = iter + 1;
 
   
    disp([iter, x, y, z, error_x, error_y, error_z])
end
 
disp('Final solution:')
disp([x, y, z])
disp('Iterations:')
disp(iter)
disp('Errors:')
disp([error_x, error_y, error_z])

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/jacobis_screenshot.png)
### Output:
```
    Iteration    x           y                  z              Error_x    Error_y   Error_z
    1.0000   17.5000   19.3750   -6.5000   17.5000   19.3750   -6.5000
    2.0000   15.3542   13.0625   10.0000   -2.1458   -6.3125   16.5000
    3.0000   13.6563    7.9479    6.4021   -1.6979   -5.1146   -3.5979
    4.0000   15.1083   10.1461    3.5073    1.4521    2.1982   -2.8948
    5.0000   15.2244   10.5056    5.1126    0.1161    0.3595    1.6053
    6.0000   14.8970    9.8456    5.3145   -0.3275   -0.6600    0.2019
    7.0000   14.9733    9.9336    4.8867    0.0764    0.0880   -0.4278
    8.0000   15.0299   10.0558    4.9601    0.0566    0.1222    0.0734
    9.0000   14.9973   10.0000    5.0373   -0.0326   -0.0558    0.0772
   10.0000   14.9938    9.9873    4.9987   -0.0036   -0.0126   -0.0386
   11.0000   15.0023   10.0036    4.9918    0.0085    0.0163   -0.0068
   12.0000   15.0008   10.0019    5.0026   -0.0016   -0.0017    0.0108
   13.0000   14.9992    9.9986    5.0011   -0.0015   -0.0033   -0.0015
   14.0000   15.0000    9.9999    4.9991    0.0008    0.0013   -0.0021
   15.0000   15.0002   10.0003    5.0000    0.0001    0.0004    0.0009

Final solution:
   15.0002   10.0003    5.0000

Iterations:
    15

Errors:
  1.0e-03 *
    0.1253    0.3782    0.9167
>>

```

6 Numerical Differentiation
### Code:
```
clc
clear all
close all

f=inline('exp(5*x)');
x0=1.5;
h=0.1;
ActualV=9.0402e+03;
 
%% Two point formula
TwoPointFormula=(f(x0+h)-f(x0))/h
 
TPFError=-((ActualV-TwoPointFormula)/ActualV)*100
 
%% Three Point Forward difference
ThreePointForwardDifference=(1/(2*h))*(-3*f(x0)+4*f(x0+h)-f(x0+2*h))
 
TPFDError=((ActualV-ThreePointForwardDifference)/ActualV)*100
 
%% Three Point Backward Difference
ThreePointBackwardDifference=(1/(2*h))*(3*f(x0)-4*f(x0-h)+f(x0-2*h))
 
TPBDError=((ActualV-ThreePointBackwardDifference)/ActualV)*100
 
%% Three Point Central Difference
ThreePointCentralDifference=(1/(2*h))*(f(x0+h)-f(x0-h))
 
TPCDError=-((ActualV-ThreePointCentralDifference)/ActualV)*100
 
%% Five Point Central Difference
FivePointCentralDifference=(1/(12*h))*(f(x0-2*h)-8*f(x0-h)+8*f(x0+h)-f(x0+2*h))
 
FPCDError=((ActualV-FivePointCentralDifference)/ActualV)*100
 
%% Actual 
g='exp(5*x)';
syms x
gdx=diff(g,x);
gd=inline(gdx);
ActualValue=gd(x0)

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/numerical_differentiation_screenshot.png)
### Output:
```
TwoPointFormula =
   1.1729e+04
TPFError =
   29.7444
ThreePointForwardDifference =
   7.9247e+03
TPFDError =
   12.3396
ThreePointBackwardDifference =
   8.5137e+03
TPBDError =
    5.8242
ThreePointCentralDifference =
   9.4216e+03
TPCDError =
    4.2192

FivePointCentralDifference =
   9.0208e+03
FPCDError =
    0.2145
ActualValue =
   9.0402e+03
>>

```

7 Numerical  Integration
### Code:
```
clc
clear all
close all
 
 
f=inline('x*log(x)')
SL=1.5;
EL=3;
ActualV=2.8001;
%% Trapezoidal Rule
h=1.5;
TrapezoidalRule=(h/2)*(f(SL)+f(EL))
 
TRError=-((ActualV-TrapezoidalRule)/ActualV)*100
 
%% Simpson Rule
h=0.75;
SimpsonRule=(h/3)*(f(SL)+4*f(SL+h)+f(EL))
 
SRError=-((ActualV-SimpsonRule)/ActualV)*100
 
%% 3/8 Simpson Rule
h=0.5;
SimpsonRule3by8=((3*h)/8)*(f(SL)+3*f(SL+h)+3*f(SL+2*h)+f(EL))
 
SR3Error=-((ActualV-SimpsonRule3by8)/ActualV)*100
 
%% Composite Trapezoidal
h=0.1;
sum=0;sp=h;
for i=1:((EL-SL)/h)-1
    sum=sum+f(SL+sp);
    sp=sp+h;
end
 
CompositeTrapezoidalRule=(h/2)*(f(SL)+2*sum+f(EL))
 
CTRError=-((ActualV-CompositeTrapezoidalRule)/ActualV)*100
 
%% Boole's Rule
h=0.375;
BoolesRule=((2*h)/45)*(7*f(SL)+32*f(SL+h)+12*f(SL+2*h)+32*f(SL+3*h)+7*f(EL))
 
BRError=-((ActualV-BoolesRule)/ActualV)*100
 
%% Actual
g='x*log(x)';
syms x
ActualValue=eval(int(g,x,[1.5 3]))

```
### ScreenShot:
![ScreenShot](https://github.com/H-R-S/Numerial-Computing-Assignments/blob/main/screen_shots/numerical_integration_screenshot.png)
### Output:
```
f =
  Inline function:
  f(x) = x*log(x)
TrapezoidalRule =
    2.9280
TRError =
    4.5686
SimpsonRule =
    2.8006
SRError =
    0.0179
SimpsonRule3by8 =
    2.8003
SR3Error =
    0.0082
CompositeTrapezoidalRule =
    2.8007
CTRError =
   0.0209

BoolesRule =
    2.8001
BRError =
  4.0020e-04
ActualValue =
    2.8001
>>

```
