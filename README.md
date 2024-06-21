# pco_edge26
Python device adaptor: PCO.edge 26 USB sCMOS camera.
## Quick start:
- Install the PCO USB interface driver, then install 'Camware' to test the camera and get the latest
 "SC2_Cam.dll" (a version included here). Put the .dll in the directory with "pco_edge26.py" and run
 the script (requires Python and numpy).

![social_preview](https://github.com/amsikking/pco_edge26/blob/main/social_preview.png)

## Details:
- The adaptor reveals a minimal API from the extensive PCO SDK by following the 'typical implementation'
for a series of .dll calls for camera setup, image acquisition and tidy up.
- See the '\_\_main__' block at the bottom of "pco_edge26.py" for some typical ways to interact with a
stand alone camera.
- The demo unit tested was unreliable. Power is seemingly shared between the DC adaptor, the switch and the USB port and would randomly fail or the usb connection would be lost.
- With the current firmware (FW_PCO_EDGE_26_USB3_V01_02) the camera defaults to the trigger I/O line (SMA 1) being switched off in software (which is applied on power up or when calling 'PCO_ResetSettingsToDefault'). It can be toggled on in Camware and triggered manually (with NI-MAX test panels for example), but to achieve this in Python would require implementing a large struct: see PCO_GetHWIOSignalDescriptor (TRIGGER_INPUT) and PCO_SetHWIOSignal in PCO SDK for details. So currently no external triggering has been successfully implemented in Python.
  - i.e. 'pco_edge26_external_trigger_example.py' has not successfully run (included as template for future testing).
