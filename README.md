# reaction-tube-propulsion

**Zero-reaction-mass photon propulsion: a mathematical framework for fusion-powered, closed-mass spacecraft thrust via stimulated emission and phononic thermal management.**

---

## Overview

The Tsiolkovsky equation has a well-known pathology for interstellar missions: propellant mass grows exponentially with delta-v, and for relativistic targets no finite propellant fraction is sufficient. Every high-specific-impulse system ever proposed â€” ion drives, solar sails, nuclear pulse â€” either defers this problem or softens it. None eliminates it.

The only clean escape is a propulsion system that consumes no reaction mass at all: a photon rocket, in which momentum is carried entirely by radiation. The physics is straightforward. Thrust equals emitted power divided by $c$. What is not straightforward is achieving useful thrust from any power source a spacecraft could carry, because the thrust-to-power ratio of a photon rocket is 3.3 nanoNewtons per watt â€” the lowest of any propulsion concept, and a direct consequence of the speed of light appearing in the denominator.

This project accepts that penalty in full and asks instead: given that penalty, how efficiently can we convert fusion energy into directed radiation, with zero propellant expenditure, in a closed spacecraft?

---

## The machinery and its purpose

The system consists of a fusion reactor, a recirculating projectile loop, a phase-change fluid, and a photon collimation section. All solid and fluid mass remains permanently aboard. The only thing that exits is radiation.

The projectile loop and the phase-change fluid are not thrust generators. Every internal force pair cancels identically â€” Newton's third law is not negotiable. Their purpose is energy conversion: to excite the working fluid in a manner that maximises the fraction of fusion power emitted as directed, thrust-producing photons. The sole thrust equation is:

$$F_{\mathrm{net}} = \frac{C_{\mathrm{rad}}}{c} \left[ P_{\mathrm{in}} - (1 - \eta_{\mathrm{rec}}) \, \dot{m}_{\mathrm{phase}} \, \Delta H \right]$$

where:
- $C_{\mathrm{rad}}$ is the photon collimation efficiency
- $\eta_{\mathrm{rec}}$ is the fraction of condensation energy recovered and returned to the power budget
- $\dot{m}_{\mathrm{phase}} \, \Delta H$ is the irreducible thermal loss to the working fluid cycle

---

## The collimation ceiling â€” and two very different ways to hit it

$C_{\mathrm{rad}}$ is the key constraining parameter, and it has two fundamentally different ceilings depending on the emission physics.

### Thermal emission â€” Ã©tendue limited

For thermal emission, Ã©tendue conservation â€” the optical analogue of Liouville's theorem â€” is absolute. No passive optical system can increase the brightness of a thermal source. A hot fluid radiating isotropically into a hemisphere, redirected by the best physically realisable parabolic mirror, yields at most:

$$C_{\mathrm{rad}}^{\mathrm{thermal}} \approx 0.25 \text{ -- } 0.38$$

This is not an engineering limitation. It cannot be improved with better optics. It is a consequence of the source having finite spatial extent, and it holds for any temperature.

### Stimulated emission â€” diffraction limited

For stimulated emission the situation is categorically different. Coherent, phase-locked photons are emitted in a single direction and their divergence is set by diffraction from the aperture â€” not by source extent. The Ã©tendue constraint does not apply. In principle:

$$C_{\mathrm{rad}}^{\mathrm{stimulated}} \to 1$$

The factor-of-2.6 difference between these two ceilings is the reason the projectile subsystem either earns its place in this design or becomes superfluous. If projectile impact at the fluid interface can generate a population inversion â€” via shock excitation, collisional energy-level selectivity, or optical pumping through an impact luminescence flash â€” then the mechanical subsystem is the most compact optical pump ever proposed for a spacecraft.

---

## Fluid selection and thermodynamic recovery

The phase-change losses are not simply a cost to be minimised in isolation. When the vapour recondenses, the latent heat $\Delta H$ is released and is partially recoverable. A Carnot-bounded recovery device operating between the condensation temperature $T_H$ and the spacecraft radiator at $T_C$ achieves:

