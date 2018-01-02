# Wholesale Configuration / Shopify Open Source
Version: 1.0.2
Wholesale setup is perfect for merchants who are looking to sell large scale to specific tiers. This will help to walk you through different
setups.


## Getting Started

We are using the following:
* [Bold Customer Pricing](http://apps.shopify.com/customer-pricing?ref=micainteractive) - most other wholesale apps work well Bold just has great support.
* In our case the tag we used for our wholesale app was 'customer'. If you are using another tag, please change all instances of 'customer' to new tag.
* Theme Liquid
* Javascript
* We assume your theme is Sectioned


# Force Registration
This forces all visitors to register and be logged in (and tagged) before they can start browsing the site.
Issue fix: Sometimes the redirect forces you to skip Shopify's native captcha, we have fixed and updated the code.

**Scenario:**
You have an existing store selling energy drinks. You'd like to hide to most users who google your brand or visit your site that you also sell wholesale products. You also want to focus on handpicking who gets to become a wholesaler and who doesn't.

## Instructions

* Duplicate your theme (always backup theme)
* Between the <head> and </head> of the theme.liquid file add [Challenge](https://github.com/mikhailarden/Shopify-OpenSource/blob/master/Wholesale%20Configuration/Challenge)

###Step #2 (Optional)
Creating a "waiting page". This is great for before you tag your customers to show a screen where they can be told that you got their request and will alert them as soon as they are tagged.

* Create a page called 'for-review'
* Replace  {{ page.content }} with the file [For Review](https://github.com/mikhailarden/Shopify-OpenSource/blob/master/Wholesale%20Configuration/For%20Review)
* Wrap all of your code found in the templates folder in

```
{% if customer.tags contains 'Wholesale' %}

//// REPLACE ME --- The code within the template goes here.

{%else%}

{%include 'for-review'%}

{%endif%}
```
