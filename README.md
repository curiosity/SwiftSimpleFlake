# SwiftSimpleFlake
================

Generates unique ids consisting of 41 bits of time followed by 23 bits of random.

Configurable epoch is the default reference date of 2001-01-01T00:00:00.000Z.

Use
---
Generate an id using current time and a random sequence number:
```swift
let flake = SimpleFlake()           // SimpleFlake
flake.toString(encoding: .binary)   // 11101000001110001101000011110111011010100001011000011111001111
flake.toString(encoding: .hex)      // 3a0e343dda8587cf
flake.toString(encoding: .base10)   // 4183338544137603023
```

Generate an id using deterministic time and sequence:
```swift
let date = Date(timeIntervalSinceReferenceDate: 501098400)  // Nov 17, 2016, 12:00 PM
let seed: UInt64 = 123456789                                // 123456789
let flake = SimpleFlake(date: date, seedInt: seed)          // SimpleFlake
```

Configuration (default values shown):
```swift
SimpleFlake.epoch = Date(timeIntervalSinceReferenceDate: 0)
SimpleFlake.timebits = 41
```
