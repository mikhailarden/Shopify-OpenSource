# Structured Data / Shopify Open Source
Google Search works hard to understand the content of a page. You can help Google by providing explicit clues about the meaning of a page to Google by including structured data on the page. Structured data is a standardized format for providing information about a page and classifying the page content; for example, on a recipe page, what are the ingredients, the cooking time and temperature, the calories, and so on.

Google uses structured data that it finds on the web to understand the content of the page, as well as to gather information about the web and the world in general. For example, here is a JSON-LD structured data snippet that might appear on the contact page of the Unlimited Ball Bearings corporation, describing their contact information.

# Open Graph Data / Shopify Open Source

The Open Graph protocol enables any web page to become a rich object in a social graph. For instance, this is used on Facebook to allow any web page to have the same functionality as any other object on Facebook.

While many different technologies and schemas exist and could be combined together, there isn't a single technology which provides enough information to richly represent any web page within the social graph. The Open Graph protocol builds on these existing technologies and gives developers one thing to implement. Developer simplicity is a key goal of the Open Graph protocol which has informed many of the technical design decisions.

### Basic Metadata
To turn your web pages into graph objects, you need to add basic metadata to your page. We've based the initial version of the protocol on RDFa which means that you'll place additional <meta> tags in the <head> of your web page. The four required properties for every page are:

og:title - The title of your object as it should appear within the graph, e.g., "The Rock".
og:type - The type of your object, e.g., "video.movie". Depending on the type you specify, other properties may also be required.
og:image - An image URL which should represent your object within the graph.
og:url - The canonical URL of your object that will be used as its permanent ID in the graph, e.g., "http://www.imdb.com/title/tt0117500/".
As an example, the following is the Open Graph protocol markup for The Rock on IMDB:

```
<html prefix="og: http://ogp.me/ns#">
<head>
<title>The Rock (1996)</title>
<meta property="og:title" content="The Rock" />
<meta property="og:type" content="video.movie" />
<meta property="og:url" content="http://www.imdb.com/title/tt0117500/" />
<meta property="og:image" content="http://ia.media-imdb.com/images/rock.jpg" />
...
</head>
...
</html>

```

# Getting Started

I assume that you at least have some knowledge of liquid. A lot of the code written is for specific use cases.
Each folder contains a ReadMe which goes through how installation should take place.

### Tools to help

OpenGraph testing tool: http://opengraphcheck.com
Structured Data tool: https://search.google.com/structured-data/testing-tool/u/0/
