<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This chip is a **general-purpose protocol emulator**. Instead of implementing UART, SPI and I2C as fixed
logic, it implements a small number of programmable **protocol engines** (PEs) and lets firmware decide what
protocol they speak. A protocol is a program, not a circuit — so the chip can be taught protocols that did not
exist when it was fabricated.

Each protocol engine is a tiny, cycle-deterministic state machine with:

- a program counter and a shared instruction memory,
- an input shift register (ISR) and output shift register (OSR) for serialising/deserialising bits,
- two scratch registers for loop counters and bit counts,
- a fractional clock divider, so an engine can hit arbitrary line rates from the system clock,
- a per-instruction delay and side-set field, which is what makes bit timing exact rather than approximate.

The engines run **in parallel**. This matters because real protocols are concurrent: SPI has to drive SCK,
MOSI and CS while sampling MISO in the same bit period, and I2C has to manage open-drain SDA and SCL while
watching for a target stretching the clock. One sequential engine cannot hold several of those at once.

## How to test

No info yet.

## External hardware

No info yet
