# Meizu S25 · Linux 3.18.140

**Device:** Meizu S25, MediaTek MT6755. **Branch:** `lineage-15.1`.
This tree contains the S25 board profile and the matching display/touch bring-up
resources. The BSP calls this platform `mt6755`.

## Hardware and source map

This table reads [s25_defconfig](arch/arm64/configs/s25_defconfig). Listed options
are defconfig requests; they are not a newly generated configuration or a
compilation receipt. Static bring-up does not certify every branch tip or replace
hardware testing.

| Component | Source implementation | Configuration / integration | Compiled | Working on this branch |
|---|---|---|---|---|
| Display panels | [LCM drivers](drivers/misc/mediatek/lcm) | `ili9881p_hd_dsi_txd` | Not rechecked | Not verified for this tip |
| Touchscreen | [MediaTek touch drivers](drivers/input/touchscreen/mediatek) | `TOUCHSCREEN_MTK_FT5X0X=y` | Not rechecked | Board-variant tests needed |
| GPU | [Mali GPU drivers](drivers/misc/mediatek/gpu) | `mali midgard r12p1` | Not rechecked | Rendering / DVFS tests needed |
| Cameras | [Image-sensor drivers](drivers/misc/mediatek/imgsensor) | `imx278_mipi_raw ov8856jsl_mipi_raw` | Not rechecked | Camera pipeline tests needed |
| PMIC | [MT6353](drivers/misc/mediatek/pmic/mt6353) | `MTK_PMIC_NEW_ARCH=y`, `MTK_PMIC_CHIP_MT6353=y` | Not rechecked | Power / thermal tests needed |
| Audio | [MediaTek ASoC](sound/soc/mediatek) | `MT_SND_SOC_6750=y` | Not rechecked | Call / media routes need testing |
| Wi-Fi / Bluetooth | [CONSYS drivers](drivers/misc/mediatek/connectivity) | `CONSYS_6755`, `MTK_COMBO_WIFI=y` | Not rechecked | Firmware and radio tests needed |
| Modem transport | [ECCCI](drivers/misc/mediatek/eccci) | `MTK_ECCCI_DRIVER=y` | Not rechecked | Depends on modem firmware and Android RIL |
| Accelerometer | [Accelerometer drivers](drivers/misc/mediatek/accelerometer) | `MTK_BMA253=y` | Not rechecked | Orientation / variant tests needed |
| Storage | [MediaTek MMC](drivers/mmc/host/mediatek) | `MMC_MTK=y` | Not rechecked | I/O / suspend tests needed |

## Build inputs

Use the kernel in the repository root, `ARCH=arm64`, and an absolute
`CROSS_COMPILE` prefix for AArch64 Android GCC 4.9. Select
[s25_defconfig](arch/arm64/configs/s25_defconfig) and use a separate Kbuild output
directory. The BSP image target is `Image.gz-dtb`; matching board
generation inputs, ramdisk, command line and boot-image geometry are still
required for device integration. A kernel image alone is not a ROM.

No new build or device test was run for this source-map update. Use the matching
Android device tree and board firmware; a common chipset is not a substitute
for matching panel, touch, power and storage resources.

## Related branches

- [S25 kernel profile](../../tree/lineage-15.1)

## Credits and licensing

Built on Linux, Android and MediaTek BSP work. Original vendor and downstream
authors remain credited in Git history and per-file notices. See
[COPYING](COPYING); individual files may carry additional terms.
Device firmware, calibration and Android vendor libraries are separate inputs.

[ReMeizu project status](https://github.com/nomorecoolnicknames/remeizu/blob/main/PROJECT_STATUS.md)
