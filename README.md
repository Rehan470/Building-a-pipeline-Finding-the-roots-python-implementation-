# Building-a-pipeline-Finding-the-roots-python-implementation-
import numpy as np
import math
def my_pipe_builder(C_ocean,C_land,L,H):
    p1=lambda x:math.sqrt(H**2 + x**2)
    p2=lambda x:L-x
    cost=lambda x: p1(x)*C_ocean+p2(x)*C_land
    error=lambda a,b: cost(a) - cost(b)
    tolerance=1e-6;
    limit=int(np.ceil(np.log2(L/tolerance)))
    i=1;
    a=0;
    b=L;
    while i<limit:
        m=(a+b)/2
        if abs(error(a,b))<tolerance:
            return m
        elif error(a,b)<0:
            b=m
        else:
            a=m
        i+=1
C_ocean=int(input("Enter Cost of per mile under the ocean :"))
C_land=int(input("Enter Cost of pipe per mile on the land :"))
L=int((input("Enter horizonatal distance in mile :")))
H=int((input("Enter vertical distance in  mile :")))
print("Out put is :",my_pipe_builder(C_ocean, C_land,L,H))
