# Servo setup for an HD-1910 duck

Set up all 15 servos on the bench, one at a time, before any of them goes into a printed part. Every Feetech HD-1910-C001 leaves the factory as **ID 1 at 1,000,000 baud**, so two new servos on the same bus answer as one.

## What you need

- 15 × Feetech HD-1910-C001 servos, each with its 2.0 mm 3-pin lead ([duck set](https://armdojo.com/products/feetech-hd-1910-c001-coreless-servo-microduck?variant=50899680592111&utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck))
- A [Feetech FE-URT-2](https://armdojo.com/products/feetech-fe-urt-2-usb-ttl-rs485-servo-debug-board?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) USB debug board and the USB-A to USB-C data cable from its box. Charge-only USB-C cables will not connect.
- An [adjustable 3–12 V 5 A power supply](https://armdojo.com/products/servo-power-adapter-7-4v-8-4v-3a-dc-5-5x2-1?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) with its DC jack lead
- A computer with Chrome or Edge for the free [ArmDojo Servo ID Tool](https://armdojo.com/pages/servo-id-tool?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck), or a Windows computer for Feetech FD. On Linux and macOS the board also works as a serial port for the Feetech SCServo SDK.
- A marker to label the servos

## 1. Set the voltage first

The adjustable supply ships at its lowest setting.

1. Plug the supply into the wall with nothing connected to its DC plug.
2. Turn the knob until the display reads **7.3**.
3. Unplug it from the wall again before you wire anything.

The HD-1910-C001 is rated 4–8.4 V. Never connect it while the display reads more than 8 V; 12 V damages it.

## 2. Wire the FE-URT-2

1. With the supply unplugged, put the black wire of the jack lead into **G** and the red wire into **V1**, on the TTL side of the screw terminal, and tighten both screws.
2. Leave **G / V2** empty. That pair is for RS485 servos.
3. Push the supply's barrel plug into the jack lead.
4. Connect **one** servo to the board.

USB alone powers the servo port while you set IDs. Switch on the external supply before a servo moves under load, and switch servo power off before you plug or unplug a servo.

## 3. Connect the board to your computer

On Windows the driver installs by itself. The board appears in Device Manager → Ports as **USB-Enhanced-SERIAL CH343 (COMx)**; note the COM number.

## 4. Give each servo its ID

**In the browser (any computer):** open the free [ArmDojo Servo ID Tool](https://armdojo.com/pages/servo-id-tool?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck) in Chrome or Edge and press *Connect URT-2*. Set *Start at ID* 10 and *Last ID* 14, press *Start numbering* and plug in one servo at a time: each one gets the next ID, is set to 1 Mbps and is read back. Then do 20–24 and 30–34. Keep the 7.3 V supply connected. The tool shows the HD-1910 by its model number.

**In Feetech FD (Windows):**

1. Select the CH343 COM port, set the baud rate to **1000000** and click **Open**.
2. Click **Search**. When the servo appears, click **Stop**, then click the servo. A new servo shows ID 1.
3. Open the **Programming** tab, select the **ID** row, type the new ID and click **Save**.
4. Power-cycle the servo and click **Search** again to confirm the new ID.
5. Write the ID on the servo, unplug it and connect the next one.

### ID map

| IDs | Joints in microduck-replica |
|---|---|
| 10–14 | Right leg |
| 20–24 | Left leg |
| 30–34 | Neck, head and beak |

XGO-Duck uses the same three ID ranges. Check your build's joint list before you assemble.

## 5. Centre, plan, test unmounted

- **Centre each servo** with centre calibration in FD before it goes into a joint, then label it.
- **Plan the direction of every servo.** Servos on mirrored joints turn opposite ways, so decide each orientation before you mount it.
- **Run the first motion tests with the servo out of the frame**, so a wrong command cannot drive a joint into a hard stop.

## If something doesn't work

| Symptom | Likely cause | Fix |
|---|---|---|
| FD finds no servo | Wrong COM port or baud rate, or a charge-only cable | Pick the CH343 port and 1000000 baud, and use the cable from the box |
| Several servos answer as one, or replies are garbled | Duplicate IDs | Set the IDs one servo at a time |
| Servos reset when several move together | Supply set too low, or the whole robot drawing power through the board | Check the display; run the finished duck from its battery |
| A servo does nothing after power-on | It may have seen too high a voltage | Check the display before you connect; ask on [Discord](https://discord.gg/MdyRuJVFAm) before you open anything |

The illustrated version, with a printable two-page PDF, is our [Feetech servo setup guide](https://armdojo.com/blogs/guides/feetech-servo-setup-guide-fe-urt-2-wiring-voltage-ids?utm_source=github&utm_medium=referral&utm_campaign=armdojo-duck).
