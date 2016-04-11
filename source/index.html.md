---
title: SWCE API Reference

language_tabs:

toc_footers:
  - <a href='http://api.swcollectionsexplorer.org.uk'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SWCE API.

The API is a (mostly) RESTful service, with authentication handled by API tokens sent as a header or parameter on every request.

This API documentation was created with [Slate](https://github.com/tripit/slate). You can send us pull request for any changes you think should be made to these docs over on [Github](https://github.com/Thirty8Digital/swce-api-docs)

# API Endpoint

The API endpoint is:

`http://api.swcollectionsexplorer.org.uk/api/v1/`

# Formats

By default, the API returns everything in JSON. We recommend you consume this.

XML is also available on every request if you prefer it, simply append ".xml" of your endpoint.

# Rate Limiting

You can make 60 requests to the API every 60 seconds.

After this, you'll receive an `429 Too Many Requests` status.

You can check your rate limit status by reading the `X-RateLimit-Limit` and `X-RateLimit-Remaining` headers returned on every request.

# Authentication

SWCE currently only offers API tokens to allow access to the API. You can register a new API token key at our [developer portal](http://api.swcollectionsexplorer.org.uk).

SWCE requires the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer w0WlRHfwbbr4JUJygL`

Alternatively, you can make any request and append an api_token parameter:

`http://api.swcollectionsexplorer.org.uk/api/v1/sites?api_token=w0WlRHfwbbr4JUJygL`

<aside class="notice">
You must replace <code>w0WlRHfwbbr4JUJygL</code> with your personal API key.
</aside>

# Objects

## Get All Objects

```curl

curl -X "GET" "http://api.swcollectionsexplorer.org.uk/api/v1/objects" \
	-H "Authorization: Bearer w0WlRHfwbbr4JUJygL"
```

> The above command returns JSON structured like this:

```json
{
  "total": 11379,
  "per_page": 50,
  "current_page": 1,
  "last_page": 228,
  "next_page_url": "http://api.swcollectionsexplorer.org.uk/api/v1/objects?page=2",
  "prev_page_url": null,
  "from": 1,
  "to": 50,
  "data": [
    {
      "id": 1,
      "accession-loan-no": "71/1929",
      "simple-name": "door",
      "full-name": null,
      "collector-excavator": null,
      "collection-country": "England",
      ...
      "site": {
        "name": "RAMM"
      },
      "category": {
        "name": "Antiquities",
        "slug": "antiquities"
      }
    },
    ...
  ]
}
```

This endpoint retrieves all objects.

### HTTP Request

`GET objects`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
site | null | Limit results to only one site ID
since | null | Only return objects modified since this timestamp (2016-04-10 18:00:00 format)
category | null | Limit results to this category slug
per_page | 50 | The number of results per page (min 10, max 250)

<aside class="success">
Remember — all API requests must contain either an <code>api_token</code> parameter or a <code>Authorization</code> header.
</aside>

## Get a Specific Object

```curl

curl -X "GET" "http://api.swcollectionsexplorer.org.uk/api/v1/object/1" \
	-H "Authorization: Bearer w0WlRHfwbbr4JUJygL"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "accession-loan-no": "160/1999",
  "simple-name": "architectural fragment",
  "full-name": "label stop",
  "collector-excavator": "Pearce, Nan, Mrs",
  "collection-country": "England",
  "description": "This architectural fragment is shaped as a queenâs head with curly hair. It was salvaged from a demolished house in Membury, Devon, where it had been used in a 20th century fireplace. It was probably once part of the local church.",
  "mint": null,
  "medium": null,
  "geology-period": null,
  "common-name": "label stop",
  "family": null,
  ...
  "site": {
    "name": "RAMM"
  },
  "category": {
    "name": "Antiquities",
    "slug": "antiquities"
  }
}
```

This endpoint retrieves a specific object.

### HTTP Request

`GET object/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the object to retrieve

