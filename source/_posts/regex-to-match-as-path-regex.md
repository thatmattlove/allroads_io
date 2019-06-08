---
title: regex to match as_path regex
date: 2019-06-08 09:00
tags:
---

While working on input validation for my soon-to-be-released looking glass app Hyperglass, I had to find a way to validate regex with regex. Google searches returned nothing of relevance, so I built it myself. I figured this might be useful for others in the future:

## Supported lookup patterns

| Expression               |                                                 Match |
| :----------------------- | ----------------------------------------------------: |
| `_65000$`                |                                 Originated by AS65000 |
| `^65000\_`               |                                 Received from AS65000 |
| `_65000_`                |                                           Via AS65000 |
| `_65000_65001_`          |                               Via AS65000 and AS65001 |
| `_65000(_.+_)65001$`     |     Anything from AS65001 that passed through AS65000 |

## AS_PATH regex pattern for asplain

```regex
^(\^|^\_)(\d+\_|\d+\$|\d+\(\_\.\+\_\))+$
```

## AS_PATH regex pattern for asdot

```regex
^(\^|^\_)((\d+\.\d+)\_|(\d+\.\d+)\$|(\d+\.\d+)\(\_\.\+\_\))+$
```

## Notes

If using these patterns with Python as I am, you'll want to make sure you use the raw string literal flag, e.g. `r"pattern"`. For example:

```python
re_bgp_aspath_default = r"^(\^|^\_)(\d+\_|\d+\$|\d+\(\_\.\+\_\))+$"
```

This will ensure that Python doesn't interpret the regex escape characters as Python recape characters, and returns the raw string.