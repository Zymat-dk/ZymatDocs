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
    "side_a": 3,
    "side_b": 4,
    "side_c": 5.0,
    "angle_a": 36.86989764584402,
    "angle_b": 53.13010235415598,
    "angle_c": 90,
    "area": 6.0,
    "perimeter": 12.0,
    "height_a": 4.0,
    "height_b": 3.0,
    "height_c": 2.4,
    "latex": [
        "C = 90°",
        "a = 3",
        "b = 4",
        "c = \\sqrt{3^{2} + 4^{2}} = 5",
        "A = \\tan^{-1}(\\frac{3}{5}) = 36.8699°",
        "B = 180° - 90° - 36.8699° = 53.1301°",
        "Areal = \\frac{1}{2} \\cdot 3 \\cdot 4 \\cdot \\sin(90°) = 6",
        "O = 3 + 4 + 5 = 12",
        "h_a = 2 \\cdot \\frac{6}{3} = 4",
        "h_b = 2 \\cdot \\frac{6}{4} = 3",
        "h_c = 2 \\cdot \\frac{6}{5} = 2.4"
    ],
    "string": "C = 90°\na = 3\nb = 4\nc = √(3^2 + 4^2) = 5\nA = tan^(-1) (3/5) = 36.8699°\nB = 180° - 90° - 36.8699° = 53.1301°\nAreal = 1/2 * 3 * 4 * sin(90°) = 6\nO = 3 + 4 + 5 = 12\nh_a = 2 * 6/3 = 4\nh_b = 2 * 6/4 = 3\nh_c = 2 * 6/5 = 2.4",
    "points": {
        "a": [4, 0],
        "b": [0.0, 3.0],
        "c": [0, 0]
    }
}
```

## Triangle types

![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/59daf874-dbf8-40f9-bb58-310c564e1749)
![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/7cb2ca3f-e969-4eb6-bb85-183f1ffab37f)


## Triangle drawing
The API will return points for drawing the triangle in 2D.
The point `C` will almost always be at `(0, 0)`, and the point `A` will almost always have the y-coordinate `0`.

The only exception to these rules, are if a right triangle is drawn, where the angle `B` is right.
In this instance the triangle would be drawn upside down, which would look a bit weird, and it is therefore rotated.

### Default cases

![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/1fa3d392-afd1-4139-9bf7-c351e4158801)


### Special case (Right Angle B)

![image](https://github.com/Zymat-dk/ZymatDocs/assets/32793938/6fc13d79-6f11-4ebf-b880-1e6e7452a8ac)


## Supported settings
The settings that have an effect on the response of this API endpoint are:
* numeric (not yet)
* decimalCount
* commaSeparated
* calcType

