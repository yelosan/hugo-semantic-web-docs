+++
weight = 10
title = "Semantic Web for Hugo"

images = ["https://rsc.youronly.one/img/y/Yuki_flag-300h.webp", "https://img.youronly.one/works/Yellow_Bell-02-CC_By-SA_4.0-s.webp"]
videos = ["https://www.youtube.com/watch?v=OM6XIICm_qo", "https://vimeo.com/601088734"]
+++

# Intro
**Semantic Web for Hugo** adds *structured data* and *linked data* into a [Hugo](https://gohugo.io)-powered website. Through it search engines can easily read the data of a Hugo-powered website and establish relationships between objects. This enables search engines to intelligently store information about a website and use it to increase a website's exposure in search results.

For this project, we chose to implement *Schema.org*'s Vocabulary by adding *JSON-LD* markup automatically. In areas where custom input is required, we took advantage of Hugo's shortcode feature.

Latest version: [v1.1.0: ᜐᜎᜋᜆ᜔ (salamat)](https://github.com/YourOnly-One/hugo-semantic-web/releases) released on 2012-11-15.

## History
* v1.0.0 "감사합니다 (gamsahabnida)" released on 2021-11-08.

## Features
These are the currently supported Schema.org Types:
* [Organization](#organization)
* [Person](#person)
* [WebContent](#webcontent)
* [WebSite](#website)
* [WebPage](#webpage)
* [Article](#article)
* [BlogPosting](#blogposting)
* [ImageObject](#imageobject)
* [VideoObject](#videoboject)

# Installation
## Hugo module method

> 1. In your `config` file add the following:

```toml
[module]
		[[module.imports]]
				path = "github.com/YourOnly-One/hugo-semantic-web"
```

```yaml
module:
		imports:
			- path: github.com/YourOnly-One/hugo-semantic-web
```

```json
{
	"module": {
		"imports": [
			{
				"path": "github.com/YourOnly-One/hugo-semantic-web"
			}
		]
	}
}
```

> 2. Initialize **Semantic Web for Hugo** module:

```shell
hugo mod init github.com/YourOnly-One/hugo-semantic-web
```

> 3. Add this in `/layouts/_default/baseof.html` (or whichever is appropriate):

```go-html-template
{{ $semwebcss := resources.Get "css/semweb-style.css" }}
{{ $semwebstyle := $semwebcss | resources.Minify }}
<link rel="stylesheet" href="{{ $semwebstyle.RelPermalink }}" media="all" type="text/css" />
```

> 4. Proceed to the next [step](#types).

We recommend installing the **Semantic Web for Hugo** project by taking advantage of the *Hugo module* feature. This method ensures your project will always use the latest release of **Semantic Web for Hugo**.

Follow the steps on the right (or below if viewing in mobile).

### To update
To update the **Semantic Web for Hugo** module run this while in your project's root: `hugo mod get -u github.com/YourOnly-One/hugo-semantic-web`

## git submodule method

> 1. Add this in your `config` file:

```toml
theme = ["hugo-semantic-web", "your-theme"]
```

```yaml
theme:
	- hugo-semantic-web
	- your-theme
```

```json
{
	"theme": [
		"hugo-semantic-web",
		"your-theme"
	]
}
```

> 2. In your project's root folder:

```shell
git submodule add https://github.com/YourOnly-One/hugo-semantic-web.git themes/hugo-semantic-web
```

> 3. Then initialize the **Semantic Web for Hugo** submodule:

```shell
git submodule update --init --recursive themes/hugo-semantic-web
```

> 4. Add this in `/layouts/_default/baseof.html` (or whichever is appropriate):

```go-html-template
{{ $semwebcss := resources.Get "css/semweb-style.css" }}
{{ $semwebstyle := $semwebcss | resources.Minify }}
<link rel="stylesheet" href="{{ $semwebstyle.RelPermalink }}" media="all" type="text/css" />
```

> 5. Proceed to the next [step](#types).

The *git submodule* method is our second recommendation. This method also makes it easier to update the **Semantic Web for Hugo** module.

Follow the steps on the right (or below if viewing in mobile).

### To update
While in your project's root run this command: `git submodule update --init --recursive themes/hugo-semantic-web`

## git clone method

> 1. Add this in your `config` file:

```toml
theme = ["hugo-semantic-web", "your-theme"]
```

```yaml
theme:
	- hugo-semantic-web
	- your-theme
```

```json
{
	"theme": [
		"hugo-semantic-web",
		"your-theme"
	]
}
```

> 2. In your project's root folder:

```shell
git clone https://github.com/YourOnly-One/hugo-semantic-web.git themes/hugo-semantic-web
```

> 3. Add this in `/layouts/_default/baseof.html` (or whichever is appropriate):

```go-html-template
{{ $semwebcss := resources.Get "css/semweb-style.css" }}
{{ $semwebstyle := $semwebcss | resources.Minify }}
<link rel="stylesheet" href="{{ $semwebstyle.RelPermalink }}" media="all" type="text/css" />
```

> 4. Proceed to the next [step](#types).

*git clone* is the simplest git method to add a module in your Hugo-powered project.

Follow the steps on the right (or below if viewing in mobile).

### To update
In the **Semantic Web for Hugo** folder (`cd themes/hugo-semantic-web`) run this command: `git pull`.

## Download method

> 1. Add this in your `config` file:

```toml
theme = ["hugo-semantic-web", "your-theme"]
```

```yaml
theme:
	- hugo-semantic-web
	- your-theme
```

```json
{
	"theme": [
		"hugo-semantic-web",
		"your-theme"
	]
}
```

> 2. Download the latest release [here](https://github.com/YourOnly-One/hugo-semantic-web/releases).

> 3. Extract the file in your project's `/theme/` folder, it should be: `themes/hugo-semantic-web/`

> 4. Add this in `/layouts/_default/baseof.html` (or whichever is appropriate):

```go-html-template
{{ $semwebcss := resources.Get "css/semweb-style.css" }}
{{ $semwebstyle := $semwebcss | resources.Minify }}
<link rel="stylesheet" href="{{ $semwebstyle.RelPermalink }}" media="all" type="text/css" />
```

> 5. Proceed to the next [step](#types).

We do not recommend this method. If you prefer to lock to a specific version or include **Semantic Web for Hugo** in your theme distribution, the *Hugo Module* method can do both better.

However, if this method best suits your workflow, you can follow the steps on the right (or below if viewing in mobile).

### To update
1. Check regularly the project's [repository](https://github.com/YourOnly-One/hugo-semantic-web) for updates.
1. Download the latest release [here](https://github.com/YourOnly-One/hugo-semantic-web/releases).
1. If you did not edit any of the **Semantic Web for Hugo** files, delete the `/hugo-semantic-web/` folder located in your project's `/theme/` folder.
1. Extract the latest release in `/themess/hugo-semantic-web/`.

# Types
## Organization

<aside class="notice">An organization such as a school, NGO, corporation, club, etc.

Schema.org: Thing > [Organization](https://schema.org/Organization)
</aside>

```toml
id = ""
foundingdate = ""
knowslanguages = ["", ""]
legalname = ""
slogan = ""
taxid = ""
vatid = ""
alternatenames = ["", ""]
description = ""
name = ""
sameas = ["", ""]
url = ""

[[brands]]
  id = ""
  logo = ""
  name = ""
  url = ""
  iswebsite = false
[[brands]]
  id = ""
  logo = ""
  name = ""
  url = ""
  iswebsite = false

[[founders]]
  id = ""
  name = ""
  sameas = [""]
  url = ""
[[founders]]
  id = ""
  name = ""
  sameas = [""]
  url = ""

[[images]]
  caption = ""
  url = ""
  islogo = false
[[images]]
  caption = ""
  url = ""
  islogo = false
```

```yaml
id: ''
foundingdate: ''
knowslanguages:
  - ''
  - ''
legalname: ''
slogan: ''
taxid: ''
vatid: ''
alternatenames:
  - ''
  - ''
description: ''
name: ''
sameas:
  - ''
  - ''
url: ''
brands:
  - id: ''
    logo: ''
    name: ''
    url: ''
    iswebsite: false
  - id: ''
    logo: ''
    name: ''
    url: ''
    iswebsite: false
founders:
  - id: ''
    name: ''
    sameas:
      - ''
    url: ''
  - id: ''
    name: ''
    sameas:
      - ''
    url: ''
images:
  - caption: ''
    url: ''
    islogo: false
  - caption: ''
    url: ''
    islogo: false
```

```json
{
  "id": "",
  "foundingdate": "",
  "knowslanguages": [
    "",
    ""
  ],
  "legalname": "",
  "slogan": "",
  "taxid": "",
  "vatid": "",
  "alternatenames": [
    "",
    ""
  ],
  "description": "",
  "name": "",
  "sameas": [
    "",
    ""
  ],
  "url": "",
  "brands": [
    {
      "id": "",
      "logo": "",
      "name": "",
      "url": "",
      "iswebsite": false
    },
    {
      "id": "",
      "logo": "",
      "name": "",
      "url": "",
      "iswebsite": false
    }
  ],
  "founders": [
    {
      "id": "",
      "name": "",
      "sameas": [
        ""
      ],
      "url": ""
    },
    {
      "id": "",
      "name": "",
      "sameas": [
        ""
      ],
      "url": ""
    }
  ],
  "images": [
    {
      "caption": "",
      "url": "",
      "islogo": false
    },
    {
      "caption": "",
      "url": "",
      "islogo": false
    }
  ]
}
```

### Configurable parameters
* `id`: <span style="color: red;">***required***</span>; format: `URL/`
* `foundingdate`: <span style="color: blue;">*optional*</span>; format: `YYYY-MM-DD`
* `knowslanguages`: <span style="color: blue;">*optional*</span>; format: [IETF BCP 47 standard](https://en.wikipedia.org/wiki/IETF_language_tag), examples: `en`, `en-PH`, `tl-Tglg`, `ko`, `ja`
* `legalname`: <span style="color: red;">***required***</span>
* `slogan`: <span style="color: blue;">*optional*</span>
* `taxid`: <span style="color: blue;">*optional*</span>
* `vatid`:<span style="color: blue;">*optional*</span>
* `alternatenames`: <span style="color: blue;">*optional*</span>
* `description` <span style="color: red;">***required***</span>
* `name` <span style="color: red;">***required***</span>
* `sameas`: <span style="color: blue;">*optional*</span>; URL to other profile/accounts
* `url` <span style="color: red;">***required***</span>; format: `URL/`
* `brands` <span style="color: blue;">*optional*</span>; repeat as needed
  * `id` <span style="color: red;">***required***</span>; format: `URL/`
  * `logo`: <span style="color: blue;">*optional*</span>; URL to logo file
  * `name`: <span style="color: red;">***required***</span>
  * `url`: <span style="color: red;">***required if***</span> `iswebsite` is `true`
  * `iswebsite`: <span style="color: blue;">*optional*</span>, default: `false`; set to `true` if Type:Brand is also a website, `Type:WebSite` will be added
* `founders` is <span style="color: blue;">*optional*</span>; repeat as needed
  * `id` <span style="color: red;">***required***</span>; format: `URL/#fragment-identifier`, URL should be Type:Person's about/bio Page
  * `name`: <span style="color: red;">***required***</span>
  * `sameas`: <span style="color: blue;">*optional*</span>; URL to other profile/accounts
  * `url`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `images` is <span style="color: red;">***required***</span>; repeat as needed
  * `caption` is <span style="color: green;">**recommended**</span>
  * `url` <span style="color: red;">***required***</span>; format: `URL/`
  * `islogo`: <span style="color: blue;">*optional*</span>; default: `false`; set to `true` if image is Type:Organization's logo

## Person

<aside class="notice">A person (alive, dead, undead, or fictional).

Schema.org: Thing > [Person](https://schema.org/Person)
</aside>

> Create a **Person** file in `/data/persons/`

```toml
id = ""
additionalnames = [""]
jobtitle = [""]
knowslanguages = [""]
taxid = ""
vatid = ""
description = ""
mainentityofpage = ""
name = ""
sameas = [""]
url = ""

[[affiliations]]
  id = ""
  name = ""
  url = ""
[[affiliations]]
  id = ""
  name = ""
  url = ""

[[brands]]
  id = ""
  logo = ""
  name = ""
  url = ""
  iswebsite = false
[[brands]]
  id = ""
  logo = ""
  name = ""
  url = ""
  iswebsite = false

[spouse]
  id = ""
  name = ""
  url = ""

[[worksfor]]
  id = ""
  name = ""
  url = ""
[[worksfor]]
  id = ""
  name = ""
  url = ""

[[images]]
  caption = ""
  url = ""
  isphoto = false
[[images]]
  caption = ""
  url = ""
  isphoto = false
```

```yaml
id: ''
additionalnames:
  - ''
jobtitle:
  - ''
knowslanguages:
  - ''
taxid: ''
vatid: ''
description: ''
mainentityofpage: ''
name: ''
sameas:
  - ''
url: ''
affiliations:
  - id: ''
    name: ''
    url: ''
  - id: ''
    name: ''
    url: ''
brands:
  - id: ''
    logo: ''
    name: ''
    url: ''
    iswebsite: false
  - id: ''
    logo: ''
    name: ''
    url: ''
    iswebsite: false
spouse:
  id: ''
  name: ''
  url: ''
worksfor:
  - id: ''
    name: ''
    url: ''
  - id: ''
    name: ''
    url: ''
images:
  - caption: ''
    url: ''
    isphoto: false
  - caption: ''
    url: ''
    isphoto: false
```

```json
{
  "id": "",
  "additionalnames": [
    ""
  ],
  "jobtitle": [
    ""
  ],
  "knowslanguages": [
    ""
  ],
  "taxid": "",
  "vatid": "",
  "description": "",
  "mainentityofpage": "",
  "name": "",
  "sameas": [
    ""
  ],
  "url": "",
  "affiliations": [
    {
      "id": "",
      "name": "",
      "url": ""
    },
    {
      "id": "",
      "name": "",
      "url": ""
    }
  ],
  "brands": [
    {
      "id": "",
      "logo": "",
      "name": "",
      "url": "",
      "iswebsite": false
    },
    {
      "id": "",
      "logo": "",
      "name": "",
      "url": "",
      "iswebsite": false
    }
  ],
  "spouse": {
    "id": "",
    "name": "",
    "url": ""
  },
  "worksfor": [
    {
      "id": "",
      "name": "",
      "url": ""
    },
    {
      "id": "",
      "name": "",
      "url": ""
    }
  ],
  "images": [
    {
      "caption": "",
      "url": "",
      "isphoto": false
    },
    {
      "caption": "",
      "url": "",
      "isphoto": false
    }
  ]
}
```

### Configurable parameters
* `id`: <span style="color: red;">***required***</span>; format: `URL/#fragment-identifier`
* `additionalnames`: <span style="color: blue;">*optional*</span>
* `jobtitle`: <span style="color: blue;">*optional*</span>
* `knowslanguages`: <span style="color: blue;">*optional*</span>; format: [IETF BCP 47 standard](https://en.wikipedia.org/wiki/IETF_language_tag), examples: `en`, `en-PH`, `tl-Tglg`, `ko`, `ja`
* `taxid`: <span style="color: blue;">*optional*</span>
* `vatid`: <span style="color: blue;">*optional*</span>
* `description`: <span style="color: blue;">*optional*</span>
* `mainentityofpage`: <span style="color: blue;">*optional*</span>; format: `URL/`; should be Type:Person's about/bio page
* `name`: <span style="color: red;">***required***</span>
* `sameas`: <span style="color: blue;">*optional*</span>; URL to other profile/accounts
* `url`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `affiliations`: <span style="color: blue;">*optional*</span>; repeat as needed
  * `id`: <span style="color: red;">***required***</span>; format: `URL/`; should be the primary website
  * `name`: <span style="color: red;">***required***</span>
  * `url`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `brands`: <span style="color: blue;">*optional*</span>; repeat as needed
  * `id`: <span style="color: red;">***required***</span>; format: `URL/`; can be a non-existent URL as long as it follows the format
  * `logo`: <span style="color: blue;">*optional*</span>; URL to brand or website logo
  * `name`: <span style="color: red;">***required***</span>
  * `url`: <span style="color: red;">***required if***</span> `iswebsite` is `true`
  * `iswebsite`: <span style="color: blue;">*optional*</span>, default: `false`; set to `true` if Type:Brand is also a website, `Type:WebSite` will be added
* `spouse`: <span style="color: blue;">*optional*</span>
  * `id`: <span style="color: red;">***required***</span>; format: `URL/#fragment-identifier`; can be a non-existent URL as long as it follows the format
  * `name`: <span style="color: red;">***required***</span>
  * `url`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `worksfor`: <span style="color: blue;">*optional*</span>; repeat as needed
  * `id`: <span style="color: red;">***required***</span>; format: `URL/`; should be the primary website
  * `name`: <span style="color: red;">***required***</span>
  * `url`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `images`: <span style="color: red;">***required***</span>
  * `caption`: <span style="color: green;">**recommended**</span>
  * `url`: <span style="color: red;">***required***</span>
  * `isphoto`: <span style="color: blue;">*optional*</span>; default: `false`; set to `true` if image is Type:Person's photo

## WebContent

<aside class="notice">WebContent is a type representing all WebPage, WebSite, and WebPageElement content. It is sometimes the case that detailed distinctions between Web pages, sites and their parts is not always important or obvious. The WebContent type makes it easier to describe Web-addressable content without requiring such distinctions to always be stated.

Schema.org: Thing > CreativeWork > [WebContent](https://schema.org/WebContent)
</aside>

There are no configurable parameters for WebContent. It relies on what is available in [WebSite](#website), [WebPage](#webpage), and [Article](#article).

## WebSite

<aside class="notice">A WebSite is a set of related web pages and other items typically served from a single web domain and accessible via URLs.

Schema.org: Thing > CreativeWork > [WebSite](https://schema.org/WebSite)
</aside>

> Add this in your `[hugo|params|config]` file:

```toml
[params]
  keywords = ["", ""]
  description = ""
  images = ["", ""]

  [params.semweb]
    org = ""
    isblog = false

    issn = ""
    acquirelicensepage = ""
    copyrightholder = ""
    copyrightnotice = ""
    creator = ""
    credittext = ""
    datefirstpublished = ""
    license = ""
    publisher = ""
    sameas = [""]

    [[params.semweb.persons]]
      person = ""
      id = ""
      name = ""
      url = ""
      description = ""
    [[params.semweb.persons]]
      person = ""
      id = ""
      name = ""
      url = ""
      description = ""
```

```yaml
params:
  keywords:
    - ''
    - ''
  description: ''
  images:
    - ''
    - ''
  semweb:
    org: ''
    isblog: false
    issn: ''
    acquirelicensepage: ''
    copyrightholder: ''
    copyrightnotice: ''
    creator: ''
    credittext: ''
    datefirstpublished: ''
    license: ''
    publisher: ''
    sameas:
      - ''
    persons:
      - person: ''
        id: ''
        name: ''
        url: ''
        description: ''
      - person: ''
        id: ''
        name: ''
        url: ''
        description: ''
```

```json
{
  "params": {
    "keywords": [
      "",
      ""
    ],
    "description": "",
    "images": [
      "",
      ""
    ],
    "semweb": {
      "org": "",
      "isblog": false,
      "issn": "",
      "acquirelicensepage": "",
      "copyrightholder": "",
      "copyrightnotice": "",
      "creator": "",
      "credittext": "",
      "datefirstpublished": "",
      "license": "",
      "publisher": "",
      "sameas": [
        ""
      ],
      "persons": [
        {
          "person": "",
          "id": "",
          "name": "",
          "url": "",
          "description": ""
        },
        {
          "person": "",
          "id": "",
          "name": "",
          "url": "",
          "description": ""
        }
      ]
    }
  }
}
```

### Configurable frontmatter parameters
* `org`: <span style="color: blue;">*optional*</span>; filename of Type:Organization in `/data/orgs/`
* `isblog`: <span style="color: blue;">*optional*</span>, default: `false`; set to true if website is also a webblog, Type `BlogPosting` is added
* `keywords`: <span style="color: blue;">*optional*</span>; site keywords
* `description`: <span style="color: green;">**recommended**</span>; site description
* `images`: <span style="color: blue;">*optional*</span>
* `issn`: <span style="color: blue;">*optional*</span>; The *International Standard Serial Number* of the publication, see [wikipedia:ISSN](https://en.wikipedia.org/wiki/International_Standard_Serial_Number)
* `acquirelicensepage`: <span style="color: blue;">*optional*</span>; URL to Page with information on how to acquire a license to re-use your materials
* `copyrightholder`: <span style="color: blue;">*optional*</span>; format: `URL/#fragment-identifier` of Type:Organization or Type:Person; fallback to Hugo default `author` param
* `copyrightnotice`: <span style="color: blue;">*optional*</span>; example: `Copyleft 🄯 CC-BY-SA 4.0 International by Yelosan Publishing, LLC.`
* `creator`: <span style="color: blue;">*optional*</span>; format: `URL/#fragment-identifier`; fallback to Hugo default `author` param
* `credittext`: <span style="color: blue;">*optional*</span>; example: `YourOnly.One (https://youronly.one)`
* `datefirstpublished`: <span style="color: blue;">*optional*</span>; format: `YYYY-MM-DD`; fallback to Hugo `.Date`
* `license`: <span style="color: blue;">*optional*</span>; URL to License Page
* `publisher`: <span style="color: blue;">*optional*</span>; format: `URL/`
* `sameas`: <span style="color: blue;">*optional*</span>; URL to other profile/accounts
* `persons`: <span style="color: blue;">*optional*</span>; repeat as needed;
  * `person`: <span style="color: blue;">*optional*</span>; filename of Type:Person in `/data/persons/`
  * `id`: <span style="color: blue;">*optional if*</span> `person` exists in `/data/persons/`; format: `URL/`
  * `name`: <span style="color: blue;">*optional if*</span> `person` exists in `/data/persons/`
  * `url`: <span style="color: blue;">*optional if*</span> `person` exists in `/data/persons/`; format: `URL/`
  * `description`: <span style="color: blue;">*optional if*</span> `person` exists in `/data/persons/`

## WebPage

<aside class="notice">A web page. Every web page is implicitly assumed to be declared to be of type WebPage, so the various properties about that webpage, such as breadcrumb may be used. We recommend explicit declaration if these properties are specified, but if they are found outside of an itemscope, they will be assumed to be about the page.

Schema.org: Thing > CreativeWork > [WebPage](https://schema.org/WebPage)
</aside>

There are no configurable parameters for Type:WebPage. The properties and related data automatically adjusts depending on the [Page Kind](https://gohugo.io/templates/section-templates/#page-kinds).

## Article

<aside class="notice">An article, such as a news article or piece of investigative report. Newspapers and magazines have articles of many different types and this is intended to cover them all.

Schema.org: Thing > CreativeWork > [Article](https://schema.org/Article)
</aside>

> frontmatter parameters

```toml
title = ""
description = ""

date = ""
lastmod = ""
expirydate = ""

categories = ["", ""]
tags = ["", ""]
keywords = ["", ""]

images = ["", ""]
videos = ["", ""]

license = ""
acquirelicensepage = ""

[[author]]
  person = ""
  id = ""
  name = ""
  sameas = ""
  url = ""
[[author]]
  person = ""
  id = ""
  name = ""
  sameas = ""
  url = ""
```

```yaml
title: ''
description: ''
date: ''
lastmod: ''
expirydate: ''
categories:
  - ''
  - ''
tags:
  - ''
  - ''
keywords:
  - ''
  - ''
images:
  - ''
  - ''
videos:
  - ''
  - ''
license: ''
acquirelicensepage: ''
author:
  - person: ''
    id: ''
    name: ''
    sameas: ''
    url: ''
  - person: ''
    id: ''
    name: ''
    sameas: ''
    url: ''
```

```json
{
  "title": "",
  "description": "",
  "date": "",
  "lastmod": "",
  "expirydate": "",
  "categories": [
    "",
    ""
  ],
  "tags": [
    "",
    ""
  ],
  "keywords": [
    "",
    ""
  ],
  "images": [
    "",
    ""
  ],
  "videos": [
    "",
    ""
  ],
  "license": "",
  "acquirelicensepage": "",
  "author": [
    {
      "person": "",
      "id": "",
      "name": "",
      "sameas": "",
      "url": ""
    },
    {
      "person": "",
      "id": "",
      "name": "",
      "sameas": "",
      "url": ""
    }
  ]
}
```

### Configurable frontmatter parameters
Listed are only the parameters which are useful for building *Semantic Web* and *Linked Data*. There are other default Hugo frontmatter parameters which are required, recommended, or optional.

* `title`: <span style="color: red;">***required***</span>; default Hugo frontmatter param
* `description`: <span style="color: green;">**recommended**</span>; default Hugo frontmatter param
* `date`: <span style="color: red;">***required***</span>; default Hugo frontmatter param; ISO8601 format, examples: `2021-01-01`, `2021-01-01T00:00:00`, `2021-01-01T00:00:00+08:00`
* `lastmod`: <span style="color: green;">**recommended if**</span> the article was significantly changed; ISO8601 format, examples: `2021-01-01`, `2021-01-01T00:00:00`, `2021-01-01T00:00:00+08:00`
* `expirydate`: <span style="color: green;">**recommended if**</span> the article information is no longer valid in the present time; ISO8601 format, examples: `2021-01-01`, `2021-01-01T00:00:00`, `2021-01-01T00:00:00+08:00`
* `categories`, `tags`, `keywords`: <span style="color: blue;">*optional*</span>; default Hugo frontmatter param; comment (#) or delete when not in use
* `images`, `videos`: <span style="color: green;">**recommended if**</span> the `image` and/or `video` shortcodes were used, see: [link images to article](#link-images-to-article) and [link-videos-to-article](#link-videos-to-article) for more information and examples
* `license`: <span style="color: blue;">*optional*</span>; fallback: `config` param; URL to License legal codo
* `acquirelicensepage`: <span style="color: blue;">*optional*</span>; fallback: `config` param; URL where information on how to re-use your materials can be found
* `author`: <span style="color: blue;">*optional*</span>, if not set in frontmatter it will fallback to the author/person set in your `config` file; repeat as needed
  * `person`: filename of Type:Person in `/data/persons/`
  * `id`: <span style="color: blue;">*optional if*</span> `person` exists `/data/persons/`; format: `URL/#fragment-identifier`
  * `name` <span style="color: blue;">*optional if*</span> `person` exists in `/data/persons/`
  * `sameas`: <span style="color: blue;">*optional*</span>; URL to other profile/accounts
  * `url`: <span style="color: bluel">*optional*</span>; format: `URL/`; URL to author's homepage

## BlogPosting

<aside class="notice">A blog post.

Schema.org: Thing > CreativeWork > Article > SocialMediaPosting > [BlogPosting](https://schema.org/BlogPosting)
</aside>

This Type relies on the `isblog` parameter in your `config` file. See [Type: WebSite](#website) above for information.

## ImageObject

<aside class="notice">An image file.

Schema.org: Thing > CreativeWork > MediaObject > [ImageObject](https://schema.org/ImageObject)
</aside>

This Type takes advantage of Hugo's shortcode feature. We created a new shortcode called `image`.

The `image` shortcode uses the style from [Embed Responsively](https://embedresponsively.com). This means that the images will use 100% of box it is contained in and when the view is smaller, it will adjust.

Aside:
* There are two ways to add Type:ImageObject support—frontmatter and shortcode—the latter is simpler for everyone in the long-run.
* In addition, the initial approach for shortcode was to upgrade Hugo's built-in `figure` shortcode, however, this may cause compatibility issues with existing projects and themes.

> `{{</* image */>}}` shortcode

```go
{{</* image
  height=""
  width=""
  class=""
  style=""
  type=""

  isrepresentativeofpage=false

  src=""
  link=""
  linkrel=""
  thumbnailurl=""

  title=""
  caption=""
  alt=""
  embeddedtextcaption=""
  inlanguage=""

  datecreated=""
  datepublished=""

  objheight=""
  objwidth=""

  infoalign=""

  licensecode=""
  licenseurl=""
  licensename=""

  acquirelicensepage=""
  copyrightnotice=""
  credittext=""

  attribto=""
  attriburl=""
  attribrel=""

  cc0country=""
  cc0countrycode=""
  cc0countryurl=""

  contentloc=""
  contentlocurl=""
  contentlocrel=""
  contentreferencetime=""
*/>}}
```

### Configurable parameters
* `height` and `width`: <span style="color: blue;">*optional*</span>; used to control the height and width of the object when displayed/rendered
* `class`: <span style="color: blue;">*optional*</span>, default: `obj_center`; if `height` and/or `width` is set, set `class` to position the object. Other values are: `obj_left`, `obj_right`, `obj_floatleft`, `obj_floatright`, or *your_custom_class*; use `class="floatclear"` to clear float if needed
* `style`: <span style="color: blue;">*optional*</span>; an alternative to creating a new `class`; example: in this documentation theme `style="display: table-cell"` is better than a new `class` since it will only be used for a few demo objects
* `type`: <span style="color: blue;">*optional*</span>, default: `image`; change to `imagecoverattrib` if needed (see: [image Bonus](#image-bonus))
* `isrepresentativeofpage`: <span style="color: blue;">*optional*</span>, default: `false`; set to true if the image represents the article
* `src`: <span style="color: red;">***required***</span>; URL of the image file
* `link`: <span style="color: blue;">*optional*</span>; where the image links to when clicked
* `linkrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute of the `link`; change if needed, for example: `me noopener external`
* `thumbnailurl`: <span style="color: blue;">*optional*</span>; URL to the thumbnail image
* `title`: <span style="color: red;">***required***</span>; formal title of the image
* `caption`: <span style="color: green;">**recommended**</span>; caption or description of the image
* `alt`: <span style="color: blue;">*optional*</span>; `alt` attribute of the image; fallback: `caption` then `title`
* `embeddedtextcaption`: <span style="color: blue;">*optional*</span>; text shown in the image, useful for memes
* `inlanguage`: <span style="color: blue;">*optional*</span>; format: [IETF BCP 47 standard](https://en.wikipedia.org/wiki/IETF_language_tag), examples: `en`, `en-PH`, `tl-Tglg`, `ko`, `ja`; when there is text in the image, usually in memes
* `datecreated`: <span style="color: green;">**recommended**</span>, <span style="color: blue;">*optional if*</span> same as `datepublished`; format: `YYYY-MM-DD`;
* `datepublished`: <span style="color: green;">**recommended**</span>; format: `YYYY-MM-DD`
* `objheight`: <span style="color: blue;">*optional*</span>; actual height of the object
* `objwidth`: <span style="color: blue;">*optional*</span>; actual width of the object
* `infoalign`: <span style="color: blue;">*optional*</span>, default: `txt_center`; text alignment for the information section. Other values are: `txt_justify`, `txt_left`, `txt_right`
* `licensecode`: <span style="color: green;">**recommended**</span>; a flag to determine which Copyright notice to use. Available built-in values are:
  * `allrightsreserved`: default
  * `publicdomain`: for works already in the public domain
  * `cc0`: for your own works you want to release in the public domain; requires `cc0country`, `cc0countrycode`, `cc0countryurl`
  * if *any value* is entered, `licenseurl` and `licensename` are <span style="color: red;">***required***</span>. Examples: `ccby4`, `gfdl`, `anything`
* `licenseurl`: <span style="color: red;">***required if***</span> *any value* in `licensecode`; URL to the License's Legal page. Examples: `https://creativecommons.org/licenses/by/4.0/`, `https://www.gnu.org/licenses/fdl-1.3.en.html`
* `licensename`: <span style="color: red;">***required if***</span> *any value* in `licensecode`, default: `All Rights Reserved`; name of the License. Examples: `Creative Commons Attribution 4.0 International`, `GNU Free Documentation License 1.3`
* `acquirelicensepage`: <span style="color: green;">**recommended**</span>; URL to where information on how to get a license to use the image
* `copyrightnotice`: <span style="color: blue;">*optional*</span>; example: Copyleft 🄯 CC-BY-SA 4.0 International by YourOnly.One
* `credittext`: <span style="color: blue;">*optional*</span>; example: YourOnly.One (https://youronly.one)
* `attribto`: <span style="color: red;">***required***</span>; to whom to attribute
* `attriburl`: <span style="color: blue;">*optional*</span>; URL to `attribto`
* `attribrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute for `attriburl`
* `cc0country`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; example: `Philippines`, `South Korea`, `Japan`
* `cc0countrycode`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; should be ISO3166 code, example: `PH`, `KR`, `JP`
* `cc0countryurl`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; tip: official government or tourism website, or Wikipedia article
* `contentloc`: <span style="color: green;">**recommended for**</span> photos; location of the content shown in the photo
* `contentlocurl`: <span style="color: green;">**recommended for**</span> photos; URL of the location shown in the photo; tip: official website or Wikipedia article
* `contentlocrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute for `contentlocurl`
* `contentreferencetime`: <span style="color: blue;">*optional*</span>; ISO8601 format, examples: `2021-01-01`, `2021-01-01T00:00:00`, `2021-01-01T00:00:00+08:00`; if the photo is about a specific moment in time

### Link images to Article
To establish a relationship between Type:ImageObject and Type:Article, add the source URL of the image(s) in the article's frontmatter, use Hugo's default: `images = ["", ""]`.

For example: `images = ["https://rsc.youronly.one/img/y/Yuki_flag-300h.webp", "https://img.youronly.one/works/Yellow_Bell-02-CC_By-SA_4.0-s.webp"]`.

<aside class="warning">
If the source URL of the images change later, a new domain name for example, the URL in the `images` frontmatter must be updated as well, otherwise, the relationship will be broken.
</aside>

It is best to keep the old URLs and redirect it to the new host, or run a mass edit against the existing articles. How to do either of the aforementioned options is outside the scope of this project and documentation.

### Sample #1: Basic images
Switching existing posts from Hugo built-in `figure` to **Semantic Web for Hugo** `image` shortcode—without adding new parameters—will look like this:

<style>
  .semwebdemostyle {
    display: table-cell;
  }
</style>

```go
{{</* image
  class="semwebdemostyle"
  src="https://rsc.youronly.one/img/y/Yuki_flag-300h.webp"
  link="https://im.youronly.one/yuki/"
  alt="ALT"
  title="TITLE"
  caption="CAPTION"
  attr="ATTRIBUTION"
  attrlink="https://youronly.one"
*/>}}
```

{{< image
  class="semwebdemostyle"
  src="https://rsc.youronly.one/img/y/Yuki_flag-300h.webp"
  link="https://im.youronly.one/yuki/"
  alt="ALT"
  title="TITLE"
  caption="CAPTION"
  attr="ATTRIBUTION"
  attrlink="https://youronly.one"
>}}

Wondering why there is a `class="semwebdemostyle"` in the above sample image? We are mimicking the built-in `figure` shortcode, as explained above, and we need to add `display: table-cell` to render the image properly in this documentation theme.

### Sample #2: Rich images
This is a sample of an `image` shortcode with additional parameters useful for building *Semantic Web* and *Linked Data*.

```go
{{</* image
  style="display: table-cell;"
  type="image"
  src="https://img.youronly.one/works/Yellow_Bell-02-CC_By-SA_4.0-s.webp"
  link="https://im.youronly.one/yuki/photography/the-yellow-bells-of-piddig-2021225/"
  linkrel="noopener external"
  title="Allamanda cathartica or Yellow Bell"
  datecreated="2018-05-19"
  datepublished="2020-08-13"
  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"
  acquirelicensepage="https://im.youronly.one/p/legal-notice/"
  attribto="YourOnly.One"
  attriburl="https://youronly.one"
  attribrel="noopener external"
  contentloc="Piddig, Ilocos Norte, Philippines"
  contentlocurl="https://en.wikipedia.org/wiki/Piddig"
  contentlocrel="noopener external nofollow"
  contentreferencetime="2018-05-19"
*/>}}
```

{{< image
  style="display: table-cell;"
  type="image"
  src="https://img.youronly.one/works/Yellow_Bell-02-CC_By-SA_4.0-s.webp"
  link="https://im.youronly.one/yuki/photography/the-yellow-bells-of-piddig-2021225/"
  linkrel="noopener external"
  title="Allamanda cathartica or Yellow Bell"
  datecreated="2018-05-19"
  datepublished="2020-08-13"
  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"
  acquirelicensepage="https://im.youronly.one/p/legal-notice/"
  attribto="YourOnly.One"
  attriburl="https://youronly.one"
  attribrel="noopener external"
  contentloc="Piddig, Ilocos Norte, Philippines"
  contentlocurl="https://en.wikipedia.org/wiki/Piddig"
  contentlocrel="noopener external nofollow"
  contentreferencetime="2018-05-19"
>}}

### Bonus: cover image

```go
{{</* image
  style="display: table-cell;"
  type="imagecoverattrib"
  link="https://img.youronly.one/works/Sunflower_in_the_City-03-Nokia3_macro-20180409_150647-s.webp"
  linkrel="noopener external"
  title="Sunflower in the City"
  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"
  attribto="YourOnly.One"
  attriburl="https://youronly.one"
  attribrel="noopener external"
*/>}}
```

The `image` shortcode includes an option to give attribution for the article's cover image separately, simply add the `image` shortcode at the end of an article's file with the `type` set to `imagecoverattrib`.

It will look like this:

{{< image
  style="display: table-cell;"
  type="imagecoverattrib"
  link="https://img.youronly.one/works/Sunflower_in_the_City-03-Nokia3_macro-20180409_150647-s.webp"
  linkrel="noopener external"
  title="Sunflower in the City"
  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"
  attribto="YourOnly.One"
  attriburl="https://youronly.one"
  attribrel="noopener external"
>}}

## VideoObject

<aside class="notice">A video file.

Schema.org: Thing > CreativeWork > MediaObject > [VideoObject](https://schema.org/VideoObject)
</aside>

This Type takes advantage of Hugo's shortcode feature. The `{{</* video */>}}` shortcode is included in **Semantic Web for Hugo** with support for YouTube and Vimeo, and Hugo's [Privacy Config](https://gohugo.io/about/hugo-and-gdpr/).

> `{{</* video */>}}` shortcode

```go
{{</* video
  height=""
  width=""
  class=""
  style=""
  platform=""

  id=""
  linkrel=""
  isplaylist=false
  isloop=false
  starttime=""
  endtime=""

  title=""
  caption=""
  inlanguage=""

  datecreated=""
  datepublished=""

  director=""
  musicby=""

  objframesize=""
  objquality=""
  objheight=""
  objwidth=""

  infoalign=""

  licensecode=""
  licenseurl=""
  licensename=""

  acquirelicensepage=""
  copyrightnotice=""
  credittext=""

  attribto=""
  attriburl=""
  attribrel=""

  cc0country=""
  cc0countrycode=""
  cc0countryurl=""

  contentloc=""
  contentlocurl=""
  contentlocrel=""
  contentreferencetime=""
*/>}}
```

### Configurable parameters
* `height` and `width`: <span style="color: blue;">*optional*</span>; used to control the height and width of the object when displayed/rendered
* `class`: <span style="color: blue;">*optional*</span>, default: `obj_center`; if `height` and/or `width` is set, set `class` to position the object. Other values are: `obj_left`, `obj_right`, `obj_floatleft`, `obj_floatright`, or *your_custom_class*; use `class="floatclear"` to clear float if needed
* `style`: <span style="color: blue;">*optional*</span>; an alternative to creating a new `class`; example: in this documentation theme `style="display: table-cell"` is better than a new `class` since it will only be used for a few demo objects
* `platform`: <span style="color: blue;">*optional*</span>, default: `youtube`; change to `vimeo` if needed
* `id`: <span style="color: red;">***required***</span>; ID of the video
* `linkrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute for the video link (automatically generated); change if needed, for example: `me noopener external`
* `isplaylist`: <span style="color: blue;">*optional*</span>, default: `false`; set to `true` if `id` is a YouTube playlist
* `isloop`: <span style="color: blue;">*optional*</span>, default: `false`; set to `true` if video should loop
* `starttime`: <span style="color: blue;">*optional*</span>; format: in seconds; only applicable for YouTube
* `endtime`: <span style="color: blue;">*optional*</span>; format: in seconds; only applicable for YouTube
* `title`: <span style="color: red;">***required***</span>; formal title of the video
* `caption`: <span style="color: green;">**recommended**</span>; caption or description of the video
* `inlanguage`: <span style="color: blue;">*optional*</span>; format: [IETF BCP 47 standard](https://en.wikipedia.org/wiki/IETF_language_tag), examples: `en`, `en-PH`, `tl-Tglg`, `ko`, `ja`; voice language
* `datecreated`: <span style="color: green;">**recommended**</span>, <span style="color: blue;">*optional if*</span> same as `datepublished`; format: `YYYY-MM-DD`;
* `datepublished`: <span style="color: green;">**recommended**</span>; format: `YYYY-MM-DD`
* `director`: <span style="color: blue;">*optional*</span>; name of director
* `musicby`: <span style="color: blue;">*optional*</span>; name of music composer
* `objframesize`: <span style="color: blue;">*optional*</span>; actual framesize of the object
* `objquality`: <span style="color: blue;">*optional*</span>; actual quality of the object
* `objheight`: <span style="color: blue;">*optional*</span>; actual height of the object
* `objwidth`: <span style="color: blue;">*optional*</span>; actual width of the object
* `infoalign`: <span style="color: blue;">*optional*</span>, default: `txt_center`; text alignment for the information section. Other values are: `txt_justify`, `txt_left`, `txt_right`
* `licensecode`: <span style="color: green;">**recommended**</span>; a flag to determine which Copyright notice to use. Available built-in values are:
  * `allrightsreserved`: default
  * `publicdomain`: for works already in the public domain
  * `cc0`: for your own works you want to release in the public domain; requires `cc0country`, `cc0countrycode`, `cc0countryurl`
  * if *any value* is entered, `licenseurl` and `licensename` are <span style="color: red;">***required***</span>. Examples: `ccby4`, `gfdl`, `anything`
* `licenseurl`: <span style="color: red;">***required if***</span> *any value* in `licensecode`; URL to the License's Legal page. Examples: `https://creativecommons.org/licenses/by/4.0/`, `https://www.gnu.org/licenses/fdl-1.3.en.html`
* `licensename`: <span style="color: red;">***required if***</span> *any value* in `licensecode`, default: `All Rights Reserved`; name of the License. Examples: `Creative Commons Attribution 4.0 International`, `GNU Free Documentation License 1.3`
* `attribto`: <span style="color: red;">***required***</span>; to whom to attribute
* `attriburl`: <span style="color: blue;">*optional*</span>; URL to `attribto`
* `attribrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute for `attriburl`
* `cc0country`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; example: `Philippines`, `South Korea`, `Japan`
* `cc0countrycode`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; should be ISO3166 code, example: `PH`, `KR`, `JP`
* `cc0countryurl`: <span style="color: red;">***required if***</span> `licensecode="cc0"`; tip: official government or tourism website, or Wikipedia article
* `acquirelicensepage`: <span style="color: green;">**recommended**</span>; URL to where information on how to get a license to use the image
* `copyrightnotice`: <span style="color: blue;">*optional*</span>; example: Copyleft 🄯 CC-BY-SA 4.0 International by YourOnly.One
* `credittext`: <span style="color: blue;">*optional*</span>; example: YourOnly.One (https://youronly.one)
* `contentloc`: <span style="color: green;">**recommended**</span>; location of the content shown in the video
* `contentlocurl`: <span style="color: green;">**recommended**</span>; URL of the location shown in the video; tip: official website or Wikipedia article
* `contentlocrel`: <span style="color: blue;">*optional*</span>, default: `noopener external nofollow`; `rel` attribute for `contentlocurl`
* `contentreferencetime`: <span style="color: blue;">*optional*</span>; ISO8601 format, examples: `2021-01-01`, `2021-01-01T00:00:00`, `2021-01-01T00:00:00+08:00`; if the video is about a specific moment in time

### Link videos to Article
To create a relationship between Type:VideoObject and Type:Article, add the URL of the video(s) in the article's frontmatter, use Hugo's `videos = ["", ""]`. If any, remove all other parameters in the URL, it should only contain the video host's domain name and the video's ID.

For example:
* YouTube: `https://www.youtube.com/watch?v=OM6XIICm_qo`
* Vimeo: `https://vimeo.com/601088734`

<aside class="warning">
The host's domain name should be as it is shown when viewing the video in their respective websites, if there is a `www` include it even if a non-www version works, or vice versa.
</aside>

### Sample #1: YouTube
A sample YouTube embed with Hugo's Privacy Config enabled.

```go
{{</* video
  style="display: table-cell;"
  id="OM6XIICm_qo"
  title="Tim Berners-Lee: The next Web of open, linked data"
  caption="20 years ago, Tim Berners-Lee invented the World Wide Web. For his next project, he's building a web for open, linked data that could do for numbers what the Web did for words, pictures, video: unlock our data and reframe the way we use it together."
  inlanguage="en"
  datepublished="2009-03-13"
  attribto="TED"
  attriburl="https://www.youtube.com/channel/UCAuUUnT6oDeKwE6v1NGQxug"
*/>}}
```

{{< video
  style="display: table-cell;"
  platform="youtube"
  id="OM6XIICm_qo"
  title="Tim Berners-Lee: The next Web of open, linked data"
  caption="20 years ago, Tim Berners-Lee invented the World Wide Web. For his next project, he's building a web for open, linked data that could do for numbers what the Web did for words, pictures, video: unlock our data and reframe the way we use it together."
  inlanguage="en"
  datepublished="2009-03-13"
  attribto="TED"
  attriburl="https://www.youtube.com/channel/UCAuUUnT6oDeKwE6v1NGQxug"
>}}

### Sample #2: Vimeo
A Vimeo embed with Hugo's Privacy Config enabled.

```go
{{</* video
  style="display: table-cell;"
  platform="vimeo"
  id="601088734"
  title="The Wild: Capturing Our Planet in Dolby Vision"
  caption="The Wild is a short film inspired by the idea that we need to co-exist and protect nature. It’s Noah Beschen's journey through our beautiful world captured and shared with the crisp clarity and vibrancy of Dolby Vision. Because every moment should look like this."
  inlanguage="en"
  datepublished="2021-09-09"
  attribto="Aaron Lieber"
  attriburl="https://vimeo.com/lieberfilms"
*/>}}
```

{{< video
  style="display: table-cell;"
  platform="vimeo"
  id="601088734"
  title="The Wild: Capturing Our Planet in Dolby Vision"
  caption="The Wild is a short film inspired by the idea that we need to co-exist and protect nature. It’s Noah Beschen's journey through our beautiful world captured and shared with the crisp clarity and vibrancy of Dolby Vision. Because every moment should look like this."
  inlanguage="en"
  datepublished="2021-09-09"
  attribto="Aaron Lieber"
  attriburl="https://vimeo.com/lieberfilms"
>}}

# Contribute
You can contribute to the project via our Github: [https://github.com/YourOnly-One/hugo-semantic-web](https://github.com/YourOnly-One/hugo-semantic-web).

You can also help with our documentation via our Github: [https://github.com/YourOnly-One/hugo-semantic-web-docs](https://github.com/YourOnly-One/hugo-semantic-web-docs).

# Contact Us
## Bugs and Suggestions
Please file a bug report and suggest new features in our project's Github: [https://github.com/YourOnly-One/hugo-semantic-web/issues](https://github.com/YourOnly-One/hugo-semantic-web/issues).

## Discuss
If you want to discuss something or ask a question, you can do it in our project's Github: [https://github.com/YourOnly-One/hugo-semantic-web/discussions](https://github.com/YourOnly-One/hugo-semantic-web/discussions).

## Documentation
For documentation improvements, file it in our documentation Github: [https://github.com/YourOnly-One/hugo-semantic-web-docs/issues](https://github.com/YourOnly-One/hugo-semantic-web-docs/issues)
