# Automated Error Propagation Tool (v1.0)

[![Python 3](https://img.shields.io/badge/python-3-blue.svg)](https://www.python.org/)
[![SymPy](https://img.shields.io/badge/SymPy-Symbolic%20Math-green.svg)](https://www.sympy.org/)

A lightweight, powerful Python tool designed to automatically compute systematic errors and uncertainties in physical measurements. Developed to streamline data reporting in scientific research and undergraduate laboratories, this script saves researchers valuable time by replacing tedious manual differentiation with exact symbolic mathematics.

---

## 📖 Theory: Understanding Error Propagation

Error propagation is a critical concept when reporting scientific data. In experimental physics and engineering, we rarely measure the final desired quantity directly. Instead, we measure several independent variables—each with its own inherent uncertainty or "error"—and use a mathematical formula to calculate the final result.

If a computed quantity $q$ is a function of several measured variables $x, y, \dots, z$, meaning $q = f(x, y, \dots, z)$, the uncertainty in the final result, denoted as $\delta q$, is dictated by the uncertainties of the independent variables ($\delta x, \delta y, \dots, \delta z$). 

Assuming the uncertainties are independent and random, the total uncertainty is calculated using the **General Formula for Error Propagation**, which sums the individual contributions in quadrature:

$$ \delta q = \sqrt{ \left( \frac{\partial q}{\partial x} \delta x \right)^2 + \left( \frac{\partial q}{\partial y} \delta y \right)^2 + \dots + \left( \frac{\partial q}{\partial z} \delta z \right)^2 } $$

### The Problem This Tool Solves
As the number of variables with uncertainties increases in an equation, manually calculating these partial derivatives ($\frac{\partial q}{\partial x}$) for each variable becomes incredibly tedious, time-consuming, and highly susceptible to human error. 

This program effectively automates these long calculations. By leveraging symbolic mathematics, it accurately computes the exact partial derivatives for any user-defined function, evaluates them at the provided true values, and applies the general formula—delivering fast and rigorously accurate error analysis.

---

## ✨ Features

* **Zero Configuration & Highly Portable:** Can be run locally as a standalone script, or uploaded directly to Jupyter Notebooks and Google Colab.
* **Advanced Symbolic Differentiation:** Utilizes the `SymPy` library to perform exact analytical calculus, preventing the inaccuracies associated with numerical approximations.
* **Complex Mathematical Support:** Accepts standard Python syntax and supports trigonometric and exponential functions (`sin()`, `cos()`, `exp()`, `log()`, etc.).
* **Automated Scientific Output:** Automatically calculates both the "best value" (nominal value) and the propagated error, displaying the final result in standard scientific notation (E-notation) for easy inclusion in lab reports.
* **Interactive CLI:** An intuitive, step-by-step terminal interface that guides the user to input variables, true values, uncertainties, and the final equation.

---

## 🚀 Installation & Usage

**1. Install Dependencies**
The only external dependency required is the SymPy library. Install it via pip:
```bash
pip install sympy
```

**2. Run the Program**
Execute the script from your terminal or command prompt:
```bash
python error_automation.py
```

**3. Follow the Prompts**
*   Enter your variables one by one, separated by spaces: `<Variable_Name> <True_Value> <Uncertainty>` (e.g., `x 3.0 0.1`).
*   Type `done` when finished adding variables.
*   Enter your mathematical expression using Python syntax (e.g., `x**2 + y`).

---

## 🔬 Validation Example: The J.J. Thomson Experiment

To prove the accuracy of this tool, it has been validated against complex, real-world textbook examples, such as the J.J. Thomson "charge-to-mass ratio" experiment detailed in J.R. Taylor's *An Introduction to Error Analysis*.

In this experiment, the charge-to-mass ratio of an electron, $r = e/m$, is determined by accelerating electrons through a voltage $V$ and bending them in a magnetic field. The ratio is given by the formula:

$$ r = \frac{125}{32 \mu_0^2 N^2} \frac{D^2 V}{d^2 I^2} $$

### Student Measurements:
*   **Coil Turns ($N$):** $72$ (exact, no uncertainty)
*   **Field Coil Diameter ($D$):** $661 \pm 2$ mm
*   **Accelerating Voltage ($V$):** $45.0 \pm 0.2$ volts
*   **Curved Path Diameter ($d$):** $91.4 \pm 0.5$ mm
*   **Coil Current ($I$):** $2.48 \pm 0.04$ amps

### Program Execution:
```text
Enter 'done' when you are finished with the variables: 
Enter Variable,True value,error in this format:x 3 0.1

Type "done" if finished 
 Enter your variables, true value and error: D 661 2
Type "done" if finished 
 Enter your variables, true value and error: V 45 0.2
Type "done" if finished 
 Enter your variables, true value and error: d 91.4 0.5
Type "done" if finished 
 Enter your variables, true value and error: i 2.48 0.04
Type "done" if finished 
 done

Enter your expression:
(125*(D**2)*V)/(32*((4*pi*10**-7)**2)*(72**2)*(d**2)*(i**2))

The best value is:  182597569891.547
The error is:  6369121062.69965
1.82597569891547E+11 ± 6.36912106269965E+9
```

### Result Analysis
The tool successfully computes the uncertainty within seconds, calculating $r = 1.825 \times 10^{11} \pm 0.063 \times 10^{11}$ C/kg. This matches the accepted textbook calculation perfectly, demonstrating the program's utility in verifying manual calculations and handling complex physical constants (like $\mu_0 = 4\pi \times 10^{-7}$).

---

## 📚 References

* SymPy Development Team (2023) SymPy: Python library for symbolic mathematics. Available at: https://www.sympy.org 
* Taylor, J.R. (1997) An introduction to error analysis: the study of uncertainties in physical measurements. 2nd edn. Sausalito, CA: University Science Books.