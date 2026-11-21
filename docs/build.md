# Build notes

Open `firmware/MDK-ARM/WUST_Frame_Two.uvprojx` in Keil µVision. The source project records ARMCC 5.06 update 5 (build 528) and Keil.STM32F4xx_DFP.2.17.1. Required in-tree source dependencies and retained referenced math libraries are included. The compiler and device pack are external environment dependencies.

The firmware directory layout is unchanged, preserving relative Keil file references. Original source encodings and line endings are preserved. Some include spellings rely on Windows case-insensitive paths. Original GCC Makefiles, where present, are historical and do not necessarily enumerate all current Keil application sources.

Before running the robot, reconcile board role, task activation, motor IDs, sensor orientation, mechanical limits, control gains, and units with the intended hardware. No firmware configuration was enabled or changed as part of this repository split.
