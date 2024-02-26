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
| **Total**         |                                       |       |          | **$185**   |

## Instructions

### 3D Printing Parts

Currently in the `cad/` subdirectory, I have included a design for an E3D V6 hotend mount. I will update this to add the Chimera mount when I have tested it. In the meantime, customize this design for your hotend.

### Building Marlin

Copy the configuration files from the *Marlin* directory into a Marlin 2.0 LTS project. Customize the `MOTHERBOARD`, then build and upload Marlin to that control board.

### Configuring PrusaSlicer

I selected PrusaSlicer for its robustness and ease of customization, however, I believe that derivatives such as SuperSlicer or OrcaSlicer will also work.
Or, if you prefer Cura, as I do for my other machines, the configuration should be easy enough to replicate.

#### Set up PrusaSlicer (Windows)

1. Install [PrusaSlicer](https://www.prusa3d.com/en/page/prusaslicer_424/).
2. Copy the PrusaSlicer folder from this repository
3. Navigate to `C:/Users/YOUR_USERNAME/AppData/Roaming` in your file explorer. You can do this easily by typing in the directory bar `%APPDATA%` and pressing <kbd>Enter</kbd>.
4. Paste the PrusaSlicer folder, and select *Replace the file in the destination* if prompted. This will install the  filament settings, print settings, and printer settings I have tuned for the Stratasys Mojo conversion.
![Replace file dialog](screenshots/replace.png)
5. Open PrusaSlicer and navigate to *Printer Settings*.
6. Ensure that Expert mode is selected by pressing the button in the top right.
7. Navigate to *General* > *Bed Shape*.
![Bed Shape dialog](screenshots/bed_shape.png)
8. Load the `Mojo Logo.png` file in this repository as the bed texture.
9. Load the `Accurate Mojo Build Plate.stl` file in this repository as the bed model.

## Notes

As I haven't yet found an easy way to control the chamber temperature from the LCD in Marlin, and the Mojo lacks a heated
build plate, this configuration currently controls the chamber through the bed, and reads the chamber temperature into the bed
thermistor.
Additionally, the brushless fan used to circulate the chamber air will likely be controlled by one of the print cooling fan headers.

**Therefore, please ensure** that the bed is set to a reasonable temperature for all fo your filament profiles **and** that
your part cooling fan speed is always set to 100% to ensure that this air continues to circulate.