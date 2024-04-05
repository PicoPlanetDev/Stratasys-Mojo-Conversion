# Stratasys Mojo Retrofit

Stratasys has ended support for their Mojo 3D printers, and you can no longer purchase parts or filament for them.
This project aims to retrofit them with off-the-shelf parts to extend their lifespan.

## Notice

I have identified an issue with the Marlin 2.0.9.7 LTS firmware that causes incompatibility with the LCD display,
and I probably shouldn't have been using LTS anyway. As such, in the coming days, I'll switch the firmware over to the 
2.1-bugfix branch, and hopefully, in the slightly further future, to 2.1.3.

## Parts

Here is an example parts list that may be used for this conversion. This assumes that you repurpose the
old printer's ATX power supply and CoreXY mechanics. Minmimal irreversible changes are made to the machine,
although that doesn't really matter at this point!

|         **Item**        |                **URL**                | **Price** | **Quantity** | **Total Cost** |
|:-----------------------:|:-------------------------------------:|:---------:|:------------:|:--------------:|
| Chimera hotend          | https://www.amazon.com/dp/B08BKMM1R7/ | $20       | 1            | $20            |
| Extruder                | https://www.amazon.com/dp/B0BZD8JMPR/ | $9        | 2            | $18            |
| Control board           | https://www.amazon.com/dp/B08PCX6TM7/ | $42       | 1            | $42            |
| Endstops                | https://www.amazon.com/dp/B07PCN6T6F/ | $11       | 1            | $11            |
| PTFE tubing             | https://www.amazon.com/dp/B01CUPV90M/ | $8        | 1            | $8             |
| Stepper motors          | https://www.amazon.com/dp/B0817TS61F/ | $38       | 1            | $38            |
| LCD display             | https://www.amazon.com/dp/B08HLSCHVL/ | $12       | 1            | $12            |
| GT2 timing belt pulleys | https://www.amazon.com/dp/B07BT6N12L  | $8        | 1            | $8             |
| 4010 fan                | https://www.amazon.com/dp/B0B1N6NSGM/ | $9        | 1            | $9             |
| **Total**               |                                       |           |              | **$166**           |

### 3D Printed Parts
Currently in the `cad/` subdirectory, I have included a design for an E3D V6 hotend mount. I will update this to add the Chimera mount when I have tested it. In the meantime, customize this design for your hotend.

## Setup

### Firmware

I tested the single extruder system on old hardware I had available. Therefore, the configuration is for a mega2560 based MKS Base board.
This configuration is for Marlin 2.0.9.7 LTS.

I'm using the MKS Eagle (basically Robin Nano with builtin drivers) for the production version, so the config files and binary reflect that.
This is based on Marlin 2.1-bugfix on 4/5/2024.

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

## Instructions

I created a guide with instructions for a novice user to prepare a model for printing on one of these converted machines.
That document is available here: [Stratasys Mojo Instructions](https://docs.google.com/document/d/1dcEKFhcxA-QaMBZmRmVCBlgQjbNByx9ydnzFRXKonwo/edit?usp=sharing)

## TODO

- [ ] Update to 2.1-bugfix
- [ ] Implement M16 in print profile to ensure that the right profile (dual vs single extruder) was used
- [ ] Figure out feasibility of ATX power supply enable / disable and standby power
- [ ] Consider MPC temperature instead of PID
- [ ] Consider S-Curve acceleration
- [ ] Consider nozzle clean
- [ ] Enable linear advance
- [ ] Consider sensorless homing