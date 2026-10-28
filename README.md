# Physics-Informed-Neural-Network
I have implemented PINNs to solve PDEs i.e Poisson, Heat and Wave. I am developing a Hybrid Finite Difference–Physics-Informed Neural Network (HFD-PINN) approach to solve this PDEs in complex geometries, using a rhombus-shaped computational domain as the test case.
# Physics-Informed Neural Networks (PINNs) for Partial Differential Equations

Exploring the intersection of **scientific computing, numerical methods, and deep learning** through Physics-Informed Neural Networks (PINNs) and Hybrid Finite Difference–Physics-Informed Neural Networks (HFD-PINNs).

## 📌 Project Overview

I have implemented a neural network framework with the flexibility to solve **Poisson, heat, and wave equations** using Physics-Informed Neural Networks (PINNs). Building on this foundation, I am developing a hybrid approach that combines neural networks with compact finite difference methods to solve partial differential equations (PDEs) in complex geometries.

The project uses a **rhombus-shaped computational domain** to investigate how finite difference approximations and neural networks can be combined to approximate PDE solutions while accounting for irregular domain boundaries.

## 🎯 Objectives

- Implement PINNs for Poisson, heat, and wave equations.
- Develop a hybrid finite difference–PINN framework for solving PDEs in a non-rectangular domain.
- Use a Signed Distance Function (SDF) to represent the computational domain and identify valid interior points.
- Apply compact finite difference approximations to calculate spatial derivatives.
- Use automatic differentiation for time derivatives and as a fallback for spatial derivatives where finite difference stencils are unavailable.
- Evaluate solution accuracy, convergence behaviour, and computational cost.
- Compare the HFD-PINN approach with conventional PINNs.

## 🧮 Mathematical Problems

The framework considers three benchmark PDEs:

### 1. Poisson Equation

A representative elliptic PDE:

$$
-\nabla^2 u(x,y)=f(x,y)
$$

Used to investigate the approximation of steady-state solutions.

### 2. Heat Equation

A representative parabolic PDE:

$$
\frac{\partial u}{\partial t}-\nabla^2u=f(x,y,t)
$$

Used to investigate time-dependent diffusion problems.

### 3. Wave Equation

A representative hyperbolic PDE:

$$
\frac{\partial^2u}{\partial t^2}-\nabla^2u=f(x,y,t)
$$

Used to investigate time-dependent wave propagation.

The implementation uses analytical solutions to construct consistent forcing terms and evaluate the numerical predictions.

## 🔷 Computational Domain

The current domain is a rhombus defined by

$$
\Omega=\{(x,y): |x|+|y|<1\}.
$$

A Signed Distance Function (SDF) helps identify points inside and outside the domain. This allows the computational grid and finite difference stencils to account for the non-rectangular geometry.

## ⚙️ Methodology

### Conventional PINNs

A fully connected neural network approximates the unknown solution:

$$
u_\theta(x,y,t)\approx u(x,y,t),
$$

where \(\theta\) represents the trainable network parameters.

The network is trained by minimizing a loss function that incorporates the governing PDE, boundary conditions, and initial conditions where applicable.

### Hybrid Finite Difference–PINNs

The HFD-PINN implementation combines:

- **Neural networks:** Approximate the unknown PDE solution.
- **Compact finite differences:** Approximate spatial derivatives using neighbouring grid values.
- **Automatic differentiation:** Calculate time derivatives and provide spatial derivative fallbacks where finite difference stencils are unavailable.
- **Signed Distance Functions:** Represent the rhombus geometry and help identify valid computational points.
- **Physics-informed loss functions:** Enforce the governing equations and the required boundary and initial conditions.

The objective is to evaluate how this hybrid formulation performs relative to conventional PINNs.

## 🛠️ Technology Stack

- **Python** — Core implementation
- **PyTorch** — Neural networks, automatic differentiation, and optimization
- **NumPy** — Numerical operations
- **Matplotlib** — Visualization of predicted solutions and errors
- **Pandas** — Organizing evaluation results
- **Jupyter Notebook** — Interactive development and experimentation

## 📊 Evaluation Metrics

The models are evaluated using:

| Metric | Purpose |
|---|---|
| Relative \(L^2\) error | Measures prediction error relative to the analytical solution |
| Mean Absolute Error (MAE) | Measures average absolute prediction error |
| Maximum Absolute Error | Measures the largest absolute error |
| Training Loss | Tracks optimization progress |
| Training Time | Measures computational cost |

The comparison considers both numerical accuracy and computational efficiency. Results are interpreted separately for the Poisson, heat, and wave equations.

## 📈 Visualizations

The project uses visualizations to investigate:

- Analytical solutions
- Neural network predictions
- Absolute error distributions
- Training loss and convergence behaviour
- Comparisons between conventional PINNs and HFD-PINNs

These visualizations help identify where the models approximate the analytical solutions accurately and where larger errors occur.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

Replace the placeholders with your actual GitHub repository URL and folder name.

### 2. Create a virtual environment

```bash
python -m venv pinn_env
```

Activate it on Windows:

```powershell
.\pinn_env\Scripts\Activate.ps1
```

### 3. Install the dependencies

```bash
python -m pip install numpy pandas matplotlib jupyter
```

Install PyTorch following the instructions for your operating system and hardware:

https://pytorch.org/get-started/locally/

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the project notebook and run the cells in order.

## 📁 Project Structure

The repository is organized around the implementation and evaluation of the PDE solvers.

```text
PINNs/
├── notebooks/
│   ├── conventional_pinns.ipynb
│   └── hfd_pinns.ipynb
├── results/
│   ├── figures/
│   └── evaluation/
├── README.md
└── requirements.txt
```

## 🔬 Research Focus

This project explores the use of physics-informed deep learning for scientific computing, particularly the numerical solution of PDEs in non-rectangular domains.

The central research question is how a hybrid approach combining compact finite difference approximations and neural networks compares with conventional PINNs in terms of solution accuracy, convergence behaviour, and computational cost.

The implementation is inspired by research on hybrid finite difference methods and physics-informed neural networks for PDEs in complex geometries.

## 🔮 Future Work

Further work within the project's scope includes:

- Refining the implementation of the hybrid numerical operators.
- Investigating convergence behaviour across the three benchmark PDEs.
- Analysing the effects of domain boundaries on finite difference approximations.
- Evaluating the accuracy and computational cost of HFD-PINNs against conventional PINNs.

## 👨‍💻 Author

**Derick Mathara Kinyanjui**

BSc Mathematics and Modelling Processes  
Dedan Kimathi University of Technology, Kenya

**Areas of interest:**  
Machine Learning · Deep Learning · Scientific Computing · Numerical Analysis · Mathematical Modelling · Physics-Informed Neural Networks

---

*This project is an ongoing exploration of the integration of numerical methods and deep learning for solving partial differential equations.*
