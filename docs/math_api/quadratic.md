---
layout: default
title: Quadratic
parent: Math API
---

# Quadratic API
#### Location: `/api/math/quadratic/`

## Usage
This endpoint calculates a solution for a quadratic that looks like this:
`ax^2 + bx + c = 0`
And the three keys are `a`, `b` and `c`.

The API will return a response with two keys containing the calculations "string" and "latex".
It will also return the three numbers "a", "b", "c" and the solutions for "x".
There will also be the coordinates of the peak of the parabola under the key "t".
The "string" key is a string that can easily be copied to the users clipboard, and pasted in programs like Microsoft Word to see the entire solution.
The "latex" key is a string that can be rendered in LaTeX to easily show a good-looking version of the calculations.


## Example
The quadratic `x^2 + 2x + 1`, would have an `a` value of `1`, a `b` value of `2` and a `c` value of `1`.


### Request body:

```json
{
    "a": 1,
    "b": 2,
    "c": 1,
}
```

### Response body:

```json
{
    "a": 1,
    "b": 2,
    "c": 1,
    "x": [-1],
    "t": [-1, 0],
    "string": "f(x) = x^2 + 2x + 1\nD = 2^2 - 4 * 1 * 1\nD = 0\nx = (-2 ± √(2^2 - 4 * 1 * 1))/(2 * 1)\nx = -1\nT = (-2/(2 * 1), -0/(4 * 1))\nT = (-1, 0)",
    "latex": "f(x) = x^{2} + 2x + 1\nD = 2^{2} - 4 \\cdot 1 \\cdot 1\nD = 0\nx = \\frac{-2 \\pm \\sqrt{2^{2} - 4 \\cdot 1 \\cdot 1}}{2 \\cdot 1}\nx = -1\nT = (-\\frac{2}{2 \\cdot 1}, -\\frac{0}{4 \\cdot 1})\nT = (-1, 0)"
}
```

## Supported settings
The settings that have an effect on the response of this API endpoint are:
* numeric
* decimalCount
* commaSeparated
* calcType

