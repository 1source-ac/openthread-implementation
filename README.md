# openthread-implementation

## Building NCP

For dongle:

https://github.com/openthread/openthread/tree/master/examples/platforms/nrf528xx/nrf52840#usb-cdc-acm-support

Convert from ELF to HEX:

`arm-none-eabi-objcopy output/nrf52840/bin/ot-ncp-ftd -O ihex --change-addresses 0x01000 output/nrf52840/bin/ot-ncp-ftd.hex`

## Building OTBR

Building NCP:

`make -f examples/Makefile-nrf52840 BORDER_AGENT=1 BORDER_ROUTER=1 COMMISSIONER=1 UDP_FORWARD=1 USB=1`

https://openthread.io/guides/border-router/docker

https://openthread.io/guides/border-router/docker/run

## Testing

https://github.com/openthread/openthread/tree/master/examples/apps/cli
