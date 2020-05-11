### Updating sysprop files

#### Android 10 (Q)

```sh
lunch sdk # (Can use sdk-eng too)
export ALLOW_MISSING_DEPENDENCIES=true # Ignore errors about hostapd, wpa_supplicant etc missing
build/soong/scripts/gen-java-current-api-files.sh "vendor/oss/opentelephony/ModemConfig/sysprop" && m update-api
```

#### Android 11 (R)

```sh
lunch sdk # (Can use sdk-eng too)
export ALLOW_MISSING_DEPENDENCIES=true # Ignore errors about hostapd, wpa_supplicant etc missing
build/soong/scripts/gen-sysprop-api-files.sh "vendor/oss/opentelephony/ModemConfig/sysprop" "SomcModemProperties"
m SomcModemProperties-dump-api && rm -rf vendor/oss/opentelephony/ModemConfig/sysprop/api/SomcModemProperties-current.txt && cp -f out/soong/.intermediates/vendor/oss/opentelephony/ModemConfig/sysprop/SomcModemProperties_sysprop_library/api-dump.txt vendor/oss/opentelephony/ModemConfig/sysprop/api/SomcModemProperties-current.txt
```
