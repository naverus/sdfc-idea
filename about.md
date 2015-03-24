---
layout: page
title: About
---
*Iterum* is an internal project that born on [Jalasoft](http://www.jalasoft.com) and it is donated to the community as an open source project by the [Jalasoft Foundation](http://fundacion-jala.org/). 

The members of the Iterum team are:

{% assign contributors = site.data.contributors %}
<ul>
{% for contributor in contributors %}
    <li>{{ contributor.name }} [{{contributor.email}}]</li>
{% endfor %}
</ul>

Additional colaborators:

* Rodrigo Vivar
* Jalasoft community