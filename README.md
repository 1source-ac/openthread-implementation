# openthread-implementation

Adapted from https://openthread.io/codelabs/openthread-hardware.

## Prerequisites

Initial setup:
```
git clone --recursive https://github.com/openthread/openthread.git
cd openthread
sudo ./script/bootstrap
sudo ./bootstap

# build daemon & control cli
make -f src/posix/Makefile-posix DAEMON=1
```

## Building Network Co-Processor (NCP) for NRF52840 Dongle

```
# nrf52840 RCP
make -f examples/Makefile-nrf52840 clean
make -f examples/Makefile-nrf52840 JOINER=1 USB=1 BOOTLOADER=1
cd output/nrf52840/bin
arm-none-eabi-objcopy -O ihex ot-rcp ot-rcp.hex
```

Flash using nrfConnect application.

To understand the inner workings see here: https://openthread.io/platforms/co-processor

### Resources
https://github.com/openthread/openthread/tree/master/examples/platforms/nrf528xx/nrf52840#usb-cdc-acm-support

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
