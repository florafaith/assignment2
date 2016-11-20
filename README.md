# assignment2
##**Concept behind Bisection method**
The bisection method is one of the simpler root-ﬁnding methods  
Here is the idea of how it works. Suppose we want to ﬁnd a root of f(x)=1−2x−x5. First notice that f(0)=1, which is above the x-axis and f(1) =−2, which is below the axis. For the function to get from 1 to -2, it must cross the axis somewhere, and that point is the root.1 So we know a root lies somewhere between x = 0 and x =1. See the ﬁgure below  
Next we look at the midpoint of 0 and 1, which is x = .5 (i.e., we bisect the interval) and check the value of the function there. It turns out that f(.5)=−0.03125. Since this is negative and f(0)=1 is positive, we know that the function must cross the axis (and thus have a root) between x = 0 and x = .5. We can then bisect again, by looking at the value of f(.25), which turns out to be around .499. Since this is positive and f(.5) is negative, we know the root must be between x = .25 and x = .5. We can keep up this bisection procedure as long as we like, and we will eventually zero in on the location of the root. Shown below is a graphical representation of this process.  
In general, here is how the bisection method works: We start with values a and b such that f(a) and f(b) have opposite signs. If f is continuous, then we are guaranteed that a root lies between a and b. We say that a and b bracket a root. We then compute f(m), where m=(a+b)/2. If f(m) and f(b) are of opposite signs, we set a = m; if f(m) and if f(a) are of opposite signs, we set b = m. (In the unlikely event that f(m)= 0, then we stop because we have found a root.) We then repeat the process again and again until a desired accuracy is reached. Here is how we might code this in Python: 
def bisection(f, a, b, n): 
  
for i in range(n):  
m = (a + b) / 2  
if f(a)*f(m) < 0:  
b = m   
else:  
a = m  
return m  

##**concept behind the newton rephason method**
Here is a clever way to turn f(x)=0 into a ﬁxed point problem: divide both sides of the equation by−f0(x) and then add x to both sides. This gives  
x-(f(x)/f0(x)) = x. To see why this is useful, let’s look at the derivative of the expression on the left side. We get 1− (f0(x)2−f(x)f00(x))/(f0(x)2)  
Since we have turned f(x)=0 into a ﬁxed point problem, a ﬁxed point p must satisfy f(p)=0. Plugging p into the expression above gives:  
1− (f0(p)2−0)/(f0(p)2) =0. So the derivative at the ﬁxed point is 0. Remember that the ﬂatter the graph is around a ﬁxed point, the faster the convergence, so we should have pretty fast convergence here.  
Iterating x−( f(x))/ (f0(x)) to ﬁnd a root of f is known as Newton’s method.1 As an example, suppose we want a root of f(x)=1−2x−x5. To use Newton’s method, we ﬁrst compute f0(x)=−2−4x5. So we will be iterating    
x−(1−2x−x5)/ (2−4x5)  
Then we pick a starting value for the iteration, preferably something we expect to be close to the root of f, like .5. Wetheniteratethefunction. Usingacalculator, computerprogram, spreadsheet, orwhatever(evenbyhand), we get the following sequence of iterates:  
0.4864864864864865   
0.4863890407290883  
0.486389035934543  
0.486389035934543  
0.486389035934543  
After just a few iterations, Newton’s method has already found as many digits as possible in double-precision ﬂoating-point arithmetic. To get this on a TI calculator, put in .5, press enter, then put in Ans-(1-2*Ans-Ans^5)/(-2-5*Ans^4) and repeatedly press enter.  
In Excel, .5 in the cell A1, put the formula =A1-(1-2*A1-A1^5)/(-2-5*A1^4) into cell A2, and ﬁll down. Here also is a Python program that will produce the above output, stopping when the iterates are equal to about 15 decimal places:   

oldx = 0  
x = .5  
while abs(x - oldx) > 1e-15: oldx,  
x = x, x-(1-2*x-x**5)/(-2-5*x**4)   
print(x)



