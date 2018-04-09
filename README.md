# Marlin 3D Printer Firmware
# Specialisé pour CTC Prusa I3 Pro B (GT2560 Rev A)

<img align="right" src="../../raw/1.1.x/buildroot/share/pixmaps/logo/marlin-250.png" />

## Marlin 1.1

Il s'agit d'une version spécifique à l'imprimante chinoise CTC Prusa I3 Pro B 
avec la carte GT2560 Rev A, tirée de la version 1.1.x que vous trouvez à 
[GitHub MarlinFirmware/Marlin](https://github.com/MarlinFirmware/Marlin).

[Marlin Home Page](http://marlinfw.org/) - The Marlin Documentation Project. Join us!

## Modifications appliquées

La configuration (configuration.h) est initialement tirée de 
[](https://github.com/MarlinFirmware/Marlin/Marlin/example_configurations/Geeetech/GT2560/configuration.h)
à laquelle on modifie les paramètres suivant (d'après la documentation de CTC Elec.) :

```
#define STRING_CONFIG_H_AUTHOR "(M. Sibert, CTC DIY 3D)" // Who made the changes.

#define MOTHERBOARD BOARD_GT2560_REV_A

#define CUSTOM_MACHINE_NAME "CTC DIY 3D Printer"

#define EXTRUDERS 1

#define DEFAULT_NOMINAL_FILAMENT_DIA 1.75

#define POWER_SUPPLY 0

#define TEMP_SENSOR_0 1
#define TEMP_SENSOR_1 0
#define TEMP_SENSOR_2 0
#define TEMP_SENSOR_3 0
#define TEMP_SENSOR_4 0
#define TEMP_SENSOR_BED 1

#define TEMP_RESIDENCY_TIME 10  // (seconds)
#define TEMP_HYSTERESIS 3       // (degC) range of +/- temperatures considered "close" to the target one
#define TEMP_WINDOW     1       // (degC) Window around target to start the residency timer x degC early.

#define TEMP_BED_RESIDENCY_TIME 10  // (seconds)
#define TEMP_BED_HYSTERESIS 3       // (degC) range of +/- temperatures considered "close" to the target one
#define TEMP_BED_WINDOW     1       // (degC) Window around target to start the residency timer x degC early.

#define HEATER_0_MINTEMP 5
#define HEATER_1_MINTEMP 5
#define HEATER_2_MINTEMP 5
#define HEATER_3_MINTEMP 5
#define HEATER_4_MINTEMP 5
#define BED_MINTEMP 5

#define HEATER_0_MAXTEMP 260
#define HEATER_1_MAXTEMP 260
#define HEATER_2_MAXTEMP 260
#define HEATER_3_MAXTEMP 260
#define HEATER_4_MAXTEMP 260
#define BED_MAXTEMP 150

#define PIDTEMP
#define BANG_MAX 255     // Limits current to nozzle while in bang-bang mode; 255=full current
#define PID_MAX BANG_MAX // Limits current to nozzle while PID is active (see PID_FUNCTIONAL_RANGE below); 255=full current
#define PID_K1 0.95      // Smoothing factor within the PID

  // CTC MK8 Extruder
  #define  DEFAULT_Kp 19.86
  #define  DEFAULT_Ki 1.0
  #define  DEFAULT_Kd 98.83

#define PIDTEMPBED

#define MAX_BED_POWER 255 // limits duty cycle to bed; 255=full current

  //12v (120 watt?) MK2a PCB Heatbed into 4mm borosilicate (Geeetech Prusa i3 Pro, Pro/B/C/X)
  #define  DEFAULT_bedKp 234.88
  #define  DEFAULT_bedKi 42.79
  #define  DEFAULT_bedKd 322.28

#define PREVENT_COLD_EXTRUSION
#define EXTRUDE_MINTEMP 170

#define PREVENT_LENGTHY_EXTRUDE
#define EXTRUDE_MAXLENGTH 200

#define THERMAL_PROTECTION_HOTENDS // Enable thermal protection for all extruders
#define THERMAL_PROTECTION_BED     // Enable thermal protection for the heated bed

#define USE_XMIN_PLUG
#define USE_YMIN_PLUG
#define USE_ZMIN_PLUG

#define ENDSTOPPULLUPS // Comment this out (using // at the start of the line) to disable the endstop pullup resistors

// Enable this feature if all enabled endstop pins are interrupt-capable.
// This will remove the need to poll the interrupt pins, saving many CPU cycles.
//#define ENDSTOP_INTERRUPTS_FEATURE

/**
 * Default Axis Steps Per Unit (steps/mm)
 * Override with M92
 *                                      X, Y, Z, E0 [, E1[, E2[, E3[, E4]]]]
 */
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 4020, 96 }

/**
 * Default Max Feed Rate (mm/s)
 * Override with M203
 *                                      X, Y, Z, E0 [, E1[, E2[, E3[, E4]]]]
 */
#define DEFAULT_MAX_FEEDRATE          { 500, 500, 2, 25 }

/**
 * Default Max Acceleration (change/s) change = mm/s
 * (Maximum start speed for accelerated moves)
 * Override with M201
 *                                      X, Y, Z, E0 [, E1[, E2[, E3[, E4]]]]
 */
#define DEFAULT_MAX_ACCELERATION      { 1000, 1000, 50, 1000 }

/**
 * Default Acceleration (change/s) change = mm/s
 * Override with M204
 *
 *   M204 P    Acceleration
 *   M204 R    Retract Acceleration
 *   M204 T    Travel Acceleration
 */
#define DEFAULT_ACCELERATION          1000    // X, Y, Z and E acceleration for printing moves
#define DEFAULT_RETRACT_ACCELERATION  1000    // E acceleration for retracts
#define DEFAULT_TRAVEL_ACCELERATION   3000    // X, Y, Z acceleration for travel (non printing) moves

/**
 * Default Jerk (mm/s)
 * Override with M205 X Y Z E
 *
 * "Jerk" specifies the minimum speed change that requires acceleration.
 * When changing speed and direction, if the difference is less than the
 * value set here, it may happen instantaneously.
 */
#define DEFAULT_XJERK                 20.0
#define DEFAULT_YJERK                 20.0
#define DEFAULT_ZJERK                  0.4
#define DEFAULT_EJERK                  5.0

#define EEPROM_SETTINGS   // Enable for M500 and M501 commands
//#define DISABLE_M503    // Saves ~2700 bytes of PROGMEM. Disable for release!
#define EEPROM_CHITCHAT   // Give feedback on EEPROM commands. Disable to save PROGMEM.

// Preheat Constants
#define PREHEAT_1_TEMP_HOTEND 180
#define PREHEAT_1_TEMP_BED     50
#define PREHEAT_1_FAN_SPEED     0 // Value from 0 to 255

#define PREHEAT_2_TEMP_HOTEND 240
#define PREHEAT_2_TEMP_BED    110
#define PREHEAT_2_FAN_SPEED     0 // Value from 0 to 255

#define LCD_LANGUAGE fr

#define DISPLAY_CHARSET_HD44780 WESTERN

#define ULTRA_LCD   // Character based

#define SDSUPPORT

#define SPEAKER

//#define LCD_FEEDBACK_FREQUENCY_DURATION_MS 2
//#define LCD_FEEDBACK_FREQUENCY_HZ 5000

#define REPRAP_DISCOUNT_SMART_CONTROLLER
```

## Licence (identique à l'orignale, évidemment) 

Marlin is published under the [GPL license](https://github.com/COPYING.md) 
because we believe in open development. The GPL comes with both rights and 
obligations. Whether you use Marlin firmware as the driver for your open or 
closed-source product, you must keep Marlin open, and you must provide your 
compatible Marlin source code to end users upon request. The most 
straightforward way to comply with the Marlin license is to make a fork of 
Marlin on Github, perform your modifications, and direct users to your modified 
fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) 
that are closed source or crippled by a patent, we would prefer that you choose 
another firmware or, better yet, make your own.

<!--
[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)
-->