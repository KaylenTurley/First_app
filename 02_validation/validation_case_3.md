# Validation Case 3: Cantilever Tip Load

## Inputs

- Support type: cantilever, fixed at the left
- Span: 20 ft
- Point load: 4 kip downward at the free end (20 ft)
- Uniform load: none
- Material / section: steel W12x26
- Deflection limit: L/360

## Expected Results

- Fixed support reaction: 4 kip upward
- Fixed-end moment: -80 kip-ft
- Shear: +4 kip from the fixed end to immediately left of the tip load, then 0 at the free end
- Moment at 0, 5, 10, 15, and 20 ft: -80, -60, -40, -20, and 0 kip-ft
- Maximum deflection: approximately 3.115619 in downward at the free end
- Maximum bending stress: `80 kip-ft × 12 / 33.4 in^3 = 28.7425 ksi` — Pass for W12x26
- L/360 allowable deflection: 0.666667 in — Fail for W12x26
- Steel recommendation: W24x55, the lightest listed section passing both checks

Hand check: the tip load produces a 4 kip reaction and a fixed-end moment of `-4 kip × 20 ft`. For a cantilever with an end point load, tip deflection magnitude is `P L^3 / (3 E Ix)` using consistent inch and ksi units.

## Browser Test

Set the controls to the inputs above. Confirm the beam drawing shows a fixed support at the left, a 4 kip downward arrow at the right tip, and the fixed reaction and moment. Confirm:

- The shear plot remains at +4 kip until the tip, then returns to zero.
- The moment plot is negative (hogging), starting at -80 kip-ft at the fixed end and rising linearly to zero at the tip.
- The deflection plot is zero at the fixed end and reaches about 3.116 in downward at the tip.
- The selected W12x26 deflection check fails, and W24x55 is recommended.
