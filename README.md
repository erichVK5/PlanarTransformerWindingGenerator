# PlanarTransformerWindingGenerator
A java utility for generating obround or quadrilateral planar transformer winding footprints in either gEDA footprint or Kicad legacy module format.

The user can quickly and easily generate a helical, obround, square, or rectangular PCB winding of specified dimensions using command line options.

Users can then add suitable pins or tracks with a footprint editor or text editor to effect connections to adjacent components, and in the case of two layer coils, effect series connection with the addition of a suitable via to join the top and bottom coils.

The utility tries to calculate distributed capacitance and inductance for the inductor, as well as the resulting self resonant frequency, assuming an FR4 substrate and 35 micron (1 oz / ft^2) copper.

The utility also calculates DC resistance for 35 and 70 micron track thicknesses.

Calculations of inductance and distributed capacitance, and therefore self resonant frequency, will not be accurate for shapes other than circular or square windings, since the calculations are based ont he minor inner and outer diameters of the windings. Furthermore, coupling coefficients are not calculated for dual layer coils. 

Users will need to add suitable PCB apertures, if needed, to suit the matching transformer core.

Users can also use this utility to generate PCB inductor footprints or wireless charging footprints, although the utility's calculations are unlikely to be accurate for non-round, non-square and dual layer footprints.

Building:

download planarTransformerWindingGenerator.java to a working directory

compile it using a java compiler

	javac planarTransformerWindingGenerator.java

the resulting java class file can be used with a runtime java virtual machine implementation



Usage:

	java PlanarTransformerWindingGenerator -option value

		-k	export a kicad module, default is geda .fp file

		-n	turns per layer for the windings

		-w long	width of core in microns

		-h long	height of core in microns

		-s long	space available for windings in microns

		-g long	track gaps in microns

		-q	generate a quadrilateral rather than rounded winding

		-l long	length of segment used to approximate circular arc in microns

		-s	generate a two layer winding (that will need the addition of a via to series connect

		-h	 prints this

Example usage:

	java PlanarTransformerWindingGenerator -w 20000 -h 30000 -n 5 -s 10000 -g 300 -l 2500 -d

	generates a dual layer, 5 turn per layer, 10 turn obround winding,
	of 20mm inside width, 30 mm inside height, with a winding width of 10mm
	with 0.3mm track gap and 2.5mm segment length.


	java PlanarTransformerWindingGenerator -w 20000 -h 30000 -n 5 -s 10000 -g 300 -l 2500 -d -q -k

	generates a dual layer, 5 turn per layer, 10 turn rectangular winding,
	of 20mm inside width, 30 mm inside height, with a winding width of 10mm,
	with a 0.3mm track gap, in kicad legacy module format.


PlanarTransformerWindingGenerator.java v1.0
Copyright (C) 2015 Erich S. Heinzle, a1039181@gmail.com

    see LICENSE-gpl-v2.txt for software license
    
    This program is free software; you can redistribute it and/or
    modify it under the terms of the GNU General Public License
    as published by the Free Software Foundation; either version 2
    of the License, or (at your option) any later version.
    
    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.
    
    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

