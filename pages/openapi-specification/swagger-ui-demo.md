---
title: Демо Swagger UI
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: swagger-ui-demo.html
folder: openapi-specification
---

При использовании Swagger UI, вывод Swagger UI не обязательно должен быть [автономным сайтом](https://idratherbewriting.com/learnapidoc/assets/files/swagger/). Можно встроить Swagger в существующую веб-страницу. Ниже приведен встроенный экземпляр [Swagger UI](https://github.com/swagger-api/swagger-ui), показывающий файл [OpenAPI для OpenWeatherMapAPI](https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml).

Дисплей пользовательского интерфейса Swagger спроектирован так, чтобы быть отзывчивым, однако  сворачиваемые разделы в модели по-прежнему имеют недостатки переполнения в представлениях, поэтому при встраивании можно столкнуться с некоторыми проблемами.

<table>
    <thead>
    <tr><th>Name</th><th>Type</th><th>Description</th><th>Required?</th></tr>
    </thead>
    {% for parameter in site.data.swagger.paths.get.parameters %}
        {% if parameter.in == "query" %}
        <tr>
            <td><code>{{ parameter.name }}</code></td>
            <td><code>{{ parameter.type }}</code></td>
            <td>
            {% assign found = false %}
            {% for param in site.data.swagger.paths.get.parameters %}
                {% if parameter.name == param.name %}
                    {{ param.description }}
                    {% assign found = true %}
                {% endif %}
            {% endfor %}
            {% if found == false %}
                ** New parameter **
            {% endif %}
            </td>
            <td><code>{{ parameter.required }}</code></td>
        </tr>
        {% endif %}
    {% endfor %}
</table>

[🔙](swagger-ui-tutorial.html)

[Go next ➡](swaggerhub-introduction-and-tutorial.html)
