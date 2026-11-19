# Validation Case 1: Full-Span Uniform Load

## Inputs

- Support type: simply supported
- Span: 20 ft
- Point loads: none
- Uniform load: 1 kip/ft from 0 ft to 20 ft

## Expected Results

- Left reaction: 10 kip upward
- Right reaction: 10 kip upward
- Shear at 0, 5, 10, 15, and 20 ft: 10, 5, 0, -5, and -10 kip
- Moment at 0, 5, 10, 15, and 20 ft: 0, 37.5, 50, 37.5, and 0 kip-ft
- Fixed-end moment: 0 kip-ft

Hand check: the uniform load has a 20 kip resultant at midspan. By symmetry, each support reaction is 10 kip. For position `x` in feet, `V(x) = 10 - x` kip and `M(x) = 10x - x²/2` kip-ft.

## Stage 3 Section Checks

For the selected steel W12x26 section, use `E = 29000 ksi`, `Ix = 204 in^4`, `Sx = 33.4 in^3`, and `Fb = 30 ksi`.

- Maximum deflection: 0.608519 in at 10 ft
- L/360 allowable deflection: 0.666667 in — Pass
- Maximum bending stress: `50 kip-ft × 12 / 33.4 in^3 = 17.9641 ksi` — Pass
- Steel recommendation: W14x22 at 22 lb/ft; it passes both checks and is lighter than the other passing steel sections.

## Browser Console Test

Open `index.html`, then run this in the browser developer console:

```js
const case1 = {
  supportType: "simplySupported",
  spanFt: 20,
  pointLoads: [],
  uniformLoads: [{ magnitudeKipPerFt: 1, startFt: 0, endFt: 20 }]
};
const positions = [0, 5, 10, 15, 20];
const reactions = BeamCalculations.calculateSupportReactions(case1);
const shear = BeamCalculations.calculateShearDiagramValues(case1, positions);
const moment = BeamCalculations.calculateMomentDiagramValues(case1, positions);
const section = BeamCalculations.getSectionProperties("steel", "W12x26");
const results = BeamCalculations.calculateBeamDesignResults(case1, "steel", "W12x26", 360);
console.log({ reactions, shear, moment, results });
```

The shear results include left- and right-hand values so a point load can be represented as a jump. In this case there are no point loads, so both values are equal at every position.

The page also starts with this case loaded. The beam drawing and all three response diagrams should show this case and update when an enabled input changes. The moment diagram should peak at 50 kip-ft at midspan; the shear diagram should descend linearly from 10 to -10 kip; the deflection should peak downward at midspan.
