---
layout: default
title: Quantity Calculator
parent: Chemistry API
---

# Quantity Calculator API
### Location: `/api/chemistry/molarmass/`

## Usage
This endpoint will calculate the molarmass of stubstances. 
It provides the correct molarmass for each of the elements sent to the endpoint. 

When the API is called, the only key required is the `substances` key, which contains a string with elements, seperated with a `+`. 

If succesful, the API will always return two elements. A `table` key, which contains a 2D list. 
Each seperate list in the 2D list, contains an element and the corrosponding molarmass. 
The first list is always contains the titles for the element and the molarmass. 
The last elemtent is the sum of all the other elements molarmass.

## Example 

### Request body:

```json
{
    "substances": "H2 + Cl2"
}
```

### Response body:

```json
{
    "table": [
        ["Stof", "Molarmasse"],
        ["H₂", "2.016"],
        ["Cl₂","70.9"],
        ["Sum", "72.916"]
    ],
    "string": "Stof\tMolarmasse\t\r\nH₂\t2.016\tg/mol\r\nCl₂\t70.9\tg/mol\r\nSum\t72.916\tg/mol\r\n"
}
```


## Supported settings
The settings that have an effect on the response of this API endpoint are:
* decimalCount
* commaSeparated