import numpy as np
import matplotlib.pyplot as plt
from matplotlib import cm
from mpl_toolkits.mplot3d import Axes3D

print("✨✨✨    WELCOME TO THE 3D LINEAR EQUATION SOLVER    ✨✨✨")
print("="*65)
print("""
Please enter the coefficients for each equation in the form:

            ax + by + cz = d

Enter 4 values separated by spaces:
    a   b   c   d

Example Input:
    4  -2  7  10
Means:
    4x - 2y + 7z = 10
""")
print("-"*65)
print("               🚀 Let's enter your equations!")
print("-"*65 + "\n")

print(''' you can try a beautiful case ->
      
      (2 3 -1 5 ) . (1 -2 4 3) . (3 1 2 10 )''')
# -------------------------------
#  Input Section
# -------------------------------
print("Equation 1:")
a, b, c, d = map(float, input().split())

print("Equation 2:")
e, f, g, h = map(float, input().split())

print("Equation 3:")
i, j, k, l = map(float, input().split())

# -------------------------------
#  Solve equations
# -------------------------------
A = np.array([[a, b, c],
              [e, f, g],
              [i, j, k]])

B = np.array([d, h, l])

try:
    sol = np.linalg.solve(A, B)
    print("\nSolution (x, y, z) =", sol)
except np.linalg.LinAlgError:
    print("\n❌ The system has no unique solution (det = 0).")
    exit()

x_sol, y_sol, z_sol = sol

# -------------------------------
#  Create 3D plane mesh
# -------------------------------
x = np.linspace(x_sol - 5, x_sol + 5, 30)
y = np.linspace(y_sol - 5, y_sol + 5, 30)
X, Y = np.meshgrid(x, y)

# Ax + By + Cz = D  →  Z = (D - Ax - By) / C
def plane_z(Ax, By, Cz, D):
    if Cz == 0:
        return np.full_like(X, np.nan)  # Avoid division by zero
    return (D - Ax * X - By * Y) / Cz

Z1 = plane_z(a, b, c, d)
Z2 = plane_z(e, f, g, h)
Z3 = plane_z(i, j, k, l)

# -------------------------------
#  3D Plot
# -------------------------------
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')

# Plane surfaces
ax.plot_surface(X, Y, Z1, alpha=0.55, cmap=cm.coolwarm, rstride=1, cstride=1, label='Plane 1')
ax.plot_surface(X, Y, Z2, alpha=0.55, cmap=cm.cividis, rstride=1, cstride=1, label='Plane 2')
ax.plot_surface(X, Y, Z3, alpha=0.55, cmap=cm.PuRd, rstride=1, cstride=1, label='Plane 3')

# Solution point
ax.scatter([x_sol], [y_sol], [z_sol], color='black', s=80, label='Intersection Point')
ax.text(x_sol, y_sol, z_sol, f"  ({x_sol:.2f}, {y_sol:.2f}, {z_sol:.2f})", color='black')

# Labels
ax.set_xlabel("X axis")
ax.set_ylabel("Y axis")
ax.set_zlabel("Z axis")
ax.set_title("Intersection of Three Planes in 3D Space")

plt.show()
