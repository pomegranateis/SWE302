# Equivalence Partitioning Analysis

## Weight Input Analysis

Based on the specification: "0 < weight ≤ 10 kg (Standard)" and "10 < weight ≤ 50 kg (Heavy)", with invalid weights outside (0, 50]:

**Weight Partitions:**
- **P1: Invalid - Too Small** (weight ≤ 0)
  - Examples: -5, 0, -10.5
  - Expected: Error returned
  
- **P2: Valid - Standard Package** (0 < weight ≤ 10)
  - Examples: 1, 5.5, 10
  - Expected: No heavy surcharge applied
  
- **P3: Valid - Heavy Package** (10 < weight ≤ 50)
  - Examples: 10.1, 25, 50
  - Expected: $7.50 heavy surcharge applied
  
- **P4: Invalid - Too Large** (weight > 50)
  - Examples: 50.1, 100, 75.5
  - Expected: Error returned

## Zone Input Analysis

**Zone Partitions:**
- **P5: Valid Zones** 
  - Values: "Domestic", "International", "Express"
  - Expected: Corresponding base fees ($5, $20, $30)
  
- **P6: Invalid Zones**
  - Examples: "Local", "domestic" (lowercase), "", "unknown"
  - Expected: Error returned

## Insurance Input Analysis

**Insurance Partitions:**
- **P7: Insurance Requested** (insured = true)
  - Expected: 1.5% of (base fee + heavy surcharge) added to total
  
- **P8: No Insurance** (insured = false)
  - Expected: No insurance cost added

## Why These Partitions?

1. **Weight partitions** are based on the business rules that define different behaviors for different weight ranges
2. **Zone partitions** distinguish between valid zones (which have defined base fees) and invalid ones
3. **Insurance partitions** represent the boolean choice that affects the final calculation