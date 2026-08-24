# Iron Man Helmet Motorization Build Guide

This guide combines:

- **Walsh3D Servo Pro** for the mechanical motorization system
- **Crash Works MKE-Mini** for servo, switch, LED, and power control

The basic workflow is:

**Walsh pages 6–15 → Crash Works pages 1–2 → Walsh pages 17–18**

> Important: Walsh page 16 contains Arduino-specific servo-zeroing code. Because this build uses the MKE-Mini, that Arduino code is generally skipped and the MKE-Mini startup homing routine is used instead.

---

## 1. Print the Walsh3D Servo Pro Parts

Use **Walsh3D PDF pages 6–8**.

### Recommended print settings

- Layer height: **0.16 mm**
- Infill: **40%**
- Walls: **4**
- Supports: only where instructed

Walsh lists these parts at 100% scale:

- Arm Retainer — mirror and print 2
- Face Lighting Module
- Faceplate Interface
- Knob
- Primary Servo Arm — mirror and print 2
- Secondary Servo Arm — mirror and print 2
- Servo Case
- Servo Cover

Pages 7–8 show the required print orientation and which parts need support.

Source: Walsh3D PDF, pages 6–8.

---

## 2. Add the Walsh Mounting System to the Helmet if Needed

Start with **Walsh3D PDF page 20**.

The Servo Pro uses two mounting points:

- Dome mount
- Faceplate mount

The spacing between these mounts must remain fixed.

### If the helmet has not been printed yet

Use **Walsh pages 21–26**.

The guide walks through:

1. Opening the supplied `Mounting System` Blender file
2. Importing the helmet STL
3. Positioning the helmet relative to the mounts
4. Extruding the mounts if necessary
5. Exporting the modified dome and faceplate STLs

Walsh recommends this Blender method when possible.

### If the helmet is already printed

Use **Walsh pages 27–34**.

The guide walks through:

1. Importing the helmet into Blender
2. Positioning the mounting system
3. Boolean-cutting the dome mount to match the helmet
4. Boolean-cutting the faceplate mount
5. Exporting both mounts
6. Printing the mounts and alignment tool
7. Gluing the mounts into the helmet using the alignment tool



The final mounting and alignment steps are on page 34.

---

## 3. Install the Heat-Set Inserts and Assemble the Servo Pro

Use **Walsh pages 10–15**.

### Heat-set inserts

Page 10 explains how to install the M3 heat-set inserts using a soldering iron.

Walsh instructs you to:

1. Align the small side of the insert with the printed hole.
2. Gently heat and push it into the plastic.
3. Avoid pushing it too far.



### Insert locations

Page 11 shows the 11 heat-set inserts:

- 4 into the Servo Case
- 4 into the Servo Interface
- 1 into the knob
- 2 into the faceplate mount



### Continue assembly

Pages 12–15 cover:

- Installing the two MG90S servos
- Installing the Secondary Servo Arms
- Installing the servo cover
- Installing the M3×45 screw
- Installing the knob
- Assembling the Primary and Secondary Servo Arms
- Installing the arm retainers
- Installing the locknuts
- Checking that the linkage moves freely



---

## 4. Stop Before Attaching the Primary Servo Arms

Stop at **Walsh page 15, Step 16**.

Walsh specifically says:

> Before attaching the Primary Servo Arm, the servo must be zeroed.



Do **not** permanently install the Primary Servo Arms yet.

---

## 5. Wire the Servos to the MKE-Mini

Use the **Crash Works MKE-Mini PDF, pages 1–2**.

The MKE-Mini supports up to three MG90S servos.

For the standard Walsh Servo Pro mechanism, use:

- **Servo 1**
- **Servo 2**

Servo 3 is not needed unless you add another motorized function.

### Included servo wiring

Crash Works specifies:

- Black = Ground
- Red = Positive
- Yellow = Signal

For MG90S servos, the servo's own signal wire is typically **orange**.



The connector layout is shown in the diagram on **Crash Works page 2**.

---

## 6. Wire the Roller Limit Switch

Use **Crash Works page 2**.

The MKE-Mini requires a:

**Momentary Normally Open switch**

For a limit switch, connect the MKE-Mini switch harness to:

- **C** — Common
- **NO** — Normally Open

Do **not** use the NC terminal.



The MKE-Mini switch input is not polarity-sensitive.

---

## 7. Connect the LED Eyes

Use **Crash Works pages 1–2**.

The supplied LED connector uses:

- Red = Positive
- Black = Ground

The MKE-Mini LED output includes a current-limiting resistor.

