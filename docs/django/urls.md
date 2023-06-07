---
layout: default
title: URLs
parent: Django
---

# `pages`-app
The pages-app handles the following URL endpoints:

* `/`

This handles all generic pages - including frontpage, dashboard, profile etc. 

# `up`-app
The up-app handles uptime checks for the Redis cache and has the following endpoint: 

* `up/`

# `api`-app
This handles all API calls sent from the frontend, include doing the nessesary calculations and data manipulation. It currently controls the following endpoint:

* `api/`

In the future this will be further divided into subsections about the different subjects. 

# `config`-app
This is the parent app, which controls the URL endpoints for the entire project. It currently controls auth URLs:

* `accounts/google/login/`
* `accounts/google/login/callback/`
* `logout/`

Deprecated:

* `accounts/logout/` 

# Chem, Math, Physics
These only control their respective endpoints (i.e. math controls `math/` etc) and will only control these. 