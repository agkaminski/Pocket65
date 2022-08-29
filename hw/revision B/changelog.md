# Pocket65B changelog

Second revision of Pocket65 PC. Not tested yet!

## Fixes

- fixed the USB charger module footprint, now it should fit without any spacers,
- moved the expantion slot inward, it should not stick out so much.

## Changes

Things that might fix memory timing issues:

- Use PH0 for PH2 instead of inverted PH1,
- Changed memory decoder and read/write signals generation. Previously memory decoder was gated by PH2. This caused late /CS signal assertion. In revision B memory decoder isn't gated, read and write (/RD and /WR) signals are.

Simplification/BOM cheaping - removed quartz clock generator, replaced it with a RC oscilator on 74HC14.

Changed common anode displays to common cathode - there is an availability issues with CA displays.
