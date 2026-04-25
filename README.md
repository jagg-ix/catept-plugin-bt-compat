# catept-plugin-bt-compat

Sibling repo of [`jagg-ix/catept-main`](https://github.com/jagg-ix/catept-main).
17th plugin extracted under [Target 5](https://github.com/jagg-ix/catept-main/blob/main/docs/architecture/targets/target-4-plan.md)
(scale-out wave). **First extraction from the CAT/EPT *core* tree** (rather
than `Integration/`); a step into Wave-2 plugin-slot decoupling territory.

## What this provides

Encodes the equation-level scalar bridge of:

* M. Auci, *On the Compatibility Between Quantum and Relativistic
  Effects in an Electromagnetic Bridge Theory*, arXiv:1003.3861v1.

11 scalar definitions (BT Eqs. 1-3, 6, 14-18, 19-20; Doppler factor;
Lorentz time/space transforms; relativistic energy/momentum from
invariant scale) + 9 sanity theorems (rest-frame degeneracies) + 1
invariance theorem (Eq. 15 parametrization recovers `eps²`).

| Theorem | Statement |
|---|---|
| `btInvariantEnergySq_at_rest` | `btInvariantEnergySq E 0 c = E²` |
| `btDopplerFactor_at_rest` | `btDopplerFactor 0 θ = 1` |
| `btObservedFrequency_at_rest` | `btObservedFrequency ν₀ 0 θ = ν₀` |
| `btObservedPhotonEnergy_at_rest` | `btObservedPhotonEnergy eps 0 θ = eps/2` |
| `btPeriodPrime_at_rest` | `btPeriodPrime T λ 0 θ c = T` |
| `btWavelengthPrime_at_rest` | `btWavelengthPrime T λ 0 θ c = λ` |
| `btLorentzTime_at_rest` | `btLorentzTime t x 0 c = t` |
| `btLorentzSpace_at_rest` | `btLorentzSpace x t 0 c = x` |
| `btInvariant_from_relativistic_param` | Eq. 15 → `E² − (Pc)² = eps²` |

All proofs are elementary (`ring`, `simp`, `field_simp`, one `calc`).

## Dependencies

| Pin | Version |
|---|---|
| Lean toolchain | `leanprover/lean4:v4.29.0` |
| Mathlib | `8a178386ffc0f5fef0b77738bb5449d50efeea95` |

No internal CATEPTMain.* deps in the upstream — pure Mathlib.

## Re-import contract

```lean
require «catept-plugin-bt-compat» from git
  "https://github.com/jagg-ix/catept-plugin-bt-compat.git" @ "<sha>"
```

```lean
import CATEPTPluginBTCompat.IntegrationBridge

open CATEPTPluginBTCompat (
  btTotalEnergy btTotalMomentum
  btInvariantEnergySq btPhotonEnergyEq6
  btDopplerFactor btObservedFrequency btObservedPhotonEnergy
  btPeriodPrime btWavelengthPrime
  btLorentzTime btLorentzSpace
  btRelativisticEnergy btRelativisticMomentumTimesC
  btInvariantEnergySq_at_rest
  btDopplerFactor_at_rest btObservedFrequency_at_rest
  btObservedPhotonEnergy_at_rest btPeriodPrime_at_rest
  btWavelengthPrime_at_rest btLorentzTime_at_rest
  btLorentzSpace_at_rest btInvariant_from_relativistic_param)
```

## Build locally

```bash
lake exe cache get
lake build
```

## License

MIT, matching `catept-main`.
