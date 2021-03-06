# 完成作业1.5
 Consider again a decay problem with two types of nuclei of type A into ones of type B, while nuclei of type B, while nuclei of type
B decay into ones of type A. Strictly speaking, this is not a "decay" process,since it is possible for the type B nuclei to turn back
into type A nuclei. A better analogy would be a resonance in which a system can tunnel or move back and forth between two states A and
B which have equal energies. The corresponding rate equations are <br/>
<img src="http://latex.codecogs.com/gif.latex?\frac{dN_A}{dt}=\frac{N_B}{\tau}-\frac{N_A}{\tau}" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?\frac{dN_B}{dt}=\frac{N_A}{\tau}-\frac{N_B}{\tau}" alt="" title="" />  （1.0）<br/>
where for simplicity we have assumed that the two types of decay are characterized by the same time constant,τ. Solve this system of 
equatiions for the numbers of nuclei, NA=100, NB=0, etc., and take τ=1s. Show that your numercial results are consistent with the idea
that the system reaches a steady state in which NA and NB are constant. In such a steady state, the time derivatives dNA/dt and dNB/dt
should vanish.

# 方程的解析
## 假设原子的衰变方程
### <img src="http://latex.codecogs.com/gif.latex?\frac{dN}{dt}=-\frac{N}{\tau}" alt="" title="" />  (1.1) <br/>
对N做泰勒展开得到 <br/>
  ![](http://latex.codecogs.com/gif.latex?N%28%5CDelta%20t%29%3DN%280%29&plus;%5Cfrac%7BdN%7D%7Bdt%7D%5Ccdot%5CDelta%20t&plus;%5Cfrac%7B1%7D%7B2%7D%5Ccdot%5Cfrac%7Bd%5E2N%7D%7Bdt%5E2%7D&plus;...) <br/>
  取前两项得 <br/>
  ![](http://latex.codecogs.com/gif.latex?N%28%5CDelta%20t%29%5Capprox%20N%280%29&plus;%5Cfrac%7BdN%7D%7Bdt%7D%5Ccdot%5CDelta%20t) <br/>
  又有  <br/>
 ![](http://latex.codecogs.com/gif.latex?%5Cfrac%7BdN%7D%7Bdt%7D%3D%5Clim_%7B%5CDelta%20t%5Crightarrow%200%7D%5Cfrac%7BN%28t&plus;%5CDelta%20t%29-N%28t%29%7D%7B%5CDelta%20t%7D%5Capprox%20%5Cfrac%7BN%28t&plus;%5CDelta%20t%29-N%28t%29%7D%7B%5CDelta%20t%7D) <br/>
 ![](http://latex.codecogs.com/gif.latex?N%28t&plus;%5CDelta%20t%29%5Capprox%20N%28t%29&plus;%5Cfrac%7BdN%7D%7Bdt%7D%5Ccdot%5CDelta%20t) （1.2） <br/>
 再由式(1.1)得<br/>
 ![](http://latex.codecogs.com/gif.latex?N%28t&plus;%5CDelta%20t%29%5Capprox%20N%28t%29-%5Cfrac%7BN%28t%29%7D%7B%5Ctau%7D%5Ccdot%5CDelta%20t) 
 
#题目解析
 由上面分析知
 令![](http://latex.codecogs.com/gif.latex?N_A-N_B%3DN)<BR/>
 由（1.2）知    ![](http://latex.codecogs.com/gif.latex?N_A%28t&plus;%5CDelta%20t%29%3DN_A%28t%29&plus;%5Cfrac%7BdN_A%7D%7Bdt%7D%5Ccdot%20%5CDelta%20t)    
 由（1.0）知    ![](http://latex.codecogs.com/gif.latex?N_A%28t&plus;%5CDelta%20t%29%3DN_A%28t%29&plus;%5Cfrac%7BN_B-N_A%7D%7B%5Ctau%7D%5Ccdot%20%5CDelta%20t)    
 同理可知    ![](http://latex.codecogs.com/gif.latex?N_B%28t&plus;%5CDelta%20t%29%3DN_B%28t%29&plus;%5Cfrac%7BN_A-N_B%7D%7B%5Ctau%7D%5Ccdot%20%5CDelta%20t)
 
# 以下是在python中的代码模拟
<pre><code>
 import numpy as np    
 import pylab as pl    
 Number_A=[]    
 Number_B=[]    
 t=[]    
 print('the number of A atoms')    
 number_a=float(input())    
 Number_A.append(number_a)    
 print('the number of B atoms')    
 number_b=float(input())    
 Number_B.append(number_b)    
 print('the time of decay')    
 tdecay=float(input())    
 print('the time step')    
 dt=float(input())    
 t.append(0)    
 for i in range(100):    
     NA=Number_A[i]+((Number_B[i]-Number_A[i])/tdecay)*dt    
     NB=Number_B[i]+((Number_A[i]-Number_B[i])/tdecay)*dt    
     tadd=t[i]+dt    
     Number_A.append(NA)    
     Number_B.append(NB)    
     t.append(tadd)    
 t_max=t[-1]    
 pl.plot(t,Number_A,'r')    
 pl.plot(t,Number_B,'g')    
 pl.title('the decay between A and B')    
 pl.xlabel('the time of decay')    
 pl.ylabel('number of atoms')    
 pl.xlim(0.00,t_max)    
 pl.ylim(Number_B[0],Number_A[0])    
 pl.show()
</code></pre>

# 得到的结果如下图所示
![](https://github.com/Damonphysics/computationalphysics_N2014301020007/blob/master/figure_1.png)

## 致谢曾梓龙同学帮助解决疑问
 
 
