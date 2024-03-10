---
tags:
  - material
---

# Code visualization

## Highlight inline code

The `#!python range()` function is used to generate a sequence of numbers.

## Fenced Code Blocks

```python
import json
import re
from argparse import ArgumentParser
from collections import defaultdict
from enum import Enum

import requests

if __name__ == '__main__':

    payload = {"policies": []}
    for action_type, action_policy in POLICY_ACTION_MAP.items():
        if action_type == "link":
            # some logic with raw data for 'link'
            continue
        elif action_type == "sender":
            values = raw_data.get("from", []) + raw_data.get("domain", [])
        else:
            values = raw_data.get(action_type, [])

        if values:
            payload["policies"].append({
                "name": f"{opt.policy_prefix}_{action_type}",
                "rule": ' OR '.join(map(f'{action_type}:"{{}}"'.format, values)),
                "action": {
                    "enabled": True,
                    "action": action_policy
                }
            })
```