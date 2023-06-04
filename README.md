# Zymat Docs 

## Writing about a completely new subject
If you want to write docs about a completely new subject (eg. database, a new api, fronend etc) you need to create a new folder with the corrosponding name. This cound be `db`. Always create the folder names in snake_case. The same goes for file names.

Create an `index.md` file with the following contents:
```md
---
layout: default
title: Chemistry API
has_children: true
nav_order: 4
---
```

Never change the `layout`. Title can be changed to what is needed - no case requirements. `has_children` only needs to be true if subpages are needed to properly document the feature. `nav_order` needs to be changed to the a new value.

## Writing docs (sub-pages)
Create a file with the file name of the feature to be documented. The header of the file has the following. 
```md
---
layout: default
title: Integral
parent: Math API
---
```
`layout` never changes. The title changes as needed. `parent` is the title of the parent page, completely unchanged. 