# Extra HAL files for Silicon Labs SDK for Zephyr

This module provides additional HAL content that is not part of upstream Zephyr for use with the
Silicon Labs SDK for Zephyr.

The following SDKs are imported:

* `simplicity_sdk` - Simplicity SDK for EFM32 and EFR32 Series 2 devices

## Simplicity SDK

Scripts from [hal_silabs](https://github.com/SiliconLabsSoftware/hal_silabs) are used to update
this repository. The file list from this repository is passed to the script as an argument. Assuming
a default Zephyr workspace layout where `hal_silabs` is checked out to a sibling directory, run:

```
../silabs/scripts/update_simplicity_sdk.py              \
        --src <path/to/simplicity_sdk>                  \
        --dst simplicity_sdk/                           \
        --file-list scripts/simplicity_sdk_files.yaml   \
        --signoff
```

where `<path/to/simplicity_sdk>` points to a checked out copy of the Simplicity SDK git repository.


### Z3 Light ZAP / Studio autogen (MSLA)

Application ZAP output for the Zephyr `zigbee_z3_light` sample lives under
`samples/zigbee_z3_light/autogen/` in this module (not in the public
`zephyr-silabs` sample tree). Refresh after regenerating in Simplicity Studio:

```
rsync -a --delete \
  <sisdk>/zigbee_app/z3/zigbee_z3_light/build/<app>/autogen/ \
  samples/zigbee_z3_light/autogen/
```

Do not add these paths to `simplicity_sdk_files.yaml`; they are app-generated,
not SDK package imports.

See the README in `hal_silabs` for more details about commit naming requirements etc.
