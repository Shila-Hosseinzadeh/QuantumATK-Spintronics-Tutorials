\# QuantumATK Calculator Parameters: Basic \& Algorithm Settings for Bulk Fe



\## Overview

This document provides a detailed breakdown of the physical and numerical rationale behind configuring the \*\*ATK-DFT\*\* calculator in QuantumATK for spin-polarized bulk $\\alpha$-Fe (BCC Iron).



\---



\## 1. Calculator Selection

\* \*\*Method:\*\* `ATK-DFT` (LCAO basis)

\* \*\*Rationale:\*\* Density Functional Theory (DFT) combined with Linear Combination of Atomic Orbitals (LCAO) provides the exact electronic structure resolution required for subsequent Non-Equilibrium Green's Function (NEGF) transport simulations.



\---

<img width="733" height="611" alt="Screenshot 2026-09-24 161830" src="https://github.com/user-attachments/assets/748c0508-7f5a-40b6-a3c2-bac3e68e115b" />




\## 2. Basic Settings Parameters



| Parameter | Value | Physical \& Numerical Rationale |

| :--- | :--- | :--- |

| \*\*Electron Temperature\*\* | `300 K` | Introduces thermal Fermi-Dirac broadening at room temperature. This prevents discontinuity in electron occupancy at the Fermi level ($E\_F$), ensuring reliable SCF convergence for metallic systems. |

| \*\*Density Mesh Cut-off\*\* | `75 Hartree` | Defines real-space grid resolution for electrostatic potential integration. A value of $75\\text{ Hartree}$ balances numerical precision and computational speed for SG15 norm-conserving pseudopotentials. |

| \*\*Charge\*\* | `0` | Represents an electrically neutral bulk crystal unit cell. |

| \*\*Exchange Correlation\*\* | `SGGA (PBE)` | Spin-polarized Generalized Gradient Approximation with Perdew-Burke-Ernzerhof functional. Correctly accounts for non-uniform electron density gradients and exchange interaction in ferromagnetic systems. |

| \*\*Spin Configuration\*\* | `Polarized` | Enforces independent Kohn-Sham equations for majority ($\\uparrow$) and minority ($\\downarrow$) spin channels, capturing the intrinsic ferromagnetic state of Fe. |

| \*\*k-point Sampling\*\* | `9 × 9 × 9` | High k-point density required for metals with complex Fermi surfaces. The odd dimension ($9$) explicitly includes the \*\*Gamma point ($\\Gamma$)\*\* at $k = (0,0,0)$, which is critical for resolving the $\\Delta\_1$ symmetry channel in Fe. |



\---

<img width="737" height="346" alt="Screenshot 2026-09-24 164658" src="https://github.com/user-attachments/assets/63afab39-ed8c-4966-9cbd-51de5f7fc9b9" />


\## 3. Algorithm Parameters



| Parameter | Value | Physical \& Numerical Rationale |

| :--- | :--- | :--- |

| \*\*Eigenvalue Solver\*\* | `DiagonalizationSolver` | Solves $H \\psi = E \\psi$ via direct matrix diagonalization. Provides exact eigenvalues and maximum numerical stability for small to medium bulk unit cells. |

| \*\*Store Grids\*\* | `Enabled` | Retains real-space potential and density grids in system RAM across SCF iterations to accelerate execution. |

| \*\*Store Basis on Grid\*\* | `Automatic` | Dynamically optimizes RAM usage and performance when mapping atomic basis functions onto the real-space grid. |

| \*\*Store Energy Density Matrix\*\* | `Disabled` | Saves memory footprint, as local energy density evaluation is not required for standard SCF ground-state calculations. |

| \*\*SCF Restart Step Length\*\*| `0.1 Å` | Extrapolates electron density during structural relaxation step displacements under $0.1\\text{ \\AA}$, significantly speeding up geometry optimization. |



\---



