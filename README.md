# THAR ROXX Bluetooth Controller

Native Android Studio project for an HC-05 Bluetooth Classic controlled Arduino RC car.

## Features
- Connect to an already-paired HC-05 module
- Forward, reverse, left, right (press to drive; release to send stop)
- Five gear buttons sending `1` through `5`
- Headlight toggle `H`
- Interior light toggle `I`
- Brake/stop command `S`
- Parses Arduino messages such as `DIST:24 cm` and `OBSTACLE WARNING`

## Hardware assumptions
- Arduino UNO
- L293D Motor Driver Shield V1 (Adafruit Motor Shield V1 compatible)
- HC-05 at 9600 baud, wired TX -> A0 and RX <- A1 through a voltage divider
- Sharp GP2Y0A21YK0F analog IR distance sensor OUT -> A5
- Headlight -> A2, brake light -> A3, interior light -> A4 (each LED uses a suitable resistor)
- Arduino firmware uses the matching `AFMotor` library and the command protocol above.

## Build an APK
1. Install Android Studio on a computer.
2. Open this `TharRoxxController` folder in Android Studio.
3. Allow Gradle sync and install the Android SDK platform 35 if prompted.
4. Choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. Android Studio creates the APK under `app/build/outputs/apk/debug/app-debug.apk`.

## Install and pair
1. On Android, enable Bluetooth and pair with HC-05 in system Bluetooth settings.
2. The common HC-05 PINs are `1234` or `0000`, but use the module's configured PIN.
3. Install the APK and grant the nearby Bluetooth permission.
4. Open the app, tap Connect HC-05, and select the paired module.

## Safety / limitations
- Test with the wheels lifted before putting the car on the ground.
- Use an appropriate motor battery and ensure the L293D current rating is adequate for each motor.
- The app does not measure real vehicle speed; gear is a PWM speed setting.
- IR distance values depend on sensor calibration, target surface and angle.
- The Arduino sketch must implement the same serial protocol. Do not rely on obstacle detection as the only means of stopping.
- This project source is provided; a compiled APK is not included because an Android SDK/Gradle build environment is not available in this workspace.
