# import-dxf

__import-dxf__ v1.6 was made to handle simple DXF file importing to EAGLE. It can currently only handle flat paths well.
Polygon output and layer selection has been added, as a merger between import-dxf v.4 and dxf-import v1.5.

## Instructions

#### Converting Images to Paths
* Prepare a black and white BMP image with GIMP, or some other photo editing software
* In Inkscape open the BMP file
* Select the Bitmap object with the object select tool (*F1*)
* Path > Trace Bitmap (*Shift-Alt-B*)
* Click 'update' for preview, 'OK' to generate paths, and then close Trace Bitmap window
* Move newly generated paths and delete the Bitmap object

#### Other Image Preparations
* Type out any text that you want, Format it and such
* With the object select tool (*F1*)
* Edit > Select All in All Layers (*Ctrl-Alt-A*)
* Lock the height/width ratio
* Change height or width to 100 units (in mm or inches, this helps with changing the ratio)
* Path > Object to Path (*Shift-Ctrl-C*)
* Object > Ungroup (*Shift-Ctrl-G*) until all objects are ungrouped
* Path > Stroke to Path (*Ctrl-Alt-C*)

#### Save Current Progress
* Before modifying paths for DXF create a restore point
* File > Save As (*Shift-Ctrl-S*)
* Select format Plain SVG

#### Prepare to Save as DXF
Steps should be performed in this exact order. If there are errors when
importing in EAGLE, such as issues with invalid or overlapping polygons, 
wire segments, or incomplete images, open the previously saved file
with unmodified paths and try again. Opening a new file and retrying the
process may be more successful than undoing changes from history.
* Select all with the node path editor (*F2*, *Ctrl-A*)
* Extensions > Modify Path > Add Nodes
* Extensions > Modify Path > Flatten Beziers
* For closed loop letters and shapes O,o,D,d,etc...
  * Draw a dividing shape (such as a rectangle) through the closed shape ( O => ([)] )
  * Select both shapes
  * Path > Division (*Ctrl-/*)
  * Repeat with all closed paths
* Select all with the node path editor (*F2*, *Ctrl-A*)
* Path > Break Apart (*Shift-Ctrl-K*)
  * Uncut holes will fill in as black
  * Visually verify that all holes are properly cut
* File > Save As (*Shift-Ctrl-S*)
  * Select format Autocard DXF R14
  * Make sure LWPOLYLINE output is enabled for polygon support

#### EAGLE
* Open your .BRD file
* File > Open ULP, open the import-dxf.ulp script
* Click browse to load a DXF file
* Modify options if needed and click 'OK'
* Any errors with scaling and offset are automatically detected and solution is offered
* Verify the script looks correct and click 'Run'

## Other
Please help this project by filing an issue or pull request if there are any errata 
or improvements to be made in the documentation or associated ulp.

See the [CactusCon 2014 badge](https://github.com/erikwilson/cactuscon2014/tree/master/imgs)
for examples of DXF files generated from Inkscape for use with import-dxf.
