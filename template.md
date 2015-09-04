---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

{% include "includes/macros.md" %}

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

{% for api in apis %}

# {{ api.path }}

## Models

{% for modelName, model in api.models %}
### {{ modelName }}

Property | Type
-------- | ----
{% for propertyName, property in model.properties %}{{ propertyName }} | {{ property.type }}
{% endfor %}
{% endfor %}



{% for item in api.apis %}
## {{ item.path }}

{% for operation in item.operations %}

### Description

{{ operation.summary }}

### HTTP Request

`{{ operation.method }} {{ api.basePath }}{{ item.path }}`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
{% for parameter in operation.parameters %}{{ parameter.name }} | {{ parameter.type }} | {{ parameter.description }}
{% endfor %}

```shell
{{ curl(api.basePath + item.path, operation) }}

```

{% endfor %}

{% endfor %}



{% endfor %}
