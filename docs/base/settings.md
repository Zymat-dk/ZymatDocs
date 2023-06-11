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
| --- | --- | --- |
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



## commaSeparated
`type: bool`


## useDegrees
`type: bool`


## calcType
`type: int`
