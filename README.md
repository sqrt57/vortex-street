# Vortex Street

Fluid simulations of air and water flow, up to an airplane in a wind tunnel, with 2D and 3D visualizations.

The project is also an experiment: how well developing mathematical simulations works with Claude Code.

The name comes from the Kármán vortex street, the alternating vortices shed behind a cylinder in a flow. It is
the classic first CFD (computational fluid dynamics) result and a natural first milestone.

## Goals

- Simulate air flow and water flow.
- Simulate an airplane (or an airfoil) in a wind tunnel.
- Visualize results in 2D and 3D: velocity, pressure, vorticity, streamlines, smoke and dye tracers.

## Regime and scope (proposal, not decided)

The Reynolds number, Re = speed × size / kinematic viscosity, sets the flow regime. Low Re is smooth and
laminar; high Re is turbulent. Flow past a cylinder, roughly:

| Re | Flow |
| --- | --- |
| < ~5 | Attached, smooth |
| ~5–47 | Two steady vortices behind the body |
| ~47–~200 | Vortex street: laminar, unsteady, periodic shedding |
| ~200 and up | 3D wake, gradually turbulent |
| ~10⁵–10⁶ and up | Turbulent boundary layer |

A real airplane flies at Re ≈ 10⁶–10⁸, fully turbulent, and resolving every eddy (DNS) is out of reach on a PC.
Options:

- **Low Re** (~100–10⁴): exact physics at toy scale, good visuals. Where most hobby and real-time solvers live.
- **LES** (large-eddy simulation): resolve big eddies, model small ones. Believable turbulence at moderate cost.
- **RANS**: time-averaged flow with a turbulence model. Engineering-standard lift and drag, but no swirling
  visuals.

Proposed path: 2D low-Re vortex street → 3D → LES for a turbulent wind tunnel.

## Open questions

- Language, platform, and rendering stack (browser/WebGPU, native, Python notebooks).
- Solver method: finite differences/volumes, lattice Boltzmann, vortex methods, SPH for free-surface water.
- Real-time interactive versus offline runs with rendered output.
- How to evaluate the Claude Code experiment: validation against known results (Strouhal number ≈ 0.2 for the
  cylinder, drag coefficients, NACA airfoil lift curves).

## Naming

Chosen: **vortex-street**. Checked 2026-11-26: `sqrt57/vortex-street` was free; other GitHub repositories with
the phrase are small student simulations of the phenomenon, no product or brand.

Other candidates considered: smoke-and-dye, smoke-wire, streakline, slipstream, eddy-lab, glass-tank,
tuft-test, pressure-paint, wind-bench, navier-bench, low-reynolds (undersells the turbulent goal),
tunnel-vision, hot-air.

## References

- [ambystomatechnologies/wind-tunnel-simulator](https://github.com/ambystomatechnologies/wind-tunnel-simulator):
  browser 2D Navier–Stokes wind tunnel with NACA airfoils and lift/drag telemetry.
