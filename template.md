---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

{% include "includes/macros.md" %}
{% include "content.md" %}

# Introduction

{{ introduction() }}

{% for api in apis %}

# {{ api.path }}

## Models

{% for modelName, model in api.models %}
### {{ modelName }}

Property | Type | Description
-------- | ---- | -----------
{% for propertyName, property in model.properties %}{{ propertyName }} | {{ property.type }} | {{ modelDescription(modelName, propertyName) }}
{% endfor %}
{% endfor %}



{% for item in api.apis %}
## {{ item.path }}

{{ pathDescription(item.path) }}

{% for operation in item.operations %}

### {{ operation.method }}

```shell
{{ curl(api.basePath + item.path, operation) }}

```

{{ operation.summary }}

#### HTTP Request

`{{ operation.method }} {{ api.basePath }}{{ item.path }}`

{{ methodDescription(item.path, operation.method) }}

#### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
{% for parameter in operation.parameters %}{{ parameter.name }} | {{ parameter.type }} | {{ parameter.description }}
{% endfor %}

{% endfor %}

{% endfor %}



{% endfor %}
