# ArmDojo Duck

Build notes and a parts list for a **Microduck-style biped duck robot on 15 Feetech HD-1910-C001 serial bus servos**. The two community HD-1910 builds, microduck-replica and XGO-Duck, share the servos, the servo IDs and the bearings. This repository collects what they have in common, our servo setup checklist and, coming next, printed parts designed by ArmDojo.

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](LICENSE)
[![Get the parts](https://img.shields.io/badge/Get%20the%20parts-armdojo.com-1F5FBF)](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899680592111&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck)
[![Discord](https://img.shields.io/badge/Discord-join%20the%20community-5865F2?logo=discord&logoColor=white)](https://discord.gg/MdyRuJVFAm)

**🛒 The 15 HD-1910 servos, the FE-URT-2 board for setting their IDs, the bearings, screws and spare leads ship from Singapore with tracking: [get the complete duck set at armdojo.com](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899680592111&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck).**

**💬 Questions, build help and show-and-tell: [join our Discord](https://discord.gg/MdyRuJVFAm).**

**🔢 All 15 servos come as ID 1. Number them in your browser with the FE-URT-2, nothing to install: [free ArmDojo Servo ID Tool](https://armdojo.com/pages/servo-id-tool?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) ([source](https://github.com/armdojo/servo-id-tool)).**

## At a glance

- **Servos:** 15 × Feetech HD-1910-C001: five per leg, four in the neck and head, one for the beak. Each servo ships with its own 2.0 mm 3-pin lead.
- **Servo IDs:** 10–14, 20–24 and 30–34. In microduck-replica, 10–14 is the right leg, 20–24 the left leg and 30–34 the neck, head and beak.
- **Power:** a 2S pack. It reads 8.4 V when full, the top of the HD-1910's 4–8.4 V range, so never use a 3S pack.
- **Setup voltage:** 7.3 V from an adjustable supply while you set the IDs.
- **Bearings:** 11 × 16 × 22 × 4 mm, plus 3 × 10 × 15 × 3 mm for microduck-replica or 2 for XGO-Duck.
- **Brain:** a Radxa Zero 3W for microduck-replica, or an Arduino UNO Q for XGO-Duck.

Choose your build before you buy anything except the servos. The controller, battery and printed parts do not carry over from one build to the other.

## Parts for one duck

| Part | Qty | Notes | Get it |
|---|---|---|---|
| Feetech HD-1910-C001 servo | 15 | Leads included | [Complete duck set: 15 servos + FE-URT-2](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899680592111&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), [15 servos only](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899658670319&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), [5-servo spares pack](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899658703087&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Feetech FE-URT-2 USB debug board | 1 | Sets the servo IDs; included in the complete duck set | [FE-URT-2](https://armdojo.com/products/feetech-fe-urt-2-usb-ttl-rs485-servo-debug-board?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Adjustable 3–12 V 5 A power supply | 1 | Set it to 7.3 V for setup; a DC jack lead is included | [Servo power supply](https://armdojo.com/products/servo-power-adapter-7-4v-8-4v-3a-dc-5-5x2-1?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Bearings and screws | 1 pack | 11 × 16 × 22 × 4 mm and 3 × 10 × 15 × 3 mm bearings, M2 and M2.5 self-tapping screws | [Bearing and screw pack](https://armdojo.com/products/microduck-bearing-screw-pack-hd-1910-duck?variant=51277756399855&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), [single bearings](https://armdojo.com/products/microduck-bearing-screw-pack-hd-1910-duck?variant=51306947379439&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| M2 × 6 mm countersunk self-tapping screws | 200 | XGO-Duck only | [100-pack](https://armdojo.com/products/microduck-bearing-screw-pack-hd-1910-duck?variant=51306947444975&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) × 2 |
| Spare 2.0 mm 3-pin servo leads | as needed | AMP 2.0, 15 cm | [Single, 5-pack or 15-pack](https://armdojo.com/products/hd-1910-amp-2-0-3-pin-servo-cable-15cm?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Servo bus and IMU board, microduck-replica | 1 | For a Radxa Zero 3W: a HAT with an on-board IMU, or an IMU board on the servo bus | [Controller HAT](https://armdojo.com/products/microduck-controller-hat-radxa-zero-3w?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), [IMU servo-bus board](https://armdojo.com/products/microduck-imu-servo-bus-board-lsm6dsv16x?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Servo bus and IMU board, XGO-Duck | 1 | Sits on the Arduino UNO Q, QMI8658A 6-axis IMU | [XGO-Duck driver board V1.1](https://armdojo.com/products/xgo-duck-driver-board-arduino-uno-q-v1-1?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Head sensors, microduck-replica | 1 + 1 | 8 × 8-zone time-of-flight module and a 160° IMX219 camera | [VL53L5CX ToF module](https://armdojo.com/products/vl53l5cx-multizone-tof-sensor-module-8x8?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), [IMX219 160° camera](https://armdojo.com/products/imx219-160-wide-angle-csi-camera-module-8mp?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Head speaker | 1 | MAX98357A I2S amplifier, 8 Ω 2 W speaker and power lead | [Duck head audio kit](https://armdojo.com/products/duck-head-audio-kit-max98357a-i2s-amplifier-speaker?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |
| Finishing tools | 1 kit | Support pliers, flush cutters, deburring knife | [Finishing tool kit](https://armdojo.com/products/3d-printer-tool-kit-support-removal-pliers?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) |

Not in the table: the controller itself (Radxa Zero 3W with a microSD card, or Arduino UNO Q), the 2S battery and its charger, the heat-set inserts for microduck-replica, XGO-Duck's 4 × M3 × 16 screws, and PLA and TPU filament. Both projects keep changing their bills of materials, so check the current one before you order.

The full comparison of both builds, part by part, is in our guide: [Microduck replica BOM with Feetech HD-1910 servos](https://armdojo.com/blogs/guides/microduck-replica-bom-feetech-hd-1910-servos?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck).

## Set up the servos before assembly

Every HD-1910 leaves the factory as ID 1 at 1,000,000 baud, so give each servo its ID on its own, before anything is screwed into a printed part.

1. Set the supply to **7.3 V** on its display before you connect anything.
2. Wire the supply to the FE-URT-2: red to **V1**, black to **G**. The G / V2 pair is for RS485 servos and stays empty.
3. Plug in **one** servo, connect the board over USB, and give the servo its joint ID (10–14, 20–24, 30–34).
4. Centre the servo, write the ID on it, then do the next one.

**Fastest way:** the free [ArmDojo Servo ID Tool](https://armdojo.com/pages/servo-id-tool?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) does step 3 from Chrome or Edge on any computer. Set *Start at ID* 10 and *Last ID* 14 for the right leg, press *Start numbering* and plug in one servo at a time; then do 20–24 and 30–34. The tool shows the HD-1910 by its model number.

The step-by-step version, with the Feetech FD screens and an ID map, is in [`docs/servo-setup.md`](docs/servo-setup.md).

## Mistakes that stop a build

- **Throwing away the leads.** Each HD-1910 ships with its own 2.0 mm 3-pin lead.
- **Too much voltage.** A full 2S pack is already at 8.4 V, and 12 V damages the HD-1910.
- **Mixed revisions.** Printed parts, firmware and walking policy must all match the HD-1910 version. Parts printed for the XL330 do not clear the HD-1910 horn.
- **Using the official robot firmware unchanged.** The official Microduck talks to its servos over the Dynamixel protocol, so an HD-1910 build needs a Feetech bus driver.
- **Skipping the test fit.** Print one bearing seat and one servo mount first. Our guide to [cleaning up 3D-printed robot parts](https://armdojo.com/blogs/guides/clean-up-3d-printed-robot-parts-supports-bearing-seats?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) covers bearing seats and servo pockets.

## Printed parts (in progress)

We are designing our own HD-1910 printed parts around the servo's measured dimensions, the way we built our [5-axis desktop arm](https://github.com/miraclewhite-tech/armdojo-hardware). They will appear in [`printed-parts/`](printed-parts) as print-oriented STL and STEP files with print settings. Until then, print the parts from the HD-1910 release of the build you follow. Watch this repository or join [Discord](https://discord.gg/MdyRuJVFAm) to hear when the first parts are up.

## Repository layout

```
docs/servo-setup.md   FE-URT-2 wiring, 7.3 V setup, servo ID map
printed-parts/        ArmDojo HD-1910 parts (coming)
LICENSE               CC BY-NC-SA 4.0
```

## Community

- **Discord:** https://discord.gg/MdyRuJVFAm
- **More guides:** the [Robot Builder FAQ](https://armdojo.com/blogs/guides/robot-builder-faq-feetech-servos-microduck-robot-dog?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) answers common servo, duck and robot-dog questions.
- Issues and pull requests are welcome.

## License

- **Documents, images and printed-part files** in this repository: [CC BY-NC-SA 4.0](LICENSE). You may share and adapt them for non-commercial use, with attribution to ArmDojo, under the same license.
- Product names are used only to describe compatibility. ArmDojo is not affiliated with the projects named here.
