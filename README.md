# openthread-implementation

## Building NCP

For dongle:

Clean first!! This was a pitfall before.

`make -f examples/Makefile-nrf52840 clean`

`make -f examples/Makefile-nrf52840 USB=1 BOOTLOADER=1`

https://github.com/openthread/openthread/tree/master/examples/platforms/nrf528xx/nrf52840#usb-cdc-acm-support

Convert from ELF to HEX:

`arm-none-eabi-objcopy output/nrf52840/bin/ot-ncp-ftd -O ihex --change-addresses 0x01000 output/nrf52840/bin/ot-ncp-ftd.hex`

`arm-none-eabi-objcopy output/nrf52840/bin/ot-cli-ftd -O ihex --change-addresses 0x01000 output/nrf52840/bin/ot-cli-ftd.hex`

## Building OpenThread Border Router (OTBR)

Install docker.

Then:
`docker pull openthread/otbr:latest`

Building NCP:

`make -f examples/Makefile-nrf52840 USB=1 BOOTLOADER=1 BORDER_ROUTER=1`

https://openthread.io/guides/border-router/docker

https://openthread.io/guides/border-router/docker/run

## Testing

Connect to device:

`screen /dev/ttyACM0 115200`

https://github.com/openthread/openthread/tree/master/examples/apps/cli


## Examples

https://codelabs.developers.google.com/codelabs/openthread-hardware

## To resolve

Connect to Local IPv4 LAN:

https://groups.google.com/forum/#!msg/openthread-users/38ladIxYDs4/RyiwIO0QDAAJ

https://github.com/openthread/ot-br-posix/issues/334
