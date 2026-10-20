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

## Usage

```go
### Example

```go
package main

import (
    "fmt"

    "github.com/bytemystery-com/i2c"
)

func main() {
    bus, err := i2c.NewI2c(1) // /dev/i2c-1
    if err != nil {
        fmt.Println(err)
        return
    }
    if bus == nil {
        return
    }

    dev, err := i2c.NewI2cDevice(I2C_ADDR, bus)
    if err != nil {
        fmt.Println(err)
        return
    }

    data := make([]i2c.I2cData, 2)

    // Write register address.
    data[0].Mode = i2c.I2c_write
    data[0].Data = []byte{REGISTER_ADDR}

    // Read one byte.
    data[1].Mode = i2c.I2c_read
    data[1].Data = make([]byte, 1)

    if err := dev.Transfer(data); err != nil {
        fmt.Println(err)
        return
    }

    fmt.Printf("Data: %v\n", data[1].Data[0])
}
```

## License

MIT License

Author: Reiner Pröls

© Copyright Reiner Pröls, 2026–2027
