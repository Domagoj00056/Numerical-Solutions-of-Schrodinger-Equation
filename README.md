# Numerical-Solutions-of-Schrodinger-Equation

## 📖 Overview
This project investigates the numerical solution of the **time-dependent Schrödinger equation** using finite difference methods. The focus is on analysing **stability, accuracy, and conservation properties** of different numerical schemes.

$$
\textbf{Time-dependent Schrödinger equation: } \quad 
i \frac{\partial \psi}{\partial t} = - \frac{\partial^2 \psi}{\partial x^2}
$$

This project combines **theoretical analysis** with **numerical simulations** to study how well different schemes preserve key physical properties such as **norm (probability) conservation** and **stability**.

📄 **Full Project Report:** [Click here to view the PDF](./project%201.pdf)

---
## Reflection on theoretical part

An analytical solution was obtained using the method of separation of variables, assuming a solution of the form $\psi(x,t) = X(x)T(t)$. This provided a foundation for understanding the behaviour of the equation and served as a benchmark for numerical methods.

From this, we established the **mass conservation** property for Schrödinger-type equations:

$$
\int_0^1 |u(x,t)|^2 \, dx = \int_0^1 |u_0(x)|^2 \, dx
$$

This reflects the physical principle that total probability is preserved over time.

Furthermore, we proved **discrete mass conservation** for the Crank–Nicolson method when applied to the Schrödinger equation:

$$
\Delta x \sum_{k=0}^{k_m} |U_k^n|^2 = \Delta x \sum_{k=0}^{k_m} |u_0(x_k)|^2
$$

showing that the numerical scheme preserves this key physical property at the discrete level.

The theoretical analysis also includes **Von Neumann stability analysis using Fourier modes** and **consistency analysis**. For full details, see the report:

📄 [Click here to view the PDF](./project%201.pdf)


## Reflection on numerical methods being used

The following finite difference schemes were implemented and analysed:

---

### Explicit Scheme

- First-order accurate in time  
- Conditionally stable  
- Does not conserve norm  
- Can become unstable for large time steps  

$$
\textbf{Explicit Scheme:} \quad 
\psi_k^{n+1} = \psi_k^n + i \frac{\Delta t}{(\Delta x)^2} \left(\psi_{k+1}^n - 2\psi_k^n + \psi_{k-1}^n \right)
$$

---

### Implicit Scheme (BTCS)

- First-order accurate in time, second-order in space  
- Unconditionally stable  
- Better numerical behaviour than explicit scheme  
- Requires solving a linear system at each time step  

$$
\textbf{Implicit Scheme:} \quad 
\psi_k^{n+1} - i \frac{\Delta t}{(\Delta x)^2} \left(\psi_{k+1}^{n+1} - 2\psi_k^{n+1} + \psi_{k-1}^{n+1} \right) = \psi_k^n
$$

---

### Crank–Nicolson Method

- Second-order accurate in both space and time  
- Unconditionally stable  
- Conserves norm (physically meaningful)  
- Provides best balance between accuracy and stability  

$$
\textbf{Crank–Nicolson:} \quad 
\psi_k^{n+1} = \psi_k^n + \frac{i \Delta t}{2(\Delta x)^2} \left[ (\psi_{k+1}^n - 2\psi_k^n + \psi_{k-1}^n) + (\psi_{k+1}^{n+1} - 2\psi_k^{n+1} + \psi_{k-1}^{n+1}) \right]
$$

---

## 📊 Key Findings

### Stability and Accuracy

- The **explicit scheme** is conditionally stable and becomes unstable for large $\Delta t$  
- The **implicit (BTCS) scheme** is unconditionally stable but less accurate  
- The **Crank–Nicolson method** provides the best balance of stability and accuracy  

---

### Physical Properties

- The Schrödinger equation requires conservation of probability:
  
  $$
  \sum_k |\psi_k^n|^2 = \text{constant}
  $$

- The **explicit scheme** fails to conserve norm  
- The **Crank–Nicolson method** preserves norm, making it physically reliable  

---

### Overall Observations

- There is a trade-off between:
  - Stability  
  - Accuracy  
  - Computational cost  

- Higher-order methods provide better accuracy but require solving systems of equations  

- Preserving physical properties (such as norm conservation) is essential when solving quantum equations numerically  
