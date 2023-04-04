---
layout: doc
---

{%- assign default_paths = site.pages | where: "layout","doc" | map: "path"| sort -%}
{%- for path in default_paths -%}
{%- assign parts=path | split: "/" -%}
{{ parts | size }}

{%- endfor-%}