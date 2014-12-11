Practical-Numerical-Method
==========================
# -*- coding: utf-8 -*-
"""
Created on Sat Nov  8 13:52:52 2014

@author: sathyanarayan
"""
    
import numpy                       
import matplotlib.pyplot as plt         
from matplotlib import rcParams
rcParams['font.family'] = 'serif'
rcParams['font.size'] = 16

nx=51
dt=0.001
nt = 50
Vmax=136.
dx = .2156
L=11
rhom=250.
K=(dt*Vmax)/(dx*rhom)
x = numpy.linspace(0,L,nx)
rh = numpy.ones(nx)*20 ##note this change
rh[10:20] = 50

V=Vmax*(1-(rh/rhom))
    
plt.plot(numpy.linspace(0,L,nx), rh, color='#003366', ls='--', lw=3)
plt.ylim(0,50);


for n in range(1, nt):  
    rhn = rh.copy() 
    rh[1:] = rhn[1:]-(Vmax*(1-(rhn[1:]/rhom)))*dt/dx*(rhn[1:]-rhn[0:-1]) 
    rh[0] = 20.0

V=Vmax*(1-(rh/rhom))
AV=sum(V) / float(len(V))
print rh       
        
plt.plot(numpy.linspace(0,L,nx), rh, color='#003366', ls='--', lw=3)
plt.ylim(0,50); 
