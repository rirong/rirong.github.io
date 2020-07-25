---
layout: page
title: Timetable
permalink: /timetable
debug: False
---


<!-- 1. put debug mode -->
{% assign DEBUG = page.debug %}

{% if DEBUG %}
    The debug mode is ON.
{% endif %}
<!-- end -->


<!-- 2. get data -->
{% assign classes   = site.data.anu.classes %}
{% assign courses   = site.data.anu.courses %}
{% assign locations = site.data.anu.locations %}
{% assign semesters = site.data.anu.semesters %}
{% assign settings  = site.data.anu.settings %}
{% assign weeks     = site.data.anu.weeks %}
<!-- end -->


<!-- 3. get semester -->
{% assign year = settings.default_year %}
{% assign semester = settings.default_semester %}
{% assign now = site.time | date: "%s" | plus: 0 %}
{% assign gap = site.time.week_to_second | times: 2 %}
{% for s in semesters %}
    {% assign begin = s.begin | date: "%s" | minus: gap %}
    {% assign end   = s.end   | date: "%s" | plus: gap  %}
    {% if now > begin and now < end %}
        {% assign year     = s.year   | plus: 0 %}
        {% assign semester = s.number | plus: 0 %}
        {% assign begin = s.begin | date: "%s" %}
        {% break %}
    {% endif %}
{% endfor %}

{% if DEBUG %}
    year: {{ year }}
    semester: {{ semester }}  
    begin: {{ begin }}
{% endif %}
<!-- end -->


<!-- 4. get week -->
{% assign week = now | minus: begin | divided_by: settings.week_to_second | plus: 1 %}
{% assign closest = settings.weeks[0] | minus: week | abs %}
{% assign t = settings.weeks[0] %}
{% for w in settings.weeks %}
    {% assign distance = w | minus: week | abs %}
    {% if distance < closest %}
        {% assign closest = distance %}
        {% assign t = w %}
    {% endif %}
{% endfor %}
{% assign week = t %}

{% if DEBUG %}
    closest: {{ closest }}
    week: {{ week }}
{% endif %}
<!-- end -->


<!-- 5. put subtitle -->
## Year {{ year }}, Semester {{ semester }}, Week {{ week }} Classes
<!-- end -->


<!-- 6. put table -->
<table style="text-align: center">
    <!-- 6.1 put header -->
    <tr>
        <th></th>
        {% for w in settings.weekdays %}
        <th>{{ w }}</th>
        {% endfor %}
    </tr>
    <!-- 6.2 put body -->
    {% for h in settings.hours %}
        {% assign with_class = false %}
        {% for c in classes %}
            {% if c.year == year and c.semester == semester and c.hour == h  %}
                {% assign with_class = true %}
                {% break %}
            {% endif %}
        {% endfor %}
        <!-- hour with class -->
        {% if with_class %}
            <tr>
                <th>{{ h }}</th>
                {% for w in settings.weekdays %}
                <td>
                    {% for c in classes %}
                        {% if c.year == year and c.semester == semester and c.weekday == w and c.hour == h and c.weeks contains week %}
                            <!-- class -->
                            {% for crs in courses %}
                                {% if crs.id == c.cid %}
                                    {% if crs.link %}
                                        {% assign link = crs.link %}
                                    {% else %}
                                        {% assign link = settings.default_link %}
                                    {% endif %}
                                    <a href="{{ link }}">{{ crs.abbreviation }}</a><br/>
                                {% endif %}
                            {% endfor %}
                            <!-- location -->
                            {% for l in locations %}
                                {% if l.id == c.lid %}
                                    {% assign location = "@" | append: l.id %}
                                    {% if c.room %}
                                        {% assign location = location | append: "-" | append: c.room %}
                                    {% endif %}
                                    <a href="{{ l.link }}">{{ location }}</a><br/>
                                {% endif %}
                            {% endfor %}
                            <!---->
                        {% endif %}
                    {% endfor %}
                </td>
                {% endfor %}
            </tr>
        <!---->
        {% endif %}
    {% endfor %}
</table>
<!-- end -->


<!-- 7. put subtitle -->
## Courses
<!-- end -->


<!-- 8. put table -->
<table style="text-align: center">
    {% for s in semesters %}
    <tr style="background-color: white">
        <!-- 8.1 put header -->
        {% if s.number == "1" %}
            {% assign year = s.year %}
        {% else %}
            {% assign year = nil %}
        {% endif %}
        <th style="background-color: white">{{ year }}</th>
        <th style="background-color: white">{{ s.number }}</th>
        <!-- 8.2 put body -->
        {% for c in courses %}
            {% if c.year == s.year and c.semester == s.number %}
                {% case c.type %}
                    {% when "compulsory" %}
                    <td style="background-color: darkgray">
                    {% when "professional" %}
                    <td style="background-color: lightgray">
                    {% else %}
                    <td style="background-color: white">
                {% endcase %}
                {{ c.id }}<br/>{{ c.name }}</td>
            {% endif %}
        {% endfor %}    
    </tr>
    {% endfor %}
</table>
<!-- end -->


<!-- 9. put debug mode -->
{% assign DEBUG = page.debug %}

{% if DEBUG %}
    The debug mode is ON.
{% endif %}
<!-- end -->
