# Stratasys Mojo Retrofit

Stratasys has ended support for their Mojo 3D printers, and you can no longer purchase parts or filament for them.
This project aims to retrofit them with off-the-shelf parts to extend their lifespan.

## Parts

Coming soon

## Instructions

### Marlin

Copy the configuration files from the *Marlin* directory into a Marlin 2.0 LTS project. Customize the board, then build and upload Marlin to your control board.

### PrusaSlicer

I selected PrusaSlicer for its robustness and ease of customization, however, I believe that derivatives such as SuperSlicer or OrcaSlicer will also work.
Or, if you prefer Cura, as I do for my other machines, the configuration should be easy enough to copy.

Paste the PrusaSlicer folder in %APPDATA%, and replace any files it asks about. This will install the filament settings, print settings, and printer settings for the Stratasys Mojo conversion.

You may need to edit the Printer Settings > General > Bed Shape and re-load the Texture and Model for the bed to appear correctly.
