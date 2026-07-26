---
icon: square-info
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Adjusting Overlay Priority

{% hint style="success" %}
Technically, this is **not a bug**. It depends on your personal preference and how you want your overlays to be layered.
{% endhint %}

{% hint style="info" %}
For example, you may want your **route/highway signs** to appear **below** the **zone names**, giving the zone names higher priority and making them easier to read.
{% endhint %}

### To change the overlay order:

{% stepper %}
{% step %}
### `Open config.lua.`
{% endstep %}

{% step %}
### `Locate the category_order = {} table.`
{% endstep %}

{% step %}
### Rearrange the categories to change their loading order.
{% endstep %}

{% step %}
### Tutorial

In this example, we want the `zone_names` category to render **on top of** `underwater_routes`.&#x20;

{% hint style="info" %}
Since categories are rendered from **top to bottom**, the category placed **lower** in the `category_order` table is drawn **last** and therefore appears **above** the others.
{% endhint %}

To achieve this, simply move `zone_names` **below** `underwater_routes` in the `category_order` table, as shown in the image below.

<div align="right" data-with-frame="true"><figure><img src="../../../.gitbook/assets/before after (1).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Results

<figure><img src="../../../.gitbook/assets/Nouveau projet.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
