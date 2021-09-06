---
layout: page
title: Getting Started
permalink: /getting_started/
nav_order: 1
---

# Getting Started

### Install MQRDR

```bash
$ pip install mqrdr
```

### Set Base URL

In a new python script, set the base URL of the figshare API endpoint, e.g.:

```python
base_url = 'https://api.figshare.com/V2/'
```

### Set API Token

Create a variable entitled 'token' and set this to the value of your figshare API token:

```python
token = 'insertyourtokenhere'
```

Warning
{: .label .label-red }

> Due to the security nature of your API token, it is not recommended to include your token directly within your script itself. It is preferable to either import your API token from an environment variable set on your local computer, or imported from a configuration file that is explicitly kept out of version control etc
> {: .fs-5 }
