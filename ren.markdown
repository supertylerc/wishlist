---
layout: default
title: Tyler's Wishlist
enable_charities: false
---

<div class="center">
<a href="https://wish.tylerc.me/tyler">Tyler</a> | <a href="https://wish.tylerc.me/ren">Ren</a> | <a href="https://wish.tylerc.me/family">Family</a>
</div>

* TOC
{:toc}

{% if page.enable_charities == true %}
### Charities ###
{% for c in site.data.charities %}

<div class="tile" markdown="1">
#### {{ c.title | smartify }} ####

{% if c.image %}![Image for {{ c.title | smartify }}]({{ c.image }}){% endif %}

<span>[[Donate]({{ c.link }})]</span>
</div>
{% endfor %}
{% endif %}

{% for range in site.data.wishes %}
### {{ range[0] | replace:"lt","<" | replace:"gt",">" }} ###

{% assign items = range[1] | sort: 'price' %}
{% for w in items %}{% unless w.for != "ren" (w.bought or w.hidden) %}

<div class="tile" markdown="1">
#### {{ w.title | smartify }} {% if w.price %}<span style="white-space:nowrap">{**{{ site.data.currency_symbol }}{{ w.price }}** {{ site.data.currency }}}</span>{% endif %} ####

{% if w.image %}![Image for {{ w.title | smartify }}]({{ w.image }}){% endif %}

{% if w.link %}
<span>{% for l in w.link %}[[{{ l[0] | replace:"_"," " | capitalize }}]({{ l[1] }})]{% if forloop.length > 1 and forloop.last == false %} / {% endif %}{% endfor %}</span>
{% endif %}
</div>
{% endunless %}{% endfor %}
{% endfor %}
