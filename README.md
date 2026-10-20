# I2C Library for Go on Linux

A lightweight Go library for accessing I²C devices on Linux using the `I2C_RDWR` ioctl.

## Features

- Supports combined I²C transactions with multiple messages.
- Supports read and write operations.
- Supports 7-bit and 10-bit device addresses.
- Uses the Linux I²C device interface (`/dev/i2c-*`).
- No external dependencies beyond Go and `golang.org/x/sys/unix`.

## Requirements

- Linux with I²C support enabled in the kernel.
- Access to the appropriate `/dev/i2c-*` device.
- Go.

## License

MIT License

Author: Reiner Pröls

© Copyright Reiner Pröls, 2026–2027
