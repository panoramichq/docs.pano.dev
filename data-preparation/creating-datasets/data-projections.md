---
description: Coming Soon...
---

# Data Projections

Sometimes there is data that is structured in a format that isn't ideal for analytical querying. In these cases it's necessary to transform the table to a structure that can be queried correctly. Pano calls these transformations **Data Projections** and they allow you to write any raw SQL transformation that you need. Pano then pushes these projections into your data warehouse to ensure they are applied prior to any subsequent transformations. Pano includes some common examples of transformations to help you prepare your data faster. These include:

* deduplication of rows in an entity table
* Pivoting or flattening datasets that store metrics in rows instead of columns



