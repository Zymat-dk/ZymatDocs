---
layout: default
title: Trigonometry
parent: Math API
---

# Quadratic API
#### Location: `/api/math/trigonometry/`

## Usage
This endpoint calculates a solution for a quadratic that looks like this:
`ax^2 + bx + c = 0`
And the three keys are `a`, `b` and `c`.

The API will return a response with two keys containing the calculations "string" and "latex".
It will also return the three numbers "a", "b", "c" and the solutions for "x".
There will also be the coordinates of the peak of the parabola under the key "t".
The "string" key is a string that can easily be copied to the users clipboard, and pasted in programs like Microsoft Word to see the entire solution.
The "latex" key is a string that can be rendered in LaTeX to easily show a good-looking version of the calculations.

## Triangle types
![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/59daf874-dbf8-40f9-bb58-310c564e1749)
![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/7cb2ca3f-e969-4eb6-bb85-183f1ffab37f)

## Request keys

```json
"side_a",
"side_b",
"side_c", 
"angle_a", 
"angle_b", 
"angle_c", 
"ssa_is_acute",
"area", 
"perimeter" 
```

## Response keys
```json
"side_a": float 
"side_b": float
"side_c": float
"angle_a": float
"angle_b": float
"angle_c": float
"area": float
"perimeter": float
"latex": [string]
"string": string
```


## Example
The quadratic `x^2 + 2x + 1`, would have an `a` value of `1`, a `b` value of `2` and a `c` value of `1`.


### Request body:

```json
{
    
}
```

### Response body:

```json
{
    
}
```

## Supported settings
The settings that have an effect on the response of this API endpoint are:
* numeric
* decimalCount
* commaSeparated
* calcType

