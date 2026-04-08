# Magnetic Textures via Monte Carlo Simulation

Classical spin simulations on a 2D square lattice using the extended Heisenberg Hamiltonian, reproducing four canonical magnetic ground states: ferromagnetic, antiferromagnetic, spin spiral, and skyrmion crystal phases.

This repository is part of my ongoing effort to develop computational skills in classical spin models, complementing my broader research in condensed matter / quantum materials.

---

## The Model

The total energy is:

$$E = -J \sum_{\langle i,j \rangle} \mathbf{S}_i \cdot \mathbf{S}_j + \sum_{\langle i,j \rangle} \mathbf{D}_{ij} \cdot (\mathbf{S}_i \times \mathbf{S}_j) - A \sum_i (S_{i,z})^2 - \sum_i \mathbf{H} \cdot \mathbf{S}_i$$

Each $\mathbf{S}_i$ is a classical unit vector on a 2D square lattice. The four terms are, in order: Heisenberg exchange ($J$), Dzyaloshinskii–Moriya interaction (DMI, $\mathbf{D}_{ij}$), easy-axis anisotropy ($A$), and Zeeman coupling to an external field ($\mathbf{H}$). Color maps show the out-of-plane component $S_z$; quiver arrows show the in-plane texture where relevant.

---

## Parameters

A weak easy-axis anisotropy $A_z = 0.01$ is included in all runs.

| Phase | $J$ | $D$ | $H_z$ |
|-------|-----|-----|--------|
| Ferromagnetic (FM) | +1 | — | — |
| Antiferromagnetic (AFM) | −1 | — | — |
| Spin Spiral (SS) | +1 | 1.5 | — |
| Skyrmion Crystal (SKX) | +1 | 0.7 | 0.2 |

---

## Results

![Magnetic textures: FM, AFM, spin spiral, skyrmion crystal](images/magnetic_textures.png)

*20×20 square lattice. Color: $S_z$. Arrows: in-plane $(S_x, S_y)$ components.*

**Ferromagnetic state (a):** With $J > 0$ and no competing interactions, all spins align along $-\hat{z}$. The $S_z$ map is uniform ($S_z \approx -1$), confirming the expected ground state.

**Antiferromagnetic state (b):** Negative exchange ($J < 0$) favors antiparallel neighbors, producing the Néel checkerboard — alternating $S_z = +1$ and $S_z = -1$ sites. The pattern is sharp and defect-free, consistent with a well-converged ground state.

**Spin spiral state (c):** A large DMI ($D = 1.5 > J$) overcomes the ferromagnetic exchange, forcing spins to rotate continuously. The result is a propagating helical texture with a well-defined wavelength set by the ratio $D/J$. The in-plane arrows trace the rotation of spins across the spiral fronts.

**Skyrmion crystal (d):** At moderate DMI ($D = 0.7$) with an applied field ($H_z = 0.2$), the competition between exchange, DMI, and Zeeman energy stabilizes a periodic lattice of magnetic skyrmions. Each skyrmion is a topologically non-trivial spin whirl — $S_z \approx +1$ at the core, winding to $S_z \approx -1$ in the surrounding ferromagnetic background. The applied field is essential: without it, the spiral phase persists.

The progression FM → AFM → SS → SKX illustrates how systematically tuning $J$, $D$, and $H$ drives the system through distinct topological and magnetic phases — a point directly relevant to the design of chiral magnets and spintronic materials.

---

## References

- Mühlbauer et al., *Science* 323, 915 (2009) — skyrmion lattice in a chiral magnet
- Nagaosa & Tokura, *Nature Nanotechnology* 8, 899 (2013) — topological properties of skyrmions
- Dzyaloshinsky, *J. Phys. Chem. Solids* 4, 241 (1958) — DMI theory
- Moriya, *Phys. Rev.* 120, 91 (1960) — microscopic derivation of DMI
