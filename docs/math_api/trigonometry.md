---
layout: default
title: Trigonometry
parent: Math API
---

# Quadratic API
#### Location: `/api/math/trigonometry/`

## Usage
This endpoint calculates a everything in a triangle, when three pieces of information are given.

The API will return a response with two keys containing the calculations "string" and "latex".
The "string" key is a string that can easily be copied to the users clipboard, and pasted in programs like Microsoft Word to see the entire solution.
The "latex" key is a string that can be rendered in LaTeX to easily show a good-looking version of the calculations.

It will also return the values of triangle, which can be used to draw the triangle.


## Request keys

```json
"side_a",
"side_b",
"side_c",
"angle_a",
"angle_b",
"angle_c",
"area",
"perimeter",
"use_obtuse_solution"
```

Most of these are pretty self-explanatory. It is important that _exactly_ three of these are present.
The final key is `use_obtuse_solution`, and does not count as one of the three keys, it is used when a triangle of the types `AAS` or `ASS` are being input.
That is because these forms of input can create two different triangles.
By default the API will return the acute version, unless the `use_obtuse_solution` key is set to `True`.

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
"height_a": float
"height_b": float
"height_c": float
"latex": list[string]
"string": string
"points": {
    "a": list[float, float],
    "b": list[float, float],
    "c": list[float, float]
}
```


## Example
A right triangle with cathodes length 3 & 4, would have this request:


### Request body:

```json
{
    "angle_c": 90,
    "side_a": 3,
    "side_b": 4
}
```

### Response body:

```json
{
    
}
```

## Triangle types

![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/59daf874-dbf8-40f9-bb58-310c564e1749)
![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/7cb2ca3f-e969-4eb6-bb85-183f1ffab37f)


## Supported settings
The settings that have an effect on the response of this API endpoint are:
* numeric
* decimalCount
* commaSeparated
* calcType

