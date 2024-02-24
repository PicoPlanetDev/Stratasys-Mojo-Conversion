# Stratasys Mojo Retrofit

Stratasys has ended support for their Mojo 3D printers, and you can no longer purchase parts or filament for them.
This project aims to retrofit them with off-the-shelf parts to extend their lifespan.

## Parts

Here is an example parts list that may be used for this conversion. This assumes that you repurpose the
old printer's ATX power supply, chamber heaters, chamber thermistor, and CoreXY mechanics.

| Item              | URL                                   | Price | Quantity | Total Cost |
|-------------------|---------------------------------------|-------|----------|------------|
| Chimera hotend    | https://www.amazon.com/dp/B08BKMM1R7/ | $20   | 1        | $20        |
| Extruder          | https://www.amazon.com/dp/B07WHYBVJ5/ | $10   | 2        | $20        |
| Control board     | https://www.amazon.com/dp/B08PCX6TM7/ | $42   | 1        | $42        |
| Endstops          | https://www.amazon.com/dp/B07PCN6T6F/ | $11   | 1        | $11        |
| PTFE tubing       | https://www.amazon.com/dp/B07XYJZ17Z/ | $15   | 1        | $15        |
| Stepper motors    | https://www.amazon.com/dp/B07KW7F3P9/ | $43   | 1        | $43        |
| MOSFETs           | https://www.amazon.com/dp/B0CCP24G5J/ | $9    | 1        | $9         |
| ESC               | https://www.amazon.com/dp/B0863HZN9L/ | $13   | 1        | $13        |
| Display           | https://www.amazon.com/dp/B08HLSCHVL/ | $12   | 1        | $12        |
| SD card extension | https://www.amazon.com/dp/B07H31Y518/ | $11   | 1        | $11        |
| **Total**         |                                       |       |          | **$196**   |

## Instructions

### Marlin

Copy the configuration files from the *Marlin* directory into a Marlin 2.0 LTS project. Customize the board, then build and upload Marlin to your control board.

### PrusaSlicer

I selected PrusaSlicer for its robustness and ease of customization, however, I believe that derivatives such as SuperSlicer or OrcaSlicer will also work.
Or, if you prefer Cura, as I do for my other machines, the configuration should be easy enough to copy.

Paste the PrusaSlicer folder in %APPDATA%, and replace any files it asks about. This will install the filament settings, print settings, and printer settings for the Stratasys Mojo conversion.

You may need to edit the Printer Settings > General > Bed Shape and re-load the Texture and Model for the bed to appear correctly.
