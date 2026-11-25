# 云台-舵轮底盘机器人

## Demonstration videos

| Demonstration | Playback | Repository file |
| --- | --- | --- |
| Independent chassis motion | [Watch video](https://jiraiyamr.github.io/assets/videos/swerve/chassis-motion.mp4) | [MP4](media/videos/chassis-motion.mp4) |
| Full robot motion | [Watch video](https://jiraiyamr.github.io/assets/videos/swerve/full-robot-motion.mp4) | [MP4](media/videos/full-robot-motion.mp4) |
| Shooting | [Watch video](https://jiraiyamr.github.io/assets/videos/swerve/shooting.mp4) | [MP4](media/videos/shooting.mp4) |

[View the project on my homepage](https://jiraiyamr.github.io/#projects).

## Gimbal-equipped swerve-drive robot

Standalone robot project from Hexi Liu’s RoboMaster development portfolio. The project includes chassis and gimbal application code, robot-level command handling, and CAN-based board communication. The uploaded firmware remains an archived board/configuration snapshot.

**Platform:** STM32F407 · FreeRTOS/CMSIS-RTOS · CAN · UART · SPI  
**Project scope:** 云台-舵轮底盘机器人

## Control and integration

Four-module drive-speed decomposition, atan2 steering-angle calculation, and cascaded steering control. Gimbal source includes yaw/pitch control and CAN motor commands.

| Module | Start reading |
| --- | --- |
| Chassis kinematics and wheel-speed control | [chassis.c](firmware/Applications/chassis.c) |
| Gimbal control | [gimbal.c](firmware/Applications/gimbal.c) |
| Robot-level command handling | [robots.c](firmware/Robots/robots.c) |
| CAN board-to-board command transport | [Dual_board.c](firmware/modules/Dual_board/Dual_board.c) |
| CAN feedback and motor commands | [CAN_receive.c](firmware/modules/CAN_receive/CAN_receive.c) |
| Task creation | [freertos.c](firmware/Core/Src/freertos.c) |
| Keil project | [WUST_Frame_Two.uvprojx](firmware/MDK-ARM/WUST_Frame_Two.uvprojx) |

## Supplied configuration

Enabled: chassis, steering, and CAN board-command reception tasks, plus the generated default task. Gimbal, robot-command, and INS task creation is commented out. This snapshot is configured for a chassis/steering-side role.

Code availability and task activation are documented separately. This repository does not claim that the archived startup configuration runs every robot subsystem simultaneously.

## Build and verification

Open the Keil project with ARMCC 5.06 update 5 (build 528) and the corresponding STM32F4 device pack. See [build notes](docs/build.md) and [configuration notes](docs/configuration.md).

Run `python tools/verify_import.py` to verify that the imported firmware bytes match the source manifest. This checks packaging integrity; compilation, flashing, and hardware behavior were not revalidated during the split.

## Evidence and contributions

- [Personal contribution record](docs/contributions.md)
- [Demonstration and testing](docs/evidence.md)
- [Source provenance](docs/provenance.md)
- [Third-party notices](THIRD_PARTY_NOTICES.md)

## Related robot projects

- [云台-麦克纳姆轮底盘机器人](https://github.com/JiraiyaMr/gimbal-mecanum-robot)
- [云台-全向轮底盘机器人](https://github.com/JiraiyaMr/gimbal-omniwheel-robot)
- [云台-舵轮底盘机器人](https://github.com/JiraiyaMr/gimbal-swerve-robot)

