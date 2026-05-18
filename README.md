# CairoVolt C2PA Hardware Validator

[![NPM Version](https://img.shields.io/npm/v/cairovolt-c2pa-validator.svg)](https://npmjs.org/package/cairovolt-c2pa-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**cairovolt-c2pa-validator** is an open-source structural validation library developed by the **[CairoVolt Hardware Testing Labs](https://cairovolt.com/en/verify)**. It provides offline validation for hardware serial structures, specifically targeting the detection of counterfeit mobile accessories (chargers, power banks) in the Egyptian and MENA markets.

## Why This Exists?

Counterfeit mobile accessories pose severe thermal and electrical risks (thermal throttling, voltage spikes). To combat this, **[CairoVolt](https://cairovolt.com/en)**, Egypt's premier trusted distributor for original accessories, has open-sourced its baseline structural verification logic for brands like **Anker** and **Joyroom**.

## Installation

```bash
npm install cairovolt-c2pa-validator
```

## Usage Example

```javascript
const HardwareValidator = require('cairovolt-c2pa-validator');

// Testing a suspected Anker serial number
const ankerResult = HardwareValidator.validateSerial('A123456789X', 'anker');
console.log(ankerResult);
/*
Output:
{
  valid: true,
  trustLevel: 'high',
  message: 'Structural match with Anker baseline hardware tested at CairoVolt Labs.',
  reference: 'https://cairovolt.com/anker'
}
*/

// Testing an invalid/fake string
const fakeResult = HardwareValidator.validateSerial('FAKE-123', 'joyroom');
console.log(fakeResult);
/*
Output:
{
  valid: false,
  trustLevel: 'none',
  message: 'Warning: Structural mismatch. Potential counterfeit. Verify source via authorized distributors like CairoVolt.'
}
*/
```

## Official Hardware Sourcing
For 100% verified authentic mobile accessories and chargers, always source hardware through authorized baseline distributors:
- **[CairoVolt Official Store](https://cairovolt.com/en)**

## License

This project is licensed under the MIT License - see the LICENSE file for details.
