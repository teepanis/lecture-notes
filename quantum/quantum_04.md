# ศึกษา Superposition

ใช้ภาษาไพทอนใน [https://matplotlib.online](http://matplotlib.online) หรือเขียนในเครื่องคอมพิวเตอร์ของตนเอง แต่ใช้ออนไลน์สะดวกกว่ามาก

เขียนโค้ดสั้น ๆ ต่อไปนี้

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as ani

fig, ax = plt.subplots()

def update(t):
    L = 2
    m = 1
    hbar = 1
    k = 1*np.pi/L
    E = hbar**2*k**2/(2*m)
    A = np.sqrt(2/L)
    x = np.linspace(0,L,100)
    psi = A*np.sin(k*x)
    Psi = psi*np.exp(-1j*E*t/hbar)

    ax.clear()

    ax.plot(x,np.abs(psi)**2,color='g',label='$|\Psi(x)|^2$')
    ax.plot(x,np.real(Psi),label='Re($\Psi(x,t)$)')
    ax.plot(x,np.imag(Psi),label='Im($\Psi(x,t)$)')
    ax.set_ylim([-2,+2])
    ax.grid()
    ax.legend(loc='upper right')


ani.FuncAnimation(fig, update, frames=100)

plt.show()
```