$$\eta_{\mathrm{rec}} = \epsilon \left(1 - \frac{T_C}{T_H}\right)$$

where $\epsilon$ is the second-law efficiency of the recovery device. This pushes the optimal fluid selection toward the highest boiling point the structural materials can sustain, because the Carnot ceiling rises monotonically with $T_H$.

Among accessible working fluids, **caesium at 944 K** emerges as a strong candidate:

| Property | Value |
|---|---|
| Boiling point | 944 K |
| Specific enthalpy of vaporisation $\Delta H$ | 537 kJ kgâ»Â¹ |
| Carnot efficiency vs. 100 K radiator | 0.89 |
| Practical $\eta_{\mathrm{rec}}$ range | 0.22 â€“ 0.36 |

---

## From a single tube to an array â€” the scaling problem

A fusion-powered tube at practical power densities is physically large. The natural response is parallelisation. But a packed array introduces two dissipation channels absent from a single tube.

### Channel 1: inter-tube radiative cross-coupling

At 944 K each tube irradiates its neighbours. The cross-radiation loading factor $\Lambda$ â€” absorbed neighbour power relative to self-generated power â€” is:

$$\Lambda = \frac{n_{\mathrm{nbr}} \, F \, \varepsilon_{\mathrm{outer}} \, \sigma T_H^4 \cdot 2\pi r_o \, l}{P_{\mathrm{tube}}}$$

For a hexagonally packed array with uncoated metal surfaces ($\varepsilon \approx 0.8$), $\Lambda \approx 0.38$ at 100 kW per tube and exceeds unity below roughly 25 kW per tube. Interior tubes enter a thermally coupled regime in which operating points are no longer independent.

### Channel 2: electronic thermal conductivity

Liquid caesium conducts heat predominantly through electrons, not phonons. The Wiedemannâ€“Franz contribution accounts for approximately 95% of total thermal conductance at the Csâ€“wall interface. Phononic crystal (PnC) wall engineering addresses the remaining 5%.

### Thermal management priority stack

| Priority | Channel | Intervention | Leverage |
|---|---|---|---|
| 1 | Cross-radiation | Low-$\varepsilon$ outer coating (W, Mo) | 20Ã— reduction in $\Lambda$ |
| 2 | Cross-radiation | Inter-tube radiation shields | 40Ã— reduction in $F_{ij}$ |
| 3 | Electronic conduction | Resistive interlayer at Csâ€“wall | Suppresses $\kappa_e$ |
| 4 | Phononic conduction | PnC wall engineering | Suppresses $\kappa_{\mathrm{ph}}$ only |

A PnC wall with a high-emissivity outer surface is measurably worse than a plain metal wall with a polished low-emissivity coating.

---

## The central open question

The thermodynamics of the recovery cycle, the fluid selection, and the array scaling constraints are all tractable â€” the equations are written down and the parameter space is bounded.

What is not settled is whether projectile impact on a liquid caesium interface can produce a population inversion.

If it can, via shock excitation or collisional selectivity, this concept crosses from a well-characterised photon rocket with $C_{\mathrm{rad}} \leq 0.38$ into a coherent-emission device where $C_{\mathrm{rad}} \to 1$ and the thrust budget improves by a factor of 2.6 at identical input power. The machinery that looked like an elaborate way to heat a fluid turns out to be a laser pump. That transition, if achievable, changes the engineering case for the entire system.

---

## Repository contents

| File | Description |
|---|---|
| `reaction_tube_v2.pdf` | Full mathematical framework (14 pages) |
| `reaction_tube_v2.tex` | LaTeX source |
| `pnc_paper.pdf` | PnC efficiency multiplier model |
| `pnc_paper.tex` | LaTeX source |
| `opening_statement.pdf` | Conference presentation statement |
| `opening_statement.tex` | LaTeX source |

---

## Status

Theoretical framework â€” v2.1, March 2026. All mass-conservation corrections applied. Recondensation energy treated as partially recoverable. $F_{\mathrm{proj}}$ internal thrust term removed. Array scaling analysis complete.

**Primary open question:** experimental verification of projectile-driven population inversion in liquid caesium.
