---
layout: default
title: Settings
parent: Base
---

# Settings

## numeric
`type: bool`
### Description
This setting describes the output value of calculation.
When `True`, all fractional values will be computed to numerical values.
When `False`, the exact value will be displayed.

### Examples

| Setting Value | Input |  Output  |
|---------------|-------|----------|
| `False`       | `1/3` | `1/3`    |
| `True`        | `1/3` | `0.3333` |
| `False`       | `√2`  | `√2`     |
| `True`        | `√2`  | `1.4142` |
| `False`       | `2`   | `2`      |
| `True`        | `2`   | `2`      |

## decimalCount
`type: int`
### Description
This setting describes the amount of decimals to be displayed.

### Examples

| Setting Value | Input   |  Output  |
|---------------|---------|----------|
| `0`           |`0.3333` | `0`      |
| `0`           |`0.5`    | `1`      |
| `1`           |`0.3333` | `0.3`    |
| `1`           |`24.35`  | `24.4`   |
| `2`           |`0.3333` | `0.33`   |
| `4`           |`0.5`    | `0.5`    |



## commaSeparated
`type: bool`
### Description
This setting describes whether to use commas og periods for decimal separation.
When `False`, the decimals are separated with periods (`.`).
When `True`, the decimals are separated with commas (`,`).
Primarily an option because of the lovely danish system.

### Examples

| Setting Value | Input   |  Output  |
|---------------|---------|----------|
| `False`       |`0.3333` | `0.3333` |
| `True`        |`0.3333` | `0,3333` |
| `False`       |`2.5`    | `2.5`    |
| `True`        |`2.5`    | `2,5`    |
| `False`       |`2.0`    | `2`      |
| `True`        |`2.0`    | `2`      |


## useDegrees
`type: bool`
### Description
This setting decides if degrees or radians should be used, when calculation trigonometric functions (`cos, sin, tan, etc.`).
When `False` radians are used, when `True` degrees are used.

### Exceptions
When calculating values for triangles (the triangle calculator) degrees are always used.
For these calculations the value of this setting is ignored, and degrees are used.

### Examples
Examples are for all non-triangle calculators.

| Setting Value | Input     |  Output  |
|---------------|-----------|----------|
| `False`       |`sin(2)`   |`0.9093`  |
| `True`        |`sin(2)`   |`0.0349`  |
| `False`       |`cos(π)`   |`-1`      |
| `True`        |`cos(π)`   |`0.9985`  |
| `False`       |`atan(0.5)`|`0.4636`  |
| `True`        |`atan(0.5)`|`26.5651` |

## calcType
`type: int`
### Description
This setting allows the user to select how many steps of the calculation they wish to include.
The options are:

0. Only the result.
1. The result and calculation.
2. The result, formula and calculation.


### Examples

| Setting Value |  Output               |
|---------------|-----------------------|
| `0`           |`a = 0.5`              |
| `1`           |`a = 2/4 = 0.5`        |
| `2`           |`a = b/c = 2/4 = 0.5`  |
| `0`           |`x = -1`               |
| `1`           |`x = (-2 ± √(2^2 - 4 * 1 * 4))/(2 * 1) = -1`|
| `2`           |`x = (-b ± √(b^2 - 4 * a * c))/(2 * a) = (-2 ± √(2^2 - 4 * 1 * 4))/(2 * 1) = -1`|
