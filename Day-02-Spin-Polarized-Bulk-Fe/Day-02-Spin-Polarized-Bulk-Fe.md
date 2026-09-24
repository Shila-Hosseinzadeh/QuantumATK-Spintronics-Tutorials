\# Day 2: Spin-Polarized Bulk Fe and Geometry Optimization



\## Overview

In spintronic simulations, correctly describing ferromagnetic electrode materials is essential. Today's objective is to construct bulk ferromagnetic BCC Iron (Fe), configure spin-polarized DFT calculations, optimize the crystal geometry, and extract the magnetic moment.



\---



\## 1. Building the BCC Fe Crystal

1\. Open \*\*QuantumATK Builder\*\*.

2\. Go to `Add` -> `From Database`.

3\. Search for \*\*Iron (BCC)\*\* and add it to the Stash.

4\. Verify crystal parameters: Space group $Im\\bar{3}m$, initial experimental lattice constant $a \\approx 2.87\\ \\text{Å}$.



\---



\## 2. Setting Up the DFT Calculator in Scripter

1\. Drag the structure from Stash into \*\*Scripter\*\*.

2\. Add the \*\*New Calculator\*\* block:

&#x20;  \* \*\*Calculator Type:\*\* ATK-DFT (LCAO basis set).

&#x20;  \* \*\*Spin Configuration:\*\* `Polarized` (Collinear).

&#x20;  \* \*\*Exchange-Correlation Functional:\*\* GGA-PBE.

&#x20;  \* \*\*K-point Grid:\*\* $9 \\times 9 \\times 9$.

&#x20;  \* \*\*Initial Magnetic Moment:\*\* Set to $+2.2\\ \\mu\_B$ per Fe atom to initialize the ferromagnetic ground state.



\---



\## 3. Structural Relaxation (Geometry Optimization)

1\. Add the \*\*OptimizeGeometry\*\* block to the Scripter:

&#x20;  \* \*\*Force Tolerance:\*\* $0.02\\ \\text{eV/\\text{Å}}$.

&#x20;  \* \*\*Stress Tolerance:\*\* Enabled for cell volume and shape relaxation.

2\. Save the Python script and submit the job via \*\*Job Manager\*\*.



\---



\## 4. Results Analysis

After convergence, inspect the output `.hdf5` file on the \*\*LabFloor\*\*:

\* \*\*Optimized Lattice Parameter:\*\* Compare calculated $a$ with experimental value ($2.87\\ \\text{Å}$).

\* \*\*Total Magnetic Moment:\*\* Verify spin polarization results in $\\approx 2.2\\ \\mu\_B/\\text{atom}$, confirming ferromagnetic state.



\---



