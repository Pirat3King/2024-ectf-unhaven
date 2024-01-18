## Setup
Run everything from the Nix shell
`nix-shell`

First install packages from Poetry
`poetry install`

Run all tools via Poetry:
`poetry run {toolname}` 
OR
`poetry shell` then tool

## Build and Flash
### See `README.md` for more details

Build Deployment:
`poetry run ectf_build_depl -d ../2024-ectf-unhaven`

Build AP:
`poetry run ectf_build_ap -d ../2024-ectf-unhaven -on ap --p 123456 -c 2 -ids "0x11111124, 0x11111125" -b "Test boot message - UNHaven" -t 0123456789abcdef -od build`

Build Sensors/Components:
`poetry run ectf_build_comp -d ../2024-ectf-unhaven -on comp24 -od build -id 0x11111124 -b "Component boot" -al "West Haven" -ad "01/18/2024" -ac "Charlie"`

Flash Boards:
`poetry run ectf_update --infile ../2024-ectf-unhaven/build/ap.img --port /dev/ttyUSB0`

## Host Tools
List Tool:
`poetry run ectf_list -a /dev/ttyUSB0`

Boot Tool:
`poetry run ectf_boot -a /dev/ttyUSB0`

Replace Tool:
`poetry run ectf_replace -a /dev/ttyUSB0 -t 0123456789abcdef -i 0x11111126 -o 0x11111125`

Attestation Tool:
`poetry run ectf_attestation -a /dev/ttyUSB0 -p 123456 -c 0x11111124`


## Troubleshooting
If your AP/Components do not build and throw the following error:
`/msdk/Libraries/libs.mk: No such file or directory`
You may have to copy the extracted msdk files in "msdk/4c8989pnvxrgs8g3qb1kfx76ki56j0da-source" to the msdk root
