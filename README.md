# expand-subtemplate

Ansible role for expanding variables in a simple string based template on demand.

**License:** MIT

**Author:** Tero Niemi (https://github.com/talamus)

## Input:

| Variable             | Type   | Description                        | Example                                     |
|----------------------|--------|------------------------------------|---------------------------------------------|
| subtemplate          | string | A simple template.                 | 'Mary had a { adjective } { animal }.'      |
| subtemplate_vars     | object | Values that are used in expansion. | { 'adjective': 'little', 'animal': 'lamb' } |

## Output:

| Variable             | Type   | Description                        | Example                                     |
|----------------------|--------|------------------------------------|---------------------------------------------|
| expanded_subtemplate | string | The expanded template.             | 'Mary had a little lamb.'                   |

## Example:

```yaml
---
- hosts: all

  tasks:

  - name: Example of `expand-subtemplate`
    include_role:
      name: expand-subtemplate
    vars:
      subtemplate: 'Maijulla oli { animal } { color }'
      subtemplate_vars:
        animal: karitsa
        color: lumivalkoinen

  - debug:
      msg: 'Output: {{ expanded_subtemplate }}'
```
