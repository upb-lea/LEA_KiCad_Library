
# Set environment variable for 3D models:
In the main menu, first select "Preferences" and then "Configure Path".
Replace the environment variable `MODEL_3D` with the current location of the 3D-models, e.g. `/path/LEA_KiCad_Library/LEA_3D_Models`. This should be the 3D-models for the `LEA_KiCad_Library` repository.

Note: if you are using KiCAD6, and there is a variable `KICAD6_3DMODEL_DIR`, ignore this variable and add `MODEL_3D` as mentioned above.
![](documentation/figures/3d_model_path_preferences.png)

# Adding components
Add the new components on a separate branch. Each symbol should have the keys `Manufacturer`, `manf#` (manufacturer order number) and `mouser#` (mouser order number). Link the footprint and the 3D model. Create a pull request afterwards.

# BOM generation
The component library is aligned to use the add-on [Kicost](https://github.com/hildogjr/KiCost). Therefore the above mentioned keys `Manufacturer`, `manf#` and `mouser#` are mandatory in the symbol. Install kicost, navigate via terminal to your kicad project folder and enter `kicost` to your terminal. After that, the BOM will be created. To get the prices and stock information from Mouser, create a Mouser API key on the Mouser homepage and enter it into the [config file](https://hildogjr.github.io/KiCost/docs/_build/singlehtml/index.html#configuration-file). 

# Type labels
For a better findability and sorting of the many components, it is necessary to use a type code. Some examples are given here.
## SMD resistors
Differences:
 * Type: `SMD` / `THT`
 * Values: `_100R` / `__4R7` / `0R001`
 * Size: `0603` / `0704` / `0403`
 * Technology: Thinfilm `_THIN` / Thickfilm `THICK`
 * `HINT`: e.g. `SHUNT`
 * Derivation in percent: `_1P` / `_5P` / `10P` / `20P`
 * Voltag: `75V` / `100V`

Examples:
 * `R_0805_100R__THIN_20P_150V`
 * `R_0603_100R__THIN__1P__75V`
 * `R_0403__4R7_THICK_10P__50V`


## THT resistors
 Differences:
 * Values: `_100R` / `__4R7` / `0R001`
 * Size: `0603` / `0704` / `0403`
 * Derivation: `_1P` / `_5P` / `10P` / `20P`
 * RM: `_RM5` / `RM10` / `RM12`
 * `HINT`: e.g. `SHUNT`

 Examples:
 * `R_THT_0704__RM5_10P____1k`
 * `R_THT_0704_RM10__1P_0R001_SHUNT`

## Capacitors
 * Type: `SMD` / `THT`
 * Values: `100u` / `4u7` / `10n`
 * Size: `0603` / `0704` / `0403`
 * Voltage: `25V` / `100V` / `600V`

Examples:
 * `C_SMD_0603_100V__1u0`
 * `C_SMD_0805__25V__10u`
 * `C_SMD_1206__16V__4u7`

## Diodes
 * Start with `D_`
 * Housing: `0603` / `0704` / `0403` / `SOD` / `DFN` / `SMB` / ...
 * Current capability: `1A0` / `0A125` / ...
 * last key: exact type, e.g. `B140HW-7` / `TS4448_RGG` / ...
Examples:
 * `D_0603_0A125_TS4448_RGG`
 * `D_SOD_1A0_B140HW-7`

## Drivers
Hard to find general rules.
* Channels: `Single`/ `Dual`

Examples:
 * Driver_Dual_TI_value
 * Driver_Single_TI_value
 * Driver_Single_TI_value

## Microcontrollers
Examples:
 * `uC_FPGA_`
 
 
## Logic ICs


## Schmitt-trigger
Examples:
 * `ST_6CH_CMOS_SOIC14_MC74HC14ADG`


