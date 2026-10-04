# What Temperature Really Is, Interactively

An interactive, single-page web demo of the statistical definition of temperature, 1/T = (∂S/∂U)<sub>N,V</sub>: how it follows from maximizing entropy, how it recovers the equipartition results, how entropy relates to heat, and how a two-state paramagnet reaches infinite and even negative temperatures.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 3, Interactions and Implications, Sections 3.1 to 3.3). It follows the demos for Chapter 2 (microstates and macrostates; large systems and entropy).

## What's inside

**Temperature from entropy.** The entropies S<sub>A</sub>, S<sub>B</sub>, and S<sub>total</sub> of two Einstein solids (300 and 200 oscillators sharing 100 units), with tangent lines at any division of the energy. The slopes give k<sub>B</sub>T/ε for each solid by centered differences (0.31 and 0.85 at q<sub>A</sub> = 12), the page says which way energy flows, and a button lets the energy flow step by step up the total entropy to equilibrium at q<sub>A</sub> = 60. The textbook's "normal, miserly, and enlightened" analogy is sketched, with the instability of Problem 3.4.

**Putting the definition to work.** U = Nk<sub>B</sub>T for an Einstein solid with q ≫ N, U = (3/2)Nk<sub>B</sub>T for a monatomic ideal gas, and U = Nε e<sup>−ε/k<sub>B</sub>T</sup> in the quantum limit (Problem 3.5). A chart of the energy and the heat capacity, computed from the exact multiplicity of a large Einstein solid, joins the two limits.

**Entropy and heat.** dS = Q/T and ΔS = ∫(C<sub>V</sub>/T) dT, the third law, and Clausius's definition. Calculators for heating water (200 g from 20 °C to 100 °C gains about 200 J/K, multiplying the multiplicity by e<sup>1.5 × 10<sup>25</sup></sup>) and for the entropy bookkeeping of heat flowing between two objects (1500 J from 500 K to 300 K: −3, +5, and +2 J/K), with a verdict on whether the flow can happen spontaneously. Landauer's principle (Problem 3.16): the minimum heat to erase anything from a byte to a terabyte.

**Paramagnetism and negative temperature.** A 100-dipole two-state paramagnet worked out numerically as in the lecture's table (Ω, S/k<sub>B</sub>, k<sub>B</sub>T/μB, C/Nk<sub>B</sub>), with the S(U) curve, its tangent, and the dipoles drawn for any number pointing up, through infinite temperature to negative temperatures. Four analytic charts share the same state: k<sub>B</sub>T/μB against U/NμB, the magnetization M = Nμ tanh(μB/k<sub>B</sub>T) including T < 0, the heat capacity C<sub>B</sub> and energy, and the entropy S = Nk<sub>B</sub>[ln(2 cosh x) − x tanh x] (Problem 3.23). Curie's law, M ≈ Nμ²B/k<sub>B</sub>T, is compared with the exact tanh for electron and nuclear dipoles at any field and temperature.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- Entropies are computed exactly from logarithms of factorials. Temperatures and heat capacities in the Einstein-solid and paramagnet examples use centered differences, as in the lecture's tables, and reproduce them (for example k<sub>B</sub>T/μB = 0.47, 0.54, 0.60 and C/Nk<sub>B</sub> = 0.074, 0.310, 0.365 for 99, 98, 97 dipoles up).
- The lecture's k<sub>B</sub>T<sub>B</sub>/ε = 0.83 at q<sub>A</sub> = 12 comes from the table's rounded entropies; the exact value is 0.85. Its 2.3 × 10<sup>−11</sup> J for erasing a gigabyte uses 8 × 10<sup>9</sup> bits; a gigabyte of 2<sup>30</sup> bytes gives 2.5 × 10<sup>−11</sup> J.
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.
- Constants used: k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K = 8.617 × 10<sup>−5</sup> eV/K, μ<sub>B</sub> = 5.788 × 10<sup>−5</sup> eV/T.

## Caveats

- The nuclear option in the Curie's-law calculator uses the nuclear magneton (μ<sub>B</sub>/1836) as a representative scale; real nuclear moments differ by factors of order one.
- The analytic paramagnet charts use the large-N formulas; the 100-dipole explorer above them is exact.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Sections 3.1 to 3.3 and Problems 3.4, 3.5, 3.16, 3.19, and 3.23).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
