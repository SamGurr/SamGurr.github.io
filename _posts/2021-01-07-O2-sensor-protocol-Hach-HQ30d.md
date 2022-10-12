---
layout: post
title: O2 sensor protocol Hach HQ30d
date: '2021-01-07'
categories: Protocols
tags: O2 sensor, dissolved oxygen, protocol
---

*last updated 20210107*

## About

The following protocol can be used for setting up and using the Oxygen sensor Hach HQ30d

**Note:** SJG used this sensor on 20210107. The AA batteries in the meter were heavily corroded and replaced - the inside of the plastic is also heavily corroded by the batteries. Something to keep an eye on if the meter has issues in future use.


#### Specs:

* **DO Measurement Range** = 0.1 - 20.0 mg/L (ppm) 1 - 200% saturation
* **DO Measurement Resolution** = 0.1 mg/L

* Links:
	* [Hach HQ30d manual](https://www.hach.com/hq30d-portable-multi-meter-ph-conductivity-tds-salinity-dissolved-oxygen-do-orp-and-ise-for-water/product-details?id=7640494072)
	* [Manual calibration protocol]()

## Contents

- [**Calibration**](#Calibration)
- [**Setup/Usage**](#Setup/Usage)
- [**Functions**](#Functions)

## <a name="Calibration"></a> **Calibration**

Calibration for DO sensor ONLY.

**Note:** The DO sensors are factory calibrated, but offer a manual calibration in 100% saturated water/seawater.

**Manual Calibration of DO sensor** -  [review here](https://dnr.wi.gov/lakes/CLMN/manuals/HQ30d%20Portable%20Meter%20Instruction%20Guide.pdf)
1. Connect the DO probe into the **left port** on the top of the meter and screw it closed. Select Calibrate. If more than one probe is connected, select the probe to calibrate.

2. Fill a plastic bottle with room temperature tap water

3. Shake vigorously for 30 seconds. (this assumes a manual calibration to 100% air saturation)

4. Turn meter on (**probe must be connected before meter is on**).
* *if the meter does not power on or show recorded values...* check/replace batteries in the meter (4 AA) and/or on the sensor (plastic nob with a caution symbol, pull this out and youll find a 2032 battery)


5. Remove probe safety guard *(do not touch sensor cap). Then
place the probe into the bottle.

6. Push the CALIBRATE key, and press the green button to
activate calibration

7. Select READ. The display will show Stabilizing… and a
progress bar as the probe stabilizes - the meter will beep when it is stabalized

8. Select Done to view calibration summary.

9) Select Store to accept calibration.

10) *Reassemble black safety guard without touching sensor cap.

Note: If the meter rejects the calibration, refer to the user manual for the probe.

## <a name="Setup/Usage"></a> **Setup/Usage**

1. After calibration steps above (assume probe is plugged in, meter is on, and safety guard is fixed to the sensor). Submerge the sensor is your sample


2. Select **Read**. the display will show **Stabalizing...** with a progress bar. Once full, the meter will beep to signify the measurement stabalized and the value is automatically sotred in the **data log**

3. Write you value in the lab notebook

4. Repeat 2-3 for all your samples/tanks

5. When putting the unit/probe back into its case (ziploc bag for now...), make sure the probe’s wire doesn’t get pinched in the case’s binding, or the unit will have issues taking readings


## <a name="Functions"></a> **Functions**

	* ```Flask icon``` button allows the user to cahnge the sample name/unique ID associated with each recorded measurment.

	* ```Folder icon``` button for **data log**.  One can view past records with timestamp and unique IDs.
