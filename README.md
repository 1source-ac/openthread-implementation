# openthread-implementation

## Prerequisites

Follow https://openthread.io/codelabs/openthread-hardware.

Most important steps:

Clone repo:
```
git clone --recursive https://github.com/openthread/openthread.git
cd openthread
./script/bootstrap
./bootstrap
```

Build: 
```
make -j4 -f src/posix/Makefile-posix DAEMON=1
make -f examples/Makefile-nrf52840 clean
make -f examples/Makefile-nrf52840 JOINER=1 USB=1
```

Flash:
```
cd ~/src/openthread/output/nrf52840/bin
```

To understand the inner workings see here: https://openthread.io/platforms/co-processor

## Building Network Co-Processor (NCP) for NRF52840 Dongle

Do not skip cleaning! This was a pitfall before when make arguments changed.

`make -f examples/Makefile-nrf52840 clean`

`make -f examples/Makefile-nrf52840 USB=1 BOOTLOADER=1`

Convert from ELF to HEX:

```
arm-none-eabi-objcopy output/nrf52840/bin/ot-ncp-ftd -O ihex --change-addresses 0x01000 output/nrf52840/bin/ot-ncp-ftd.hex
arm-none-eabi-objcopy output/nrf52840/bin/ot-cli-ftd -O ihex --change-addresses 0x01000 output/nrf52840/bin/ot-cli-ftd.hex
```

Flash using nrfConnect application.

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
