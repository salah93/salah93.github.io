---
layout: post
category : python
tagline:
tags : [git, hooks, pre-commit]
---
{% include JB/setup %}

[Pre-commit](https://pre-commit.com/#intro) hooks allow you to enforce rules in a repo.

## how they work
+ contributor makes change
+ contributor commits changes
+ before the commit is registered, the pre-commit hooks are run
+ if those hooks fail, the commit is not allowed
+ if they pass the commit is allowed


## usage
After installing the pre-commit package `pip install pre-commit`, you need to run `pre-commit install`.

Now all hooks will run before each commit.

## using hooks
create a file `.pre-commit-config.yaml` in the top level directory.

the yaml file is equivalent to the following json
```json
{
    "repos": [
        {
            "repo": "https://github.com/pre-commit/pre-commit-hooks",
            "refv": "v1.2.3",
            "hooks": [
                {
                    "id": "flake8"
                }
            ]
        }
    ]
}
```

this file will clone each repo at the tag you specify with "refv" and run the hooks with the id you specify

there are [a lot more config options](https://pre-commit.com/#plugins) than the ones shown here.

## creating hooks
To create a hook, create a file called `.pre-commit-hooks.yaml`

the yaml file is equivalent to the following json

```json
[
    {
        "id": "flake8",
        "name": "python flake8 linter",
        "entry": "flake8",
        "language": "python"
    }
]
```

For each hook, we define an id, name, entry, and language.

+ id -> id that end-users will reference to use hooks
+ name -> what appears during execution
+ entry -> command to run
+ language -> tells pre-commit how to install

There are more options [here](https://pre-commit.com/#new-hooks).

```
