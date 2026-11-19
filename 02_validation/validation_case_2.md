# Validation Case 2: Midspan Point Load

## Inputs

- Support type: simply supported
- Span: 20 ft
- Point load: 10 kip downward at 10 ft
- Uniform load: none
- Material / section: steel W12x26
- Deflection limit: L/360

## Expected Results

- Left reaction: 5 kip upward
- Right reaction: 5 kip upward
- Shear at 0 and 5 ft: +5 kip; immediately right of 10 ft: -5 kip; at 15 ft and immediately left of 20 ft: -5 kip
- Moment at 0, 5, 10, 15, and 20 ft: 0, 25, 50, 25, and 0 kip-ft
- Maximum deflection: approximately 0.486815 in downward at 10 ft
- Maximum bending stress: `50 kip-ft × 12 / 33.4 in^3 = 17.9641 ksi` — Pass
- L/360 allowable deflection: 0.666667 in — Pass
- Steel recommendation: W14x22

Hand check: symmetry gives 5 kip at each support. The shear diagram is constant on either side of the midspan point load and jumps down by 10 kip at the load. Moment is linear on either side and peaks at midspan.

## Browser Test

Set the controls to the inputs above. Confirm the beam drawing places one 10 kip arrow at midspan, the reaction labels show 5 kip each, and:

- The shear plot is +5 kip from the left support to the load, then -5 kip from the load to the right support, with a vertical jump at 10 ft.
- The moment plot is triangular, reaching 50 kip-ft at 10 ft.
- The deflection plot is symmetric and reaches about 0.487 in downward at 10 ft.

The diagram summaries should report maximum shear 5 kip, maximum moment 50 kip-ft, and maximum deflection 0.49 in.
