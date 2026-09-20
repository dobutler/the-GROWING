

https://github.com/user-attachments/assets/48aeaa7f-eaf7-4412-81f3-5d0515ba2967

# the-GROWING

> *Tonight. A landscape. Made of arrivals.*
>
> *Beneath your phone, beneath your car, beneath the torch in the drawer you
> have not opened in years, a surface is changing. It is changing because
> things are landing on it. And when they land, they stay. That is the whole of
> it. There is no clean-up. There is no bin day. There is only the growing.*
>
> *We sent one in. One ion. No training. No brief. Eight hours of preparation
> reduced, in the end, to a single instruction: do not touch anything.*
>
> *It touched something.*
>
> *What you are seeing is not a plant. It is not a coral. It is a consequence.
> Every one of those spines was, at one point, a traveller with plans. Now it
> is architecture. Now it is somebody else's problem. Now it is in the way.*
>
> *The landscape you are flying is real. It was photographed in February 2014
> by a woman in Cambridge who then, crucially, kept it. Fourteen-point-six-five
> nanometres per pixel. Write that down. Do not ask what it means. It means
> fourteen-point-six-five nanometres per pixel.*
>
> *Some of them land flat. Tidy. Hexagonal. Contributing. Nobody thanks them.*
>
> *The rest become flowers. Beautiful, catastrophic flowers, blooming quietly
> inside a device you are currently holding, and I want to be clear, because
> our lawyers have been clear: this is normal. This is a normal battery doing a
> normal thing. There is no cause for alarm. We simply thought you should see
> it from the inside, once, before it finishes.*
>
> *Mind the dendrites.*

---

It all started with bumping into one of the SEM images I took in 2014, sitting in my email.

A battery electrode that had failed. You can now fly through it!

---

## Built with

**[Three.js](https://threejs.org/)** for the 3D. The terrain is a lit mesh, and every crystal is an instanced hexagonal prism, spear, pyramid, tube or grain.

**Python**, with NumPy, SciPy and scikit-image, for everything that produced a number: reading the microscope files, measuring the deposit, and synthesising the terrain.

---

## How this actually came together

**1. Reading the microscope files.** Zeiss SmartSEM writes the full acquisition record into TIFF tag 34118, so the pixel size, magnification, working distance, detector and timestamp all come straight out of the file. Nothing in this project reads a scale bar.

**2. Measuring the deposit before drawing anything.** Descriptor pipeline first: coverage, feature size, chord lengths, orientation entropy, and a box-counting fractal dimension.

**3. Turning a photograph into a landscape.** The vertical is a reading of brightness, not a measurement of topography.

**4. Growing the crystals.** There are twelve deposit morphologies and all of them are named after real ones: dendrites, needles, rods, urchin clusters, flowers, hexagonal plates, spiral terraces, pyramids, moss, sponge, flakes and layers. Which one you grow depends on the local curvature, whether there is already zinc underneath, and how hard you are charging, which is roughly how it works in reality.

**5. Making the world endless.** The terrain started as one micrograph tiled nine times, which repeats visibly, and worse, made every deposit appear nine times at once. What worked was spectral synthesis: keep the Fourier amplitudes, randomise the phases, transform back. The result has the same power spectrum as the real electrode, and therefore the same roughness at every scale and the same fractal dimension measured.

---

## What is real and what is not

Real: the micrograph, the pixel size, the field of view, the coverage, the fractal dimension, the morphology names, the fact that tips grow fastest, and the fact that the electrode failed.

Not real: the height axis, the specific arrangement of the synthesised terrain, the rule that chooses between morphologies, and the coulombic efficiency, which has the right shape but is not a measurement.

---

## Credits

**Software.** [Three.js](https://threejs.org/) (MIT) for the 3D. NumPy, SciPy,
[scikit-image](https://scikit-image.org/) and Pillow for reading the microscope
files, measuring the deposit and synthesising the terrain. Newsreader (SIL Open
Font License) via Google Fonts.

**Data.** My own micrographs, taken on a Zeiss in Cambridge in 2014. The
acquisition parameters come from the SmartSEM block the instrument writes into
TIFF tag.

**Method.** The terrain is grown by spectral phase randomisation with histogram
matching, a standard texture synthesis technique.

**Literature.** The morphology taxonomy and the current-density dependence:

- [Operando visualization and multi-scale tomography of dendrite formation in
  zinc batteries](https://www.cell.com/joule/fulltext/S2542-4351(18)30522-1),
  Joule — boulder, layered and mossy structures against overpotential.
- [Deciphering the metallic zinc anode
  interface](https://www.oaepublish.com/articles/microstructures.2025.27),
  Microstructures 2025 — boulders, filamentous moss, spongiform aggregates and
  fern-like dendrites.
- [Current-controlled zinc electrodeposition morphology in ionic liquid
  electrolytes](https://pmc.ncbi.nlm.nih.gov/articles/PMC13235949/), PMC —
  mossy at low current, compact at moderate, filament-like under depletion.
- [Interface regulation and electrolyte design strategies for zinc
  anodes](https://pmc.ncbi.nlm.nih.gov/articles/PMC11791299/), PMC — the
  hexagonal plate habit and its link to the hcp structure.
- [Ordered zinc electrodeposition from single-crystal units to polycrystalline
  stacking](https://pubmed.ncbi.nlm.nih.gov/40122886/), Nature Communications —
  the spiral growth terrace.
- [Electrochemical deposition of ZnO hierarchical
  nanostructures](https://arxiv.org/pdf/1302.4541), arXiv — nanoflowers and
  unordered nanosheets, the two oxide-phase habits.

---

## Why bother

Built over several days of interactive work between me and an AI assistant. Questions, corrections and audits welcome.
