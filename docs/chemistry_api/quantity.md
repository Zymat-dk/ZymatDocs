---
layout: default
title: Quantity Calculator
parent: Chemistry API
---

# Quantity Calculator API
### Location: `/api/chemistry/quantity/`

## Usage
This endpoint will calculate amounts of substance in chemical reactions.
It automatically balances the reaction and provides the correct molar mass.

This process has two steps, so the API must be called twice to complete the calculation.
The first time the API is called the only keys that must be suplied are `reactants` and `products`.
These can be suplied as a string where each reactant and product is separated by a "+" or as a list, where each reactant and product is its own element.

The endpoint will always return exactly two elements.
One is a 2D list, representing the table used for calculating the amount of substance.
The other is a string of this table, separated by \t and \r\n, so it can easily be copied into Microsoft Excel, Google Sheets or another program that supports tables.

The 2D list will be returned under the name `table`, and the string will be returned as `string`.

If only the `reactants` and `products` keys are supplied, the endpoint will return a table with a few empty cells.

## Example of step 1

### Request body:

```json
{
    "reactants": "H2 + Cl2",
    "products": "HCl"
}
```

### Response body:

```json
{
    "table": [
        ["Stof", "Koefficient", "Stofmængde", "Molarmasse", "Masse"],
        ["H₂", "1", "", "2.016", ""],
        ["+Cl₂", "1", "", "70.9", ""],
        ["->HCl", "2", "", "36.458", ""]
    ],
    "string": "Stof\tH₂\t+Cl₂\t->HCl\r\nKoefficient\t1\t1\t2\r\nStofmængde\t\t\t\r\nMolarmasse\t2.016\t70.9\t36.458\r\nMasse\t\t\t\r\n"
}
```

When step one has been completed, a larger request can be sent.
This requests should contain all the infomation needed to populate the remaining cells.
Here there are some additional keys that must be supplied.
`known_mol` or `known_mass` may be supplied to tell the endpoint how much of a substance we know will be in the reaction.
Only one of these keys may be provided, as the system will become overdefined if both are present.

To tell the endpoint which substance has the specified amount the `known_value_index` key must be provided.

## Example of step 2

### Request body:

```json
{
    "reactants": ["H₂", "+Cl₂"],
    "products": ["->HCl"],
    "known_value_index": 0,
    "known_mol": 2
}
```

### Response body:

```json
{
    "table":[
        ["Stof", "Koefficient", "Stofmængde", "Molarmasse", "Masse"],
        ["H₂", "1", "2", "2.016", "4.032"],
        ["+Cl₂", "1", "2", "70.9", "141.8"],
        ["->HCl", "2", "4", "36.458", "145.832"]
    ],
    "string": "Stof\tH₂\t+Cl₂\t->HCl\r\nKoefficient\t1\t1\t2\r\nStofmængde\t2\t2\t4\r\nMolarmasse\t2.016\t70.9\t36.458\r\nMasse\t4.032\t141.8\t145.832\r\n"
}
```


## Additional information
The `coefficients` key may also be provided to override the automatically balanced coefficients, and is required if the server can not automaticaly balance the reaction.

Example:

```json
{
    "reactants": ["H₂", "+Cl₂"],
    "products": ["->HCl"],
    "known_value_index": 0,
    "known_mol": 2,
    "coefficients": [1, 1, 2]
}
```

## Supported settings
The settings that have an effect on the response of this API endpoint are:
* decimalCount
* commaSeparated

