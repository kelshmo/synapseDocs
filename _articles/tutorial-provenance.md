---
title: Track your work with Provenance
layout: article
excerpt: 
category: in-practice
---

{intro}
## {top header}

```
record <- synGetProvenance() can be used with synStore(., activity = record)

```
You can also get it and reset it: 
```
library("synapser")
synLogin()
prov <- synGetProvenance("syn23564049")
synSetProvenance("syn23564052", prov)
```
## {}

Extracting synIds to use in other records:
```
library("synapser")
library("tidyverse")
synLogin()
id <- "syn23564049"
foo <- synGetProvenance(id)
get_obj  <- foo$get("used")
used <- map_if(
  get_obj,
  ~!.$wasExecuted,
  ~ paste0(.$reference$targetId, ".", .$reference$targetVersionNumber),
  .else = ~ NULL
)
unlist(used)
```