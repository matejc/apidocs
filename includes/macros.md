{% macro bodyParameters(operation) -%}
{%- for grouper, list in operation.parameters|groupby('paramType') %}
{%- if grouper == "body" %}
{%- for parameter in list %}
{%- if not loop.first %} {% endif -%}
-d {{ parameter.name }}=<value>
{%- endfor -%}
{% endif -%}
{% endfor -%}
{%- endmacro %}

{% macro queryParameters(operation) -%}
{%- for grouper, list in operation.parameters|groupby('paramType') %}
{%- if grouper == "query" %}
{%- for parameter in list %}
{%- if loop.first %}?{% endif -%}
{{ parameter.name }}=<value>
{%- endfor -%}
{% endif -%}
{% endfor -%}
{%- endmacro %}


{% macro curl(path, operation) -%}

curl "{{path}}{{ queryParameters(operation) }}" -X {{operation.method}} \
  -H "Cookie: token=<token>" {{ bodyParameters(operation) }}

{%- endmacro %}
