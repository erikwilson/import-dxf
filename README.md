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
* Lock the height/width ratio
* Change height to 100 (this helps with changing the ratio)
* Path > Object to Path (*Shift-Ctrl-C*)

#### Save Current Progress
* Before modifying paths for DXF create a restore point
* File > Save As (*Shift-Ctrl-S*)
* Select format Encapsulated PostScript (eps) or Plain SVG

#### Prepare to Save as DXF
* Select all with the node path editor (*F2*, *Ctrl-A*)
* Extensions > Modify Path > Add Nodes
* Extensions > Modify Path > Flatten Beziers
* For closed loop letters and shapes O,o,D,d,etc...
  * Draw a dividing shape through the closed shape ( O => ([)] )
  * Select both shapes
  * Path > Division (*Ctrl-/*)
  * Repeat with all closed paths
* Select all with the node path editor (*F2*, *Ctrl-A*)
* Path > Break Apart (*Shift-Ctrl-K*)
  * Uncut holes will fill in as black, visually verify that all holes are properly cut
* File > Save As (*Shift-Ctrl-S*)
* Select format Autocard DXF R14

#### EAGLE
* Open your .BRD file
* File > Open ULP, open the import-dxf.ulp script
* Click browse to load a DXF file
* Modify options if needed and click 'OK'
* Any errors with scaling and offset are automatically detected and solution is offered
* Verify the script looks correct and click 'Run'
