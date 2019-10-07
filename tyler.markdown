---
layout: default
title: Tyler's Wishlist
enable_charities: false
---

[Tyler](https://wish.tylerc.me/tyler) | [Ren](https://wish.tylerc.me/ren) | [Family](https://wish.tylerc.me/family)

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

{% for w in range[1] if w.for == 'tyler' %}{% unless w.bought or w.hidden %}

<div class="tile" markdown="1">
#### {{ w.title | smartify }} {% if w.price %}<span style="white-space:nowrap">{**{{ w.price }}**}</span>{% endif %} ####

{% if w.image %}![Image for {{ w.title | smartify }}]({{ w.image }}){% endif %}

{% if w.for %}<span>[{{ w.for | capitalize }}]</span>{% endif %}

{% if w.link %}
<span>{% for l in w.link %}[[{{ l[0] | replace:"_"," " | capitalize }}]({{ l[1] }})]{% if forloop.length > 1 and forloop.last == false %} / {% endif %}{% endfor %}</span>
{% endif %}
</div>
{% endunless %}{% endfor %}
{% endfor %}
