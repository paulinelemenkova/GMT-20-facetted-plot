# GMT Faceted Plot — Side-by-Side Gridding Comparison Figure

A GMT (Generic Mapping Tools) shell script that composes a faceted (side-by-side) figure of two map panels in a single layout, used here to compare two gridding algorithms applied to the same bathymetry data. The left panel grids the data by direct conversion (xyz2grd) and the right panel by local interpolation (nearneighbor), so the methods can be judged against each other at a glance. The example covers the Kuril-Kamchatka Trench and supports method-comparison figures in the author's marine-geophysical and cartographic publications.

## What the script does

- inspect the XYZ data range (gmtinfo) and convert the table to binary (gmt convert)
- panel a) grid the data by direct conversion (xyz2grd) and contour-map it (grdcontour, pscoast)
- shift the origin (-X) and panel b) grid the same data by nearest-neighbour interpolation (nearneighbor) and contour-map it
- add per-panel captions a) / b), a common title and the GMT logo (pstext, logo)
- export the combined figure to raster (psconvert) at high resolution

The script demonstrates GMT's manual panel layout via origin shifts (-X / -Y) with overlay (-O -K) chaining to build small-multiples figures.

## Data source

Scattered / gridded XYZ bathymetry exported from a global grid (e.g. TOPEX/UCSD). Input as an ASCII .xyz table.

## Requirements

- GMT 6.x (Generic Mapping Tools): https://www.generic-mapping-tools.org
- A POSIX shell (bash/sh)
- The XYZ point table available locally

## Usage

Place the required XYZ table in the working directory, adjust the -R region at the top of the script, then run:

    bash GMT-20-JM-2together.sh

The script writes a PostScript file and converts it to a raster image (JPG/PNG) via psconvert.

## Author and citation

Polina Lemenkova
ORCID: https://orcid.org/0000-0002-5759-1089

This script supports method-comparison figures in the author's marine-geophysical and cartographic papers; please cite the specific article a given figure appears in. The full publication list is available via the ORCID record above.

## License

See the LICENSE file in this repository.
