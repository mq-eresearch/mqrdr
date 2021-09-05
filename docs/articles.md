---
layout: home
nav_order: 3
---

# Articles

- [List (my) articles](#list-my-articles)
- [Search (my) articles](#search-my-articles)

## 1. List (my) articles

{% highlight python %}
mqrdr.articles.list_private_articles(token, page=1, page_size=10, impersonated_id=None)
{% endhighlight %}

Returns a list of articles belonging to the current user, including published and private articles

**Options**

- _token_ : Repository authorization token (string, required)
- _page_ : Page number. Used for pagination with page_size (integer, optional, default = 1)
- _page_size_ : The number of results included on a page. Used for pagination with page (integer, optional, default = 10)
- _impersonated_id_ : Account ID of user being impersonated (integer, optional, only usable by admin accounts)

**Example**

{% highlight python %}
articles = mqrdr.articles.list_private_articles(token)
print(articles)

[{'defined_type_name': 'dataset',
'handle': '',
'url_private_html': 'https://figshare.com/account/articles/14450157',
'timeline': {},
'url_private_api': 'https://api.figshare.com/v2/account/articles/14450157',
'url_public_api': 'https://api.figshare.com/v2/articles/14450157',
'id': 14450157,
'doi': '',
'thumb': '',
'title': 'My Astro dataset',
'url': 'https://api.figshare.com/v2/account/articles/14450157',
'defined_type': 3,
'resource_title': None,
'url_public_html': 'https://mq.figshare.com/articles/dataset/_/14450157',
'resource_doi': None,
'published_date': None,
'group_id': 35027},
{'defined_type_name': '',
'handle': '',
'url_private_html': 'https://figshare.com/account/articles/14417807',
'timeline': {},
'url_private_api': 'https://api.figshare.com/v2/account/articles/14417807',
'url_public_api': 'https://api.figshare.com/v2/articles/14417807',
'id': 14417807,
'doi': '',
'thumb': '',
'title': 'Untitled Item',
'url': 'https://api.figshare.com/v2/account/articles/14417807',
'defined_type': 0,
'resource_title': None,
'url_public_html': 'https://mq.figshare.com/articles/dataset/_/14417807',
'resource_doi': None,
'published_date': None,
'group_id': 35027}]

{% endhighlight %}
