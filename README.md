# Pulumi Poetry Actions

I attempted to set up a python project using *poetry* and _best practices_ (mypy, flake8, yamllint etc.) for an infrastructure repo that manages AWS
using `pulumi` and `pulumi-aws`

In the process identified an issue with interaction between `pulumi/actions@v3` and using `poetry`. `pulumi/actions@v3` only works with `pip`. 

When running `pulumi preview` the workflow fails with a python import error.

I've not tracked down why this is the case. 

However the following attempts were made

* Install poetry in a virtual environment
* Install poetry with virtualenvs disabled in config

In the second case, the packages _must_ have installed globally, yet the import error persists.

The *workaround* was to generate the requirements file from poetry and using `pip` to install all the dependencies.
