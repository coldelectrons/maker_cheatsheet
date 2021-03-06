# 3D Printing Cheat Sheet

## Techniques

### Table of contents
* [Selective Infill](#selective-infill)
* [Clean Vertical Hole](#clean-vertical-hole)
* [Sharp Angle](#sharp-angle)
* [SCAD to STEP Conversion](#scad-to-step-conversion)
* [Sanding](#sanding)


### Selective Infill

Selective infill is a technique used to put solid infill in critical places (like around a screw hole).

Here are common parameters for applying selective infill in Fusion 360 with Slic3r Prusa Edition 1.37.1.

I found this technique in Prusa OpenScad files, thanks for sharing!

#### Horizontal (compared to heated bed)

| Parameter | Expression | Value |
|:---------:|:----------:|:-----:|
| layer_height           | 0.20mm | 0.20 |
| extrusion_width        | 0.45mm | 0.45 |
| num_perimeters         | 3 | 3 |
| perimeters_thickness   | num_perimeters * extrusion_width - 0.1 | 1.25 |

Note: I do not know why I have to add this "-0.1" in perimeters_thickness. If I do not do this in Fusion 360, then I get a too fat perimeter. Any idea is welcome :)


#### Vertical (compared to heated bed)

| Parameter | Expression | Value |
|:---------:|:----------:|:-----:|
| layer_height           | 0.20mm | 0.20 |
| num_top_bottom         | 5 | 5 |
| top_bottom_thickness   | num_top_bottom * layer_height | 1.00 |


### Clean Vertical Hole

Used to put more space on top of a vertical hole and avoid clean-up after printing

I also wrote an OpenScad lib : https://github.com/gregsaun/vertical_hole

I found this technique in Prusa OpenScad files, thanks for sharing!

![Clean Vertical Hole Diagram](img/hole_cleaning_diagram.png)

Where
* h = layer_height
* w = hole radius
* a = 45°


### Sharp Angle

When printing angles the filament take a small short-cut resulting in a rounded angle. After several tests (in PETG), I found that this geometry is doing perfectly squared angles. This is valid for angle printed perpendicularly to the bed.

![Perfect Angle Diagram](img/perfect_angle.png)

Where
* e = extrusion width
* a = angle (45° for a printed angle of 90°)


### SCAD to STEP Conversion

Tutorial to convert OpenSCAD files to STEP files using FreeCAD

https://forum.lulzbot.com/viewtopic.php?t=243



### Sanding

To get smooth surface from a 3D print

Thanks to JKSniper for this technique : https://www.thingiverse.com/thing:2307550 and https://youtu.be/0vgynnYzo08

#### Material
* Sandpaper 200, 500 and 800
* Spray filler
* Spray paint (acrylic), glossy or matt
* Bowl big enough to put your part in
* Water (in the bowl)

#### Steps
1. Sand as much as you can the edges using 200 sandpaper. Regularly put the sandpaper in water. At the end, surface should be smooth and even
1. Clean the part and dry it carefully
1. Mount the part in a way that you can spray all around
1. Spray with filler and let dry. Depending on the first sanding, apply one or more layers
1. Sand using firs 500 and then 800 sandpaper until it is smooth everywhere. Regularly put the sandpaper in water.
1. Clean, rinse carefully the part and let it dry
1. Spray the acrylic paint
