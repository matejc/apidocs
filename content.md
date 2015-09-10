
{% macro introduction() -%}
Some veryyyyyyyyyyyyyyyyyyyyyyyyyyy short introduction.
{%- endmacro %}

{% macro pathDescription(path) -%}
{% if path == "/Users" %}
Some extra info about /Users route
{% endif %}
{%- endmacro %}


{% macro methodDescription(path, method) -%}
{% if path == "/Users" and method == "POST" %}
Some extra info about POST method of /Users route
{% endif %}
{%- endmacro %}


{% macro modelDescription(model, property) -%}
{% if model == "User" and property == "username" -%}
Some extra info about username property
{%- endif %}
{%- endmacro %}
