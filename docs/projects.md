---
layout: page
title: Projects
permalink: /projects/
nav_order: 2
---

# Projects

- Projects
  - [List projects belonging to current user](#list-user-projects)
  - [Search projects belonging to the current user](#search-user-projects)
  - View a project belonging to current user
  - Create a new project
  - Update a project
  - Delete a project
- Project Articles
  - List project articles
  - View project article
  - Create project article
  - Update project article
  - Delete project article
- Project Article Files
  - List project article files
  - View project article file
  - Download project article file
  - Create project article file
  - Delete project article file
- General
  - Publish Project Article

## List user projects

{% highlight python %}
mqrdr.projects.list_projects(base_url, token, page='1', page_size='10')
{% endhighlight %}

Returns a list of projects belonging to the current user, including published and private projects

**Options**

**base_url** - The base URL of the API endpoint (string, required) \
**token** - Repository authorization token (string, required) \
**page** - Page number. Used for pagination with page_size (integer, optional, default = 1) \
**page_size** - The number of results included on a page. Used for pagination with page (integer, optional, default = 10) \
**impersonated_id** - Account ID of user being impersonated (integer, optional, only usable by RDR admin accounts)

**Example**

{% highlight python %}
projects = mqrdr.projects.list_projects(base_url, token, page='1', page_size='20')
print(projects.json())

[{'storage': 'group',
'role': 'Owner',
'id': 122958,
'title': 'GD Project to host MQ theses: 20210905-11:04',
'url': 'https://api.figsh.com/v2/account/projects/122958',
'created_date': '2021-09-05T01:04:52Z',
'published_date': None,
'modified_date': '2021-09-05T01:12:20Z'},
{'storage': 'group',
'role': 'Owner',
...
...
}
]

{% endhighlight %}

## Search user projects

{% highlight python %}
mqrdr.projects.search_user_projects(base_url, token, data)
{% endhighlight %}

Searches projects belonging to the current user

**Options**

**base_url** - The base URL of the API endpoint (string, required) \
**token** - Repository authorization token (string, required) \
**data** - Dictionary object containing project filters (object, required)

**An example of a _data_ object**

{% highlight python %}
{
"order": "published_date",
"search_for": "figshare",
"page": 1,
"page_size": 10,
"limit": 10,
"offset": 0,
"order_direction": "desc",
"institution": 2000013,
"published_since": "2017-12-22",
"modified_since": "2017-12-22",
"group": 2000013
}
{% endhighlight %}

**Impersonation**

The impersonate option must be included in the body (_data_ object) when using the search_user_projects function. Only applicable for admin accounts.

**Example**

{% highlight python %}
data = {
"search_for": 'Sample',
}
found_projects = mqrdr.projects.search_user_projects(token, data)
print(found_projects)

[
{'modified_date': '2021-05-12T02:02:16Z',
'title': 'PB01 Sample Project for RDR Testing Normal Title Normal Description (v5 23/04.....',
'url': 'https://api.figshare.com/v2/account/projects/111356',
'published_date': None,
'storage': 'group',
'role': 'Collaborator',
'created_date': '2021-04-09T10:17:03Z',
'id': 111356}
]

{% endhighlight %}

## View a user project

{% highlight python %}
mqrdr.projects.view_user_project(token, project_id, impersonated_id=None)
{% endhighlight %}

View a project belonging to the current user, including published and private projects

**Options**

- _token_ : Repository authorization token (string, required)
- _project_id_ : ID of the project (integer, required)
- _impersonated_id_ : Account ID of user being impersonated (integer, optional, only usable by admin accounts)

**Example**

{% highlight python %}
project = mqrdr.projects.view_user_project(token, '111356')
print(project)

{'description': '19/04 This test added above the line. The following text was ...',
'used_quota': 0,
'created_date': '2021-04-09T10:17:03Z',
'quota': 1073741824,
'funding_list': [],
'id': 111356,
...
...
}

{% endhighlight %}

## Create a user project

{% highlight python %}
mqrdr.projects.create_user_project(token, data)
{% endhighlight %}

Create a project belonging to the current user.

**Options**

- _token_ : Repository authorization token (string, required)
- _data_ : object containing project parameters (object, required)

**An example of a _data_ object**

{% highlight python %}
{
"title": "project title",
"description": "project description",
"funding": "string",
"funding_list": [
{
"id": 0,
"title": "string"
}
],
"group_id": 0
}
{% endhighlight %}

**Impersonation**

The impersonate option must be included in the body (_data_ object) when using the create_user_project function. Only applicable for admin accounts.

**Example**

{% highlight python %}
data = {
"title": "Large international study examining the effect of climate on tree height",
"description": "This project looks at the effect of climate on tree heights around the world",
}
new_project = mqrdr.projects.create_user_project(token, data)
print(new_project)

{'location': 'https://api.figshare.com/v2/account/projects/114204'}

{% endhighlight %}
