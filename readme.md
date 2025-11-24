# 3D Linear Algebra Solver – Project Report

This project solves a system of three linear equations in three variables and visualizes the corresponding three planes in 3D space. It computes the intersection point of the planes using matrix algebra and displays the result graphically using Matplotlib.
##  Features
Solves systems of the form:
  \
  ax + by + cz = d  
  ex + fy + gz = h  
  ix + jy + kz = l  
  \
Uses `numpy.linalg.solve()` to compute the exact solution.
Generates a smooth 3D meshgrid to reconstruct each plane.
Plots all three planes in 3D with transparency.
Highlights the intersection point of the planes.
Provides both numerical and graphical interpretation.
##  Project Structure
```
Project/
│── report.pdf
│── main.py
│── graph.png
│── README.md  ← (this file)
```
##  How the Code Works
1. **User Input:**  
   The user enters the coefficients (a, b, c, d) for each equation in one line.

2. **Matrix Form Conversion:**  
   The equations are represented in matrix form AX = B.

3. **Solving the System:**  
   `numpy.linalg.solve()` determines the unique solution (x, y, z).

4. **3D Plane Construction:**  
   Using `numpy.meshgrid()`, the program generates a grid for X and Y and computes Z for each plane.

5. **Visualization:**  
   - Matplotlib's 3D plotting tools render the three planes.
   - Different color maps separate the planes visually.
   - The intersection point is plotted and labeled clearly.
##  Graphical Representation
The 3D plot illustrates:
- The three planes
- Their intersection point
- Axes labels
- Visual distinction through color maps and transparency

(See `graph.png`)
## Requirements
Install the required libraries with:
```
pip install numpy matplotlib
```
## Running the Program
Run the Python script using:
```
python main.py
```
You will be prompted to enter values for three equations.
## 🎯 Conclusion
This project demonstrates the power of Python for combining numerical linear algebra and 3D visualization. It provides a strong conceptual link between algebraic solutions and geometric interpretation.
## Author
**Rishab Jain**
Reg. No:25BCE10989  
VIT Bhopal University  
