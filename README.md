# StoneRing

## Circular Paving Calculator

**StoneRing** is a browser-based planning tool for designing circular paving rings made from wedge-shaped stones, with optional rectangular shim stones.

It helps answer the practical questions that come up before laying a circular stone ring:

- How many wedge stones are required?
- What happens if the ideal quantity is not a whole number?
- How much larger or smaller will the finished ring become when the stone count is snapped to a whole number?
- Will the inner edges of the stones leave gaps or create overlaps?
- Can alternating shim stones improve the appearance of the inner edge?
- How will different stone dimensions affect the finished ring?

StoneRing runs entirely in the browser and is contained in a single HTML file. No installation, server, framework, external JavaScript library, or build process is required.

---

## Features

### Circular wedge-stone calculation

Enter the dimensions of a wedge-shaped paving stone:

- Outer width
- Inner width
- Radial depth
- Desired inner diameter

StoneRing calculates the required number of stones and visualizes the resulting ring.

### Three solver methods

StoneRing supports three ways of resolving the fact that a calculated stone count will often not be a whole number.

#### Exact

Prioritizes the requested inner diameter.

The calculator:

- Keeps the requested wedge guide diameter
- Reports the theoretical stone quantity as a decimal
- Displays the number of complete stones that physically fit
- Visualizes the remaining gap in the outer ring

This is useful when the target diameter is more important than forming a completely closed ring from unmodified stones.

#### Larger Snap

Prioritizes a complete, continuous paving pattern.

The theoretical stone count is rounded **up** to the next whole number. StoneRing then calculates the larger resulting inner diameter.

#### Smaller Snap

Also prioritizes a complete, continuous paving pattern.

The theoretical stone count is rounded **down** to the previous whole number. StoneRing then calculates the smaller resulting inner diameter.

---

## Optional Shim Stones

StoneRing can also calculate rings that use rectangular **shim stones** between the wedge stones.

When enabled, the ring follows a complete alternating pattern:

```text
Wedge -> Shim -> Wedge -> Shim -> Wedge -> Shim -> ...
```

The number of wedge stones and shim stones is therefore equal in a snapped ring.

For shim stones, the user can specify:

- Shim width
- Shim radial depth
- Inner-edge or outer-edge alignment

The shim width is rectangular, so its inner and outer widths are equal.

### Shim alignment

If the shim depth differs from the wedge depth, StoneRing can align the shim with either edge of the wedge stones.

**Outer alignment** keeps the shim flush with the outside of the ring.

**Inner alignment** keeps the shim flush with the inside wedge guide.

The visualization shows any resulting inward or outward protrusion.

---

## Interactive Visualization

StoneRing includes a responsive SVG plan view of the calculated ring.

The visualization distinguishes:

- Wedge stones
- Shim stones
- Inner and outer ring geometry
- Exact-mode residual gaps
- Resulting clear opening
- Stone spacing and fit

The input panels also include dimension diagrams showing which physical stone measurements correspond to each parameter.

The interface adapts to desktop, tablet, and mobile screen sizes.

---

## How the Calculation Works

For a wedge-only ring, the calculator first determines the outer reference radius:

```text
outer radius = desired inner diameter / 2 + wedge radial depth
```

The circumference at that radius is:

```text
outer circumference = 2 * pi * outer radius
```

The theoretical wedge count is then:

```text
wedge count = outer circumference / wedge outer width
```

When shim stones are enabled, one repeating unit consists of one wedge and one shim:

```text
repeat width = wedge outer width + shim width
```

and:

```text
pair count = outer circumference / repeat width
```

The selected solver method determines whether that theoretical quantity is kept as a decimal or rounded up or down to a complete repeating pattern.

### Why inner width is also requested

The **outer width** controls the primary circumference calculation.

The **inner width** is used to evaluate how well the supplied wedge geometry fits the circumference at the inner guide. StoneRing reports whether the inner edges are expected to:

- Fit closely
- Leave gaps
- Overlap

Shim stones can contribute additional material at this inner edge and may reduce visible gaps.

---

## Getting Started

StoneRing does not require installation.

1. Download or clone the repository.
2. Open the StoneRing HTML file in any modern web browser.
3. Enter the dimensions of your paving stones in centimetres.
4. Select a solver method.
5. Optionally enable shim stones.
6. Adjust the dimensions and compare the resulting ring visually.

Because all CSS and JavaScript are embedded in the HTML file, the calculator also works locally without an internet connection.

---

## Input Reference

| Input | Meaning |
|---|---|
| Outer width of wedge stone | Tangential width of the wedge at the outside of the ring |
| Inner width of wedge stone | Tangential width of the wedge at the inside of the ring |
| Radial depth of wedge stone | Distance from the inner edge to the outer edge |
| Desired inner diameter | Diameter of the wedge guide used as the target ring opening |
| Solver method | Exact, Larger Snap, or Smaller Snap |
| Use shim stones | Enables alternating rectangular stones between wedges |
| Shim stone width | Tangential width of the rectangular shim |
| Shim radial depth | Radial depth of the shim |
| Shim alignment | Determines whether the shim is flush with the inner or outer wedge edge |

All dimensions are entered in **centimetres**.

---

## Design Assumptions

StoneRing is intended as a practical 2D planning aid rather than a structural or construction-engineering tool.

The current model assumes:

- Stones are represented by their plan-view dimensions
- Stone height is ignored
- Wedge stones use straight inner, outer, and side edges
- Shim stones are rectangular in plan view
- Joint thickness is not independently specified
- The outside width controls the primary circumference calculation
- Snap modes use complete stones or complete wedge-shim pairs
- Shim-enabled snapped patterns alternate continuously around the entire ring
- Real-world manufacturing tolerances, cutting tolerances, bedding movement, and installation errors are not modeled

For physical construction, measurements should always be verified on site before ordering or cutting material.

---

## Browser Compatibility

StoneRing uses standard HTML5, CSS, JavaScript, and SVG.

It should work in current versions of major modern browsers, including:

- Chrome
- Chromium-based browsers
- Firefox
- Safari
- Edge

No browser extension or additional dependency is required.

---

## Contributing

Contributions, bug reports, usability improvements, and ideas for additional paving layouts are welcome.

Useful future additions could include:

- Adjustable joint widths
- Multiple shim-placement patterns
- Mixed wedge sizes
- Material and cost estimates
- Exportable dimension plans
- Printable layouts
- Imperial unit support
- Saved presets
- Additional ring and arc layouts

When contributing calculation changes, please keep the geometry transparent and understandable so users can verify how a result was derived.

---

## License

StoneRing is free software licensed under the **GNU General Public License, version 3 (GPLv3)**.

You are free to use, study, modify, and redistribute the software under the terms of GPLv3. Modified versions that are distributed must remain available under the same license terms.

For the full license text, include a `LICENSE` file containing the GNU General Public License version 3 in the repository.
