# Project Specification

## Overview

This app helps construction management students, estimators, and field engineers evaluate a beam under point and uniform loads. It presents support reactions, shear, moment, deflection, bending-stress and deflection checks, and a lightest passing section recommendation.

## Requirements

- Let users choose simply supported or cantilever support, set the span, and define point and uniform loads with their locations.
- Let users add multiple point loads and multiple uniform loads.
- Let users select steel or lumber, a section, and a deflection limit of L/240 or L/360.
- Show a beam drawing with supports and loads, reaction forces, maximum shear, maximum moment, and maximum deflection.
- Show bending-stress and deflection checks and recommend the lightest passing section.
- Include shear, moment, and deflection diagrams.
- Support light and dark appearance modes with an accessible in-app toggle.
- Load the validation example by default: a 20 ft simply supported W12x26 steel beam with a 1 kip/ft uniform load across the full span.

## Section Property Tables

Use the following properties for deflection, bending-stress checks, and section recommendations. `E` is in ksi, `Ix` in in^4, `Sx` in in^3, `Fb` in ksi, and weight in lb/ft. `Fb` is the provided allowable bending stress for the Stage 3 check.

### Steel

| Section | Weight | Ix | Sx | E | Fb |
| --- | ---: | ---: | ---: | ---: | ---: |
| W8x10 | 10 | 30.8 | 7.81 | 29000 | 30 |
| W10x12 | 12 | 53.8 | 10.9 | 29000 | 30 |
| W12x26 | 26 | 204 | 33.4 | 29000 | 30 |
| W14x22 | 22 | 199 | 29.0 | 29000 | 30 |
| W16x26 | 26 | 301 | 38.4 | 29000 | 30 |
| W18x35 | 35 | 510 | 57.6 | 29000 | 30 |
| W21x44 | 44 | 843 | 81.6 | 29000 | 30 |
| W24x55 | 55 | 1350 | 114 | 29000 | 30 |

### Lumber

| Section | Weight | Ix | Sx | E | Fb |
| --- | ---: | ---: | ---: | ---: | ---: |
| 2x8 |  | 47.63 | 13.14 | 1600 | 0.9 |
| 2x10 |  | 98.93 | 21.39 | 1600 | 0.9 |
| 2x12 |  | 177.98 | 31.64 | 1600 | 0.9 |

For steel recommendations, choose the passing section with the lowest listed weight. For lumber, do not use weight; recommend the first section in this order that passes both checks: 2x8, 2x10, 2x12.

Stage 3 deflection uses linear-elastic Euler-Bernoulli beam theory with the entered loads. Section self-weight is not added automatically; steel weight is used only for steel recommendation ranking.

## Acceptance Criteria

- All specified inputs and outputs are represented in the interface.
- The default example is clearly identifiable; live numeric outputs and diagrams update when inputs change.
- The layout remains usable on desktop and narrow screens.
- Stage 3 section checks use the properties in the tables above and update when input values change.

## Look and Feel

- Use a professional engineering-software layout with inputs in a left sidebar and results on the right.
- Use a light background, white cards with soft shadows, a blue accent color, and a modern system font.
- Provide both light and dark themes; follow the operating-system preference initially and allow users to switch modes.
- Place the beam drawing at the top of the results area, followed by stacked shear, moment, and deflection diagrams.

## Constraints

- Keep the app as a single-file web app in the root `index.html`.
- Store supporting project files in the numbered folders described in `AGENTS.md`.

## Build Stages

1. **Mockup and layout:** Create a responsive, professional page layout that follows the Look and Feel section. Show every planned input, output, chart, diagram, and control with realistic sample values; keep calculations mocked.
2. **Inputs:** Implement support, span, point-load, uniform-load, material, section, and deflection-limit controls, including adding multiple loads, without adding calculations.
3. **Calculations:** Implement beam reactions, shear, moment, deflection, stress and deflection checks, and section selection; verify representative and boundary cases.
4. **Outputs and visuals:** Connect calculations to the beam drawing, result summaries, checks, recommendation, and shear, moment, and deflection diagrams.
5. **Validation and polish:** Validate input ranges and load locations, provide clear user feedback, and check accessibility, responsive layouts, and the acceptance criteria.
