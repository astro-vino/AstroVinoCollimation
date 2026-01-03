# Astro Vino Collimation – Application Guide

This document explains how to *use* the application (what each control does and a recommended workflow). It does **not** cover building/compiling.

## What the app is for

Astro Vino Collimation is a live camera viewer with visual overlays designed to help you center a bright star/feature and judge alignment (collimation) using a **center crosshair** and **concentric circles**.

<img width="1484" height="992" alt="image" src="https://github.com/user-attachments/assets/9b744ed1-fbbc-4c12-87bb-2c04963d0323" />


It supports:

- **ZWO ASI cameras**
- **Generic webcams** (driver support for camera controls varies by device)

## Quick start

1. **Select a camera** from the Camera dropdown.
2. Click **Connect**.
3. Confirm the live view is updating.
4. Adjust **Exposure** and **Gain** until the star/feature is clearly visible.
5. Enable overlays and adjust **circle radii** to match your workflow.
6. Use **Nudge** controls to align overlays to the on-screen target.

## Main concepts

### Live image vs overlays

- The camera image is displayed with correct aspect ratio.
- Overlays (crosshair + circles) are drawn *only over the displayed image area* (i.e., they remain aligned even if the image is letterboxed).

### Overlay scaling

Circle radii are defined in **image pixels** and automatically scale to whatever size the image is displayed at.

## Controls reference

### Primary Controls panel

#### Show Crosshair / Circles

- Toggles overlay visibility:
  - **ON**: shows center crosshair and all circles
  - **OFF**: hides them

#### Circle 1 Radius / Circle 2 Radius / Circle 3 Radius

- Adjusts the radii of the 3 concentric circles.
- Each circle is color-coded:
  - Circle 1: **Lime**
  - Circle 2: **Yellow**
  - Circle 3: **DeepSkyBlue**

Tips:

- Use the `-` / `+` buttons for precise single-step changes.
- Use the slider to reach the approximate size quickly, then fine-tune with buttons.

#### Nudge

Moves the crosshair/circle center relative to the image.

- **↑ / ↓ / ← / →**: nudges the overlay center
- **Reset**: returns nudge offset to the default center

Keyboard support:

- Arrow keys also nudge the overlay center.

#### Focus

- This is primarily for **webcams**.
- The slider is always visible, but it is only enabled when focus control is available.

Notes:

- Many webcams do **not** expose focus control.
- Some drivers require the camera to be in manual focus mode to accept focus changes.

### Bottom control bar

#### Camera selector + Connect

- **Camera dropdown**: choose between detected ZWO cameras and a small set of generic webcam entries.
- **Connect**:
  - Connects to the selected camera
  - Starts streaming
  - Clicking again disconnects

#### Exposure (ms)

- Sets manual exposure time.
- **Auto Exposure** checkbox toggles automatic exposure.

Behavior notes:

- When **Auto Exposure** is ON:
  - Manual exposure controls are disabled (to avoid conflicting settings).
- When **Auto Exposure** is OFF:
  - Manual exposure slider/text is active.

Webcam note:

- Webcam exposure behavior is highly driver-dependent. Some devices ignore exposure changes or use different exposure units.

#### Gain

- Sets camera gain.

Webcam note:

- Some webcams do not support gain control (or may label it differently internally).

#### ROI Controls (ASI cameras)

These controls apply to **ZWO ASI cameras**.

- **Bin**: sensor binning (1x, 2x, 3x, 4x)
- **Format**: image format (e.g., RAW8 / RGB24 / RAW16)
- **Reset ROI**: resets the camera to full-frame capture

#### Save Image

- Saves the currently displayed frame to a file.

### Viewport overlay text

- **X / Y coordinate readout** shows the mouse position in **image pixel coordinates**.

## Recommended collimation workflow (example)

1. Center a bright star/feature in the viewport.
2. Turn overlays ON.
3. Adjust exposure/gain until rings/features are visible.
4. Set circle radii to match your intended measurement points.
5. Use Nudge to place the crosshair exactly on the target center.
6. Make optical adjustments while watching how the pattern changes relative to the circles.

## Troubleshooting

### “Controls don’t do anything” (webcam)

Many webcam controls depend on the driver:

- Exposure / gain / auto exposure / focus may not be supported
- Some settings only work when the camera is in a specific mode

If a control is unsupported, the application will keep streaming video, but the setting might not visibly change.

### Overlays appear misaligned

If you changed camera/format and something looks off:

- Toggle overlays OFF then ON.
- Resize the window once (forces the layout to recalc the displayed image area).

## Glossary

- **Exposure**: how long each frame integrates light.
- **Gain**: amplification applied to the sensor signal.
- **Binning**: combining adjacent pixels to improve sensitivity.
- **ROI**: region of interest (capturing only part of the sensor).
