# CNC Router — UMass Aeronautics

Getting the Airframe Structures team off manual carbon fiber cutting.

![Status](https://img.shields.io/badge/status-modifying%20machine-orange)

## Why

Every CF sheet on our DBF aircraft was being cut by hand. Slow, inconsistent from person to person, and on a competition timeline the cut quality was starting to limit how good the parts could be. I took on finding us a better way.

## Designing one

I started by designing a router around what we needed:

- 400 × 400 mm cutting area
- Dual 2040 extrusion gantry, GT2 belt and V-wheels on X/Y, T8 lead screw on Z
- Makita RT0701CR spindle
- GRBL on an Arduino Uno with a CNC Shield V3
- MeanWell LRS-350-24 supply

Frame geometry is done in Onshape. BOM landed around $742 at [Rev 4a](design/bom-rev-4a.xlsx). I wrote a Python script to generate the drawing sheets parametrically so dimensions stayed in sync with the model instead of drifting every time I changed something.

<img src="images/cad-01.png" width="260"> <img src="images/cad-02.png" width="260"> <img src="images/cad-03.png" width="260">

Working drawings:

<img src="design/drawing-01.jpeg" width="380"> <img src="design/drawing-02.jpeg" width="380">

## Then the scope grew

The machine was no longer just for flat CF sheet. It also had to trim 3D-printed fuselage halves, cut hatches and wing sections, and handle CF-over-foam sandwich panels.

Fuselage halves are about 127 mm across. That pushed the working height requirement from 100 mm to roughly 160 mm, which my locked spec didn't cover. I added a plywood torsion box riser to the design to get the gantry up another 60–80 mm.

## Build vs. buy

Around the same time a used FoxAlien Masuter Pro came up locally for about $400, roughly half my BOM, already assembled and already cutting.

My design was better matched to what we needed. It was also going to cost more and take weeks the team didn't have before they needed parts. The Masuter Pro gets us cutting now and can be modified for the height we need.

I went with buying it. The design work is still here. Doing that work is what told me what to look for in a machine, and the modifications come straight out of it.

## First cuts

Bought, brought back, and cutting.

<p align="center">
  <img src="images/CNC-working-wood-masuterPRO.jpeg" alt="Masuter Pro cutting wood" width="500"/>
</p>

📹 [Masuter Pro running](images/MasuterPro-workinh.mp4)

## Modification 1: raising the gantry

Out of the box, the Masuter Pro doesn't have the clearance for our fuselage halves. Instead of building a riser under the whole machine, I designed new corner brackets that lift the Y beams, and everything mounted on them.

<p align="center">
  <img src="images/cnc_plate_upgrade.jpeg" alt="Stock orange corner bracket held against the taller replacement bracket" width="300"/>
</p>

### Design and test fit

1. **CAD**: new brackets designed in Onshape around the Masuter Pro's existing mounting holes.
2. **Test fit in PLA**: printed the brackets first to check hole positions and fit before cutting metal.

<p align="center">
  <img src="images/testplatesoutofpla.jpeg" alt="PLA test brackets for fit check" width="320"/>
</p>

### First attempt: plasma cutter

3. **Plasma cut** from 1/4" aluminum in the makerspace, then drilled on the drill press.

The cuts came out rough, and the brackets weren't clean enough to put on the machine.

<p align="center">
  <img src="images/plasmajetworking.jpeg" alt="Plasma cutter cutting the aluminum brackets" width="320"/>
</p>

📹 [Drilling the plasma-cut brackets](images/pressdrill.mp4)

### Second attempt: manual mill

4. **Remade on a manual mill**: cut the same brackets again from aluminum. They came out much cleaner.
5. **Installed** on the machine.

<table>
  <tr>
    <th align="center">Plasma cut (first attempt)</th>
    <th align="center">Milled (installed)</th>
  </tr>
  <tr>
    <td align="center"><img src="images/CNC_plates_after_plasma_jet.jpeg" alt="Rough plasma-cut aluminum brackets" width="360"/></td>
    <td align="center"><img src="images/New%20milled%20brackets.jpg" alt="Milled aluminum corner bracket installed on the Masuter Pro" width="360"/></td>
  </tr>
</table>

<p align="center">
  <img src="images/Router%20with%20brackets%20(more%20upgrades%20coming).jpg" alt="Masuter Pro with the new milled corner brackets installed" width="600"/>
  <br>
  <sub>The Masuter Pro with the new brackets installed. More upgrades coming.</sub>
</p>

## Where it is now

- [x] Designed a router from scratch (BOM, CAD, drawings)
- [x] Bought a used Masuter Pro instead, and documented why
- [x] First cuts
- [x] Riser brackets designed and test-fit in PLA
- [x] Plasma-cut the brackets, then remade them on a manual mill
- [x] Milled brackets installed
- [ ] Machine re-squared after the bracket install
- [ ] First CF cuts
- [ ] Dust shoe (3D printed), plus a shop vacuum with a filter to connect to it
- [ ] Spindle: switch to a cheaper 65 mm spindle (FoxAlien FA710) instead of the Makita

## In this repo

```
images/     CAD screenshots, machine photos, modification photos
design/     drawing sheets and the BOM
```

## Open questions

- Workholding for curved fuselage halves vs. flat CF sheet
- Plate nesting and stock strategy, to confirm with our advisor

*The original open items (Z plate material, Makita collet offset, V-wheel OD, pulley heights) applied to the from-scratch design and are closed now that we bought the Masuter Pro.*
