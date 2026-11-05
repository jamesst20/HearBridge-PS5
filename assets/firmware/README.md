# Bundled Realtek USB Bluetooth firmware

Files here are copied from the
[linux-firmware `rtl_bt` tree](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_bt)
and redistributed under
[LICENCE.rtlwifi_firmware.txt](LICENCE.rtlwifi_firmware.txt).

`scripts/gen_rtl_fw.py` embeds the listed blobs into `src/rtl_fw_blobs.h`.
On start, HearBridge writes any missing or outdated copies to
`/data/hearbridge/firmware/` on the console.

Every USB part in `src/bt/realtek_fw.c`'s chip table is shipped:

- `rtl8723b_fw.bin` / `rtl8723b_config.bin`
- `rtl8723d_fw.bin` / `rtl8723d_config.bin`
- `rtl8821a_fw.bin` / `rtl8821a_config.bin`
- `rtl8821c_fw.bin` / `rtl8821c_config.bin`
- `rtl8761a_fw.bin` / `rtl8761a_config.bin`
- `rtl8761bu_fw.bin` / `rtl8761bu_config.bin`
- `rtl8761cu_fw.bin` / `rtl8761cu_config.bin`
- `rtl8822b_fw.bin` / `rtl8822b_config.bin`
- `rtl8822cu_fw.bin` / `rtl8822cu_config.bin`
- `rtl8852au_fw.bin` / `rtl8852au_config.bin`
- `rtl8852bu_fw.bin` / `rtl8852bu_config.bin`
- `rtl8852cu_fw.bin` + `rtl8852cu_fw_v2.bin` / `rtl8852cu_config.bin`
- `rtl8851bu_fw.bin` / `rtl8851bu_config.bin`
- `rtl8922au_fw.bin` / `rtl8922au_config.bin`
- `rtl8852btu_fw.bin` / `rtl8852btu_config.bin`

`linux-firmware` ships several of those config names as symlinks to another
config (for example `rtl8761a_config.bin` -> `rtl8761bu_config.bin`); the
copies here are resolved so the loader always finds a regular file.

Only RTL8761BU has been tested on PS5 hardware. The other chips are built
from the same `btrtl` table and file formats.
