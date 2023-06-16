---
layout: default
title: Modules
parent: Database
---
# Modules in DB

All metadata about each module is stored in the database, so each module can be shown on the dashboard page and have a correct link. 



- [Modules in DB](#modules-in-db)
  - [name](#name)
    - [Description](#description)
  - [slug\_name](#slug_name)
    - [Description](#description-1)
  - [description](#description-2)
    - [Description](#description-3)
  - [subjects](#subjects)
    - [Description](#description-4)
  - [level](#level)
    - [Description](#description-5)
  - [institution](#institution)
    - [Description](#description-6)
  - [is\_premium](#is_premium)
    - [Description](#description-7)
  - [is\_active](#is_active)
    - [Description](#description-8)
- [Update DB from file](#update-db-from-file)
- [JSON format in modules.json](#json-format-in-modulesjson)

## name
`Type: CharField`
`Max length: 255`
`Can be blank: no`
`Can be null: no`

### Description
This contains the publicly shown name for each module. Special chars and `æøå` are allowed. 

## slug_name
`Type: CharField`
`Max length: 255`
`Can be blank: no`
`Can be null: no`

### Description
Identifier used internally to fetch the correct url. This **MUST** be the same as the one used in the `urls.py` file, otherwise the url wont be correct and the user cant reach the site. This field can't contain specialchars or `æøå`. 

## description
`Type: TextField`
`Max length: None`
`Can be blank: no`
`Can be null: no`

### Description
Contains the description for each module. This will be shown on the dashboard and possibly on the actualy site. This can contain special chars and `æøå`.

## subjects 
`Type: JSONField`
`Default: list`
`Can be blank: yes`
`Can be null: yes`

### Description
Contains the connected subjects for the module in a list, as json format. Each module must be a lowercase string. 

## level
`Type: CharField`
`Max length: 255`
`Can be blank: yes`
`Can be null: yes`

### Description
Contains the level for the subject. It's a CharField to allow for custom levels such as: `A-C` or `B&C`, but also allows simple level (`A`, `B`, `C`). Must be uppercase.

## institution
`Type: CharField`
`Max length: 255`
`Can be blank: yes`
`Can be null: yes`

### Description
Contains the institution. Only set this if the module is exclusive to one or few institutions, but not all. Must be uppercase. 

## is_premium
`Type: BooleanField`
`Default: False`

### Description
If the module is premium only or not. 

## is_active
`Type: BooleanField`
`Default: False`

### Description
If the module is curretly active. This could possible allow bug testers to try a module, before the public has access.

# Update DB from file 
The entire Modules table is loaded from the `modules.json` file located in `pages/fixtures`. This allows the db to be centralized and in VCS. To update the local DB, from the file, the following command can be run.
```bash
./run manage loaddata module
```

# JSON format in modules.json
The modules require a specific format in the json file. If the field is allowed to be blank in the db, it can also be blank in this file (i.e. not exist). Below is an example of a module. 
```json
[
  {
    "model": "pages.Module", // dont change
    "pk": 1, // increment by 1
    "fields": {
      "name": "Andengradsløsning",
      "slug_name": "quadratic",
      "description": "Løsning af andengradsligninger",
      "subjects": [
        "matematik"
      ],
      "level": "A-C",
      "is_premium": false,
      "is_active": true
    }
  }
]

```