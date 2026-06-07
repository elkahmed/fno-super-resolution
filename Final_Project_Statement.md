# Final Project - PINNs, Neural Operators, and Deep Learning Methods for PDEs

## 1. Context and Objective

You must complete an applied project focused on either an engineering problem or a PDE, using at least one method covered in this course.

Learning objectives:
- Formulate a clear physical or engineering problem.
- Select an appropriate method from the course.
- Implement a numerical solution in PyTorch.
- Analyze result quality using a scientific approach.

## 2. Project Scope

Your project must fall into one of the following categories:

1. Solving an engineering problem (heat transfer, flow, diffusion, vibration, etc.).
2. Solving one or more PDEs with a course method.

Minimum dimensionality requirement:
- The core problem must be at least 2D (spatially).

Allowed methods (examples):
- PINNs (Physics-Informed Neural Networks)
- PINN variants (hard constraints, adaptive collocation, loss weighting, etc.)
- Neural Operators (FNO, GNO, and other neural operators covered in class)
- Transformer-based PDE models
- Any method explicitly taught in lectures/labs

## 3. Required Deliverables

You must submit **two deliverables**:

1. **Scientific report (maximum 10 pages)**
   - Scientific article format (IMRaD style recommended: Introduction, Methods, Results, Discussion).
   - PDF, maximum 10 pages (including references).
   - Readable figures, labeled axes, and units.

2. **Executable PyTorch code**
   - Clean, reproducible code that runs without manual intervention.
   - A main entry script (for example, `main.py`) or a notebook that runs end-to-end.
   - A `README.md` file explaining:
     - dependencies,
     - run command,
     - folder structure,
     - how to reproduce the main results.

## 4. Minimum Technical Requirements

Your code must:
- Be implemented in PyTorch.
- Target a problem that is at least 2D in space.
- Include clear hyperparameter management.
- Provide at least one quantitative comparison (for example, L2 error, L-infinity error, RMSE, runtime, etc.).
- Compare at least two configurations (for example, architecture, number of collocation points, optimization strategy, baseline vs proposed method).
- Save at least one result figure.

Your study must include:
- A clear problem definition (equation, domain, boundary and/or initial conditions).
- A description of the selected method and why it is appropriate.
- A limitations/errors section (what does not work, instabilities, computational cost, etc.).

## 5. Recommended Report Structure (10 pages)

Recommended outline:
1. Introduction (problem, motivation, contributions)
2. Mathematical formulation (PDE or physical model)
3. Method (model, loss, training strategy, implementation details)
4. Experimental protocol (data, metrics, baselines)
5. Results (quantitative + figures)
6. Discussion (critical analysis, limitations, perspectives)
7. Conclusion
8. References

## 6. Project Ideas (for inspiration)

You may build on one of these examples, or propose your own topic (to be validated by the instructor).

### Example A - 2D Lid-Driven Cavity Flow (Incompressible Navier-Stokes)
- PDE: steady incompressible Navier-Stokes equations in a square cavity.
- Question: how Reynolds number affects vortical structures and solution quality.
- Possible comparisons:
  - velocity-pressure PINN vs streamfunction-vorticity PINN,
  - no-slip BC enforcement strategies,
  - collocation distributions (uniform vs wall-focused sampling).

### Example B - Inverse Source Identification in 2D Poisson
- PDE: Poisson equation with unknown source term parameters.
- Goal: recover source parameters from sparse interior observations and boundary data.
- Possible comparisons:
  - direct PINN parameter estimation vs two-stage optimization,
  - dense vs sparse sensor layouts,
  - effect of measurement noise on recovered parameters.

### Example C - 2D Wave Equation with Mixed Initial/Boundary Conditions
- PDE: transient wave equation in 2D with mixed BCs.
- Goal: predict the spatio-temporal solution and evaluate long-time stability.
- Possible comparisons:
  - standard PINN vs curriculum-in-time training,
  - tanh vs sine/Fourier-feature encodings,
  - collocation focused near boundaries/initial time vs uniform sampling.

### Example D - 2D Poisson Equation on a Simple Geometry
- PDE: Poisson equation with a nontrivial source term.
- Goal: compare PINN to a classical method in terms of accuracy and cost.
- Extension: add extra physical constraints.

### Example E - Neural Operator for a Family of Conditions
- Goal: learn an operator mapping initial conditions/parameters to solutions.
- Typical case: diffusion or Burgers equation across multiple parameter settings.
- Evaluation: out-of-sample generalization (light OOD), comparison to a pointwise network.

### Example F - Applied Engineering Problem
- Example: 2D thermal fin optimization, 2D pollutant diffusion, plate vibration in 2D.
- Goal: solve the model and study one key engineering parameter (thickness, velocity, diffusivity, etc.).

## 7. Evaluation Criteria 

- Problem formulation and scientific rigor: 20%
- Methodological quality (model choices, protocol, metrics): 25%
- Result quality and critical analysis: 25%
- Code quality (clarity, execution, reproducibility): 20%
- Report writing and presentation quality: 10%

## 8. Validation Requirements

The project is considered valid if:
- Both deliverables are submitted (10-page max report + executable PyTorch code).
- The code runs and reproduces at least one result reported in the document.
- The report includes quantitative analysis and critical discussion.

## 9. Practical Advice

- Start simple, then add one meaningful extension.
- Validate your baseline before adding complexity.
- Log your experiments (hyperparameters, seeds, versions).
- Keep the scope controlled to ensure a complete and robust project.

## 10. Submission Guidelines

To submit:
- `project_report.pdf`
- Code archive (or Git repository) containing PyTorch code + `README.md`

Recommended naming convention:
- `Name1_Name2_PINNProject.zip` or `Name1_Name2_OperatorProject.zip`

Optional but recommended:
- A `results/` folder with automatically generated figures and tables.

---

If you are hesitating between several topics, propose 2-3 ideas (with target PDE, method, and metrics) and ask for quick validation before starting full implementation.