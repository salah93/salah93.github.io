---
layout: post
category : python
tagline:
tags : [python, intro, debugging]
---
{% include JB/setup %}

Debugging in python is sweet and easy.

+ install packages

```
pip install pdbpp ipdb
```

+ set trace point

```
import ipdb; ipdb.set_trace()
import pdb; pdb.set_trace()

```

+ debug from beginning of file

```
python -m ipdb run.py
```

