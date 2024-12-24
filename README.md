# Expo Camera Barcode Scanning Bug

This repository demonstrates a bug encountered when using the Expo Camera API for barcode scanning.  The scanner intermittently fails to detect barcodes, even with necessary permissions granted.  The bug is characterized by inconsistent behavior, making debugging challenging.

## Bug Description
The `onBarCodeScanned` callback of the Expo Camera API sometimes returns no data or an empty array when a barcode is clearly within the camera's view. This occurs despite having the correct permissions set and the barcode being easily readable by other barcode scanning apps.

## Reproduction Steps
1. Clone this repository.
2. Install the dependencies using `npm install`.
3. Run the app using `expo start`.
4. Point the camera at a barcode.
5. Observe that the barcode is sometimes detected correctly, and sometimes not detected at all, seemingly randomly.

## Solution
The solution involves adding a small delay and multiple calls to `scanBarcodesAsync` to overcome some internal timing issues of the `Expo.BarCodeScanner`. This isn't a perfect fix, as the root cause remains unknown, but it improves the reliability of barcode scanning significantly.