The LED connector location is shown in the page-2 MKE-Mini diagram.



> Note: If using flexible LED eye panels instead of simple LEDs, verify their electrical requirements before connecting them to the MKE-Mini.

---

## 8. Connect Power to the MKE-Mini

Use **Crash Works page 1**.

The MKE-Mini requires a USB power bank providing:

- **5V / 2.1A**, or
- **5V / 2.4A**, or
- **5V / 3A**



### Important

The MKE-Mini is powered through its dedicated **Power-In JST connector**.

Do **not** power the board through the ESP32-C3 USB port.

Crash Works explicitly warns:

> Do not power the board by plugging a USB cable directly into the ESP32-C3 module.



The included Power-In connector uses:

- Red = +5V
- Black = Ground

---

## 9. Let the MKE-Mini Home the Servos

After the servos, switch, LEDs, and power are wired correctly, power on the MKE-Mini.

On initial startup:

1. The LEDs blink.
2. The servos move to their home position.
3. The first switch press tells the system that you are ready for operation.



For this build, use that home position as the servo-zeroing point required by Walsh.

This replaces the Arduino-specific zeroing process described on Walsh page 16.

---

## 10. Attach the Primary Servo Arms

Return to **Walsh page 17, Step 17**.

With the servos still in their MKE-Mini home position:

1. Position the Servo Pro mechanism in its closed configuration.
2. Push the Primary Servo Arms onto the MG90S output splines.
3. Secure each arm using the small servo screw supplied with the MG90S.

Walsh notes that the printed servo-arm teeth may self-tap onto the servo spline.



---

## 11. Test the Mechanism Before Mounting It

Use **Crash Works page 2**.

After the initial setup press, each subsequent button press alternates between:

- Opening the helmet and turning the eyes off
- Closing the helmet and turning the eyes on

A double-tap cycles the eye brightness through:

- Off
- Low
- Medium
- High



Before mounting the assembly into the helmet, verify:

- Both servos move in the correct directions
- The faceplate reaches fully open
- The faceplate reaches fully closed
- The linkage does not bind
- No servo is trying to push past a mechanical stop

---

## 12. Mount the Servo Pro Into the Helmet

Return to **Walsh pages 17–18**.

Step 18 begins mounting the Servo Pro assembly into the helmet.

### Dome attachment

Use:

- **2 × M3×8 screws**

### Faceplate attachment

Use:

- **2 × M3×8 screws**

These final attachment steps are shown on Walsh page 18.

---

# Recommended Build Order

```text
Walsh PDF
Pages 6–8
Print Servo Pro parts
        ↓
Walsh PDF
Pages 20–34 if mounts need to be added
        ↓
Walsh PDF
Pages 10–15
Assemble Servo Pro
        ↓
STOP before attaching Primary Servo Arms
        ↓
Crash Works PDF
Pages 1–2
Wire servos, switch, LEDs, and power
        ↓
Power on MKE-Mini
Let servos move to HOME position
        ↓
Walsh PDF
Page 17
Attach Primary Servo Arms
        ↓
Crash Works PDF
Page 2
Test open/close operation
        ↓
Walsh PDF
Pages 17–18
Install completed mechanism into helmet
```

---

# Which Manual Controls What?

| Task | Manual |
|---|---|
| Print settings | Walsh3D |
| Part orientation | Walsh3D |
| Servo Pro mechanical assembly | Walsh3D |
| Heat-set inserts | Walsh3D |
| M3 hardware installation | Walsh3D |
| Helmet mounting system | Walsh3D |
| Blender mount adaptation | Walsh3D |
| Servo wiring | Crash Works |
| Switch wiring | Crash Works |
| LED wiring | Crash Works |
| Power wiring | Crash Works |
| Servo startup/homing | Crash Works |
| Button behavior | Crash Works |
| LED brightness controls | Crash Works |
| Final linkage installation | Walsh3D |

---

# Important Notes

## Skip the Arduino code on Walsh Page 16

Walsh page 16 provides Arduino code for manually zeroing the MG90S servos.

Because this build uses the MKE-Mini, use the MKE-Mini's automatic startup homing routine instead.

## Do Not Power the MKE-Mini Through USB

The USB connector visible on the ESP32-C3 is for programming/debugging.

The board must receive 5V through the dedicated **Power-In JST connector**.

## Do Not Attach the Primary Arms Before Homing

Walsh requires the servos to be zeroed before the Primary Servo Arms are installed.

Therefore:

**Wire MKE-Mini → power it on → let servos home → attach Primary Servo Arms.**