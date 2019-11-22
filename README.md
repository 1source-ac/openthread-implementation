# openthread-implementation

## Building NCP

For dongle:

https://github.com/openthread/openthread/tree/master/examples/platforms/nrf528xx/nrf52840#usb-cdc-acm-support

Convert from ELF to HEX:

`arm-none-eabi-objcopy infile -O ihex out.hex`

## Building OTBR

https://openthread.io/guides/border-router/docker
https://openthread.io/guides/border-router/docker/run

## Testing

https://github.com/openthread/openthread/tree/master/examples/apps/cli
