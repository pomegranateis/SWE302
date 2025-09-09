# Boundary Value Analysis

## Weight Boundaries

The weight input has three critical boundaries where behavior changes:

### Lower Boundary (around 0)
- **0** - Last invalid value (should error)
- **0.1** - First valid value (Standard package)

### Mid Boundary (around 10) 
- **10** - Last value for Standard package (no surcharge)
- **10.1** - First value for Heavy package ($7.50 surcharge)

### Upper Boundary (around 50)
- **50** - Last valid value (Heavy package with surcharge)
- **50.1** - First invalid value (should error)

## Why These Boundaries Matter

1. **0 boundary**: Tests the transition from invalid to valid weight
2. **10 boundary**: Tests the transition from Standard to Heavy package (surcharge application)
3. **50 boundary**: Tests the transition from valid to invalid weight

## Zone and Insurance Boundaries

- **Zone**: String-based, no numerical boundaries to test
- **Insurance**: Boolean, only two states (true/false) to test

## Expected Boundary Behaviors

| Weight | Expected Behavior |
|--------|------------------|
| 0 | Error: "invalid weight" |
| 0.1 | Valid, Standard package (no surcharge) |
| 10 | Valid, Standard package (no surcharge) |
| 10.1 | Valid, Heavy package (+$7.50 surcharge) |
| 50 | Valid, Heavy package (+$7.50 surcharge) |
| 50.1 | Error: "invalid weight" |