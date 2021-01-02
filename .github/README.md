# Feed Json
[heading__top]:
  #feed-json
  "&#x2B06; JSON feed from collection and FrontMatter data"


JSON feed from collection and FrontMatter data


## [![Byte size of Feed Json][badge__main__feed_json__source_code]][feed_json__main__source_code] [![Open Issues][badge__issues__feed_json]][issues__feed_json] [![Open Pull Requests][badge__pull_requests__feed_json]][pull_requests__feed_json] [![Latest commits][badge__commits__feed_json__main]][commits__feed_json__main] [![feed-json Demos][badge__gh_pages__feed_json]][gh_pages__feed_json] 


---


- [:arrow_up: Top of Document][heading__top]

- [:building_construction: Requirements][heading__requirements]

- [:zap: Quick Start][heading__quick_start]

  - [:memo: Edit Your ReadMe File][heading__your_readme_file]
  - [:floppy_disk: Commit and Push][heading__commit_and_push]

- [&#x1F9F0; Usage][heading__usage]

- [:symbols: API][heading__api]

- [&#x1F5D2; Notes][heading__notes]

- [:chart_with_upwards_trend: Contributing][heading__contributing]

  - [:trident: Forking][heading__forking]
  - [:currency_exchange: Sponsor][heading__sponsor]

- [:card_index: Attribution][heading__attribution]

- [:balance_scale: Licensing][heading__license]


---



## Requirements
[heading__requirements]:
  #requirements
  "&#x1F3D7; Prerequisites and/or dependencies that this project needs to function properly"


This repository depends upon [Jekyll][jekyll_rb__home] which is supported by [GitHub Pages][github_docs__github_pages__jekyll], further details about setup can be found from [documentation][jekyll_rb__github_pages] published by the Jekyll maintainers regarding GitHub Pages.


Spicificly this project utilizes the `push` filter that Jekyll _flavored_ Liquid makes available to build JSON output, eg...


```Liquid
{% assign new_list = '' | split: ',' %}
{% assign new_list = new_list | push: 'first' %}
{% assign new_list = new_list | push: 'second' %}
{% assign new_list = new_list | push: 'third' %}

{% capture json_data %}
{
  "list": {{ new_list | jsonify }}
}
{% endcapture %}

{{ json_data }}
```


______


## Quick Start
[heading__quick_start]:
  #quick-start
  "&#9889; Perhaps as easy as one, 2.0,..."


This repository encourages the use of Git Submodules to track dependencies


**Bash Variables**


```Bash
_module_name='feed-json'
_module_https_url="https://github.com/liquid-utilities/feed-json.git"
_module_base_dir='_layouts/modules'
_module_path="${_module_base_dir}/${_module_name}"
```


**Bash Submodule Commands**


```Bash
cd "<your-git-project-path>"

git checkout gh-pages
mkdir -vp "${_module_base_dir}"

git submodule add -b main\
                  --name "${_module_name}"\
                  "${_module_https_url}"\
                  "${_module_path}"
```


---


### Your ReadMe File
[heading__your_readme_file]:
  #your-readme-file
  "&#x1F4DD; Suggested additions for your ReadMe.md file so everyone has a good time with submodules"


Suggested additions for your _`ReadMe.md`_ file so everyone has a good time with submodules


```MarkDown
Clone with the following to avoid incomplete downloads


    git clone --recurse-submodules <url-for-your-project>


Update/upgrade submodules via


    git submodule update --init --merge --recursive
```


---


### Commit and Push
[heading__commit_and_push]:
  #commit-and-push
  "&#x1F4BE; It may be just this easy..."


```Bash
git add .gitmodules
git add "${_module_path}"


## Add any changed files too


git commit -F- <<'EOF'
:heavy_plus_sign: Adds `liquid-utilities/feed-json#1` submodule



**Additions**


- `.gitmodules`, tracks submodules AKA Git within Git _fanciness_

- `README.md`, updates installation and updating guidance

- `_layouts/modules/feed-json`, JSON feed from collection and FrontMatter data
EOF


git push origin gh-pages
```


**:tada: Excellent :tada:** your project is now ready to begin unitizing code from this repository!


______


## Usage
[heading__usage]:
  #usage
  "&#x1F9F0; How to utilize this repository"


`_config.yml (snip)`


```YAML
collections_dir: documentation
collections:
  example-collection:
    output: true
    permalink: /:collection/:name/
```


---


`documentation/_example-collection/feed.json`


```YAML
layout: modules/feed-json/feed-json
title: Example Collection
description: Collection of example posts
collection_name: example-collection
collection_home: /example-collection/
date: 2021-01-01 11:12:13 -0700
permalink: /:collection/:name:output_ext
```


---


`documentation/_example-collection/something-about-something.md`


```MarkDown
---
## Layout may be `default`, `post`, or `page` depending upon theme
layout: post

title: Title of Page
date: 2021-01-01 13:42:11 -0300
#date_updated:  ## Optional and formatted like `date` above

description: A description of page content
tags:
  - spam
  - flavored
  - ham
---


Content that expands on the topic of something about some thing
```


---


Expect JSON output similar to...


`https://organization.github.io/project-name/example-collection/feed.json`


```JSON
{
  "version": "https://jsonfeed.org/version/1",
  "title": "Example Collection",
  "home_page_url": "https://<account>.github.io/<project>/",
  "feed_url": "https://<account>.github.io/<project>/example-collection/feed.json",
  "description": "Collection of example posts",
  "user_comment": "",
  "next_url": "https://<account>.github.io/<project>/other-collection/",
  "icon": "https://<account>.github.io/<project>/example-collection/icon.png",
  "favicon": "https://<account>.github.io/favicon.ico",
  "author": {
    "name": "S0AndS0",
    "url": "https://github.com/S0AndS0",
    "avatar": "https://avatars2.githubusercontent.com/u/4116150?s=460&u=c45ac68bdfbeec882ff760450de243df45700a73&v=4"
  },
  "expired": false,
  "hubs": [
    {
      "type": "",
      "url": ""
    }
  ],
  "items": [
    {
      "id": "https://<account>.github.io/<project>/posts/<name>.<ext>",
      "url": "https://<account>.github.io/<project>/posts/<name>.<ext>",
      "external_url": "https://example.com/some-applicable-reference",
      "title": "Title of Page",
      "content_html": "<html><!-- Results of rendering post layout --></html>",
      "summary": "A description of page content",
      "image": "https://<account>.github.io/<project>/assets/images/cats/funny.png",
      "banner_image": "",
      "date_published": "2021-01-01T14:13:41-14:00",
      "date_modified": "2021-01-02T14:15:00-14:00",
      "author": {
        "name": "S0AndS0",
        "url": "https://github.com/S0AndS0",
        "avatar": "https://avatars2.githubusercontent.com/u/4116150?s=400&u=c45ac68bdfbeec882ff760450de243df45700a73&v=4"
      },
      "tags": [
        "spam",
        "flavored",
        "ham"
      ],
      "attachments": [
        {
          "url": "",
          "mime_type": "",
          "title": "",
          "size_in_bytes": 99,
          "duration_in_seconds": 42
        }
      ],
      "_custom_entry": {
        "about": "",
        "explicit": false,
        "copywrite": "AGPL-3.0",
        "owner": "",
        "subtitle": ""
      },
      "content_text": "Content that expands on the topic of something about some thing"
    }
  ]
}
```


______


## API
[heading__api]:
  #api
  "&#x1F523; Parameter documentation"


**Collection FrontMatter Type Definitions**


```YAML
title: string

description: string?
user_comment: string?
next_url: string?
icon: string?
favicon: string?
expired: boolean?
language: string?

author: string? | dictionary?
#author:
#  name: string
#  url: string?
#  avatar: string?

authors: dictionary[]?
#authors:
#  - name: string
#    url: string?
#    avatar: string?

hubs: dictionary[]?
#hubs:
#  - type: string
#    url: string
```


**Post FrontMatter Type Definitions**


```YAML
title: string

id: string?
image: string?
banner_image: string?
external_url: string?
tags: string[]?
language: string?

date: string?
#date_published: aliased to date

date_updated: string?
#date_modified: aliased to date_updated

external_url: string?

description: string?
#excerpt: aliased to description
#summary: aliased to description

author: string? | dictionary?
#author:
#  name: string
#  url: string?
#  avatar: string?

authors: dictionary[]?
#authors:
#  - name: string
#    url: string?
#    avatar: string?

attachments: dictionary[]?
#attachments:
#  - url: string
#    mime_type: string
#    title: string?
#    size_in_bytes: number?
#    durration_in_seconds: number?
```


- JSON `"content_html"` is built from `{{ post.output | jsonify }}`

- JSON `"content_text"` is built from `{{ post.content | strip_html | jsonify }}`

- JSON `"id"` if undefined is built from `{{ post.url | absolute_url | jsonify }}`

- JSON `"date_published"` is built from `{{ post.date | date: date_to_xmlschema | jsonify }}` when available

- JSON `"date_modified"` is built from `{{ post.date_updated }}` or `{{ post.date_modified }}`, when available, and filtered the same as `"date_published"` value

- JSON `"summary"` is built from `{{ post.description }}`, `{{ post.summary }}`, or `{{ post.excerpt }}`, where available and filtered similarly to `{{ post.description | strip_html | jsonify }}`

- JSON `"author": {"name": "", "url": "", "avatar": ""}` are built from `{{ page.author }}`, or `{{ site.author }}`, when available. If YAML `author` is a string, then it is coerced to JSON `{"author": {"name": ""}}`; else if YAML `author['name']` is accessible, then no coercion other than `jsonify` filter is used.

> Notes, for JSON Feed Specification version `1.1` JSON Feed compatibility

- JSON `"authors": [{"name": "", "url": "", "avatar": ""}]` are built from `{{ page.authors }}` or `{{ site.authors }}`, when available, but only if recognized as a list containing at least one object with `name` assigned


> YAML keys not listed above map directly to JSON with minimal filtering/alteration.
>
> This project aims to be fully compatible with [JSON Feed Specification version 1][link__json_feed__version_1]; check there for further details on available key/value pares, and expected data types.


______


## Notes
[heading__notes]:
  #notes
  "&#x1F5D2; Additional things to keep in mind when developing"


This repository may not be feature complete and/or fully functional, Pull Requests that add features or fix bugs are certainly welcomed.


---


If using a custom `collections_dir` it is advisable to move the `_posts` subdirectory to live there too, eg...


```Bash
git mv _posts documentation/


git commit -F <<'EOF'
:dizzy: Moves posts directory to collections_dir path
EOF
```


---


For auto-discovery of feeds it is advised to inclide a `link` element within the page `head`, eg...


```HTML
<link rel="alternate"
      title="My Feed"
      type="application/json"
      href="https://example.org/feed.json" />
```


______


## Contributing
[heading__contributing]:
  #contributing
  "&#x1F4C8; Options for contributing to feed-json and liquid-utilities"


Options for contributing to feed-json and liquid-utilities


---


### Forking
[heading__forking]:
  #forking
  "&#x1F531; Tips for forking feed-json"


Start making a [Fork][feed_json__fork_it] of this repository to an account that you have write permissions for.


- Add remote for fork URL. The URL syntax is _`git@github.com:<NAME>/<REPO>.git`_...


```Bash
cd ~/git/hub/liquid-utilities/feed-json

git remote add fork git@github.com:<NAME>/feed-json.git
```


- Commit your changes and push to your fork, eg. to fix an issue...


```Bash
cd ~/git/hub/liquid-utilities/feed-json


git commit -F- <<'EOF'
:bug: Fixes #42 Issue


**Edits**


- `<SCRIPT-NAME>` script, fixes some bug reported in issue
EOF


git push fork main
```


> Note, the `-u` option may be used to set `fork` as the default remote, eg. _`git push -u fork main`_ however, this will also default the `fork` remote for pulling from too! Meaning that pulling updates from `origin` must be done explicitly, eg. _`git pull origin main`_


- Then on GitHub submit a Pull Request through the Web-UI, the URL syntax is _`https://github.com/<NAME>/<REPO>/pull/new/<BRANCH>`_


> Note; to decrease the chances of your Pull Request needing modifications before being accepted, please check the [dot-github](https://github.com/liquid-utilities/.github) repository for detailed contributing guidelines.


---


### Sponsor
  [heading__sponsor]:
  #sponsor
  "&#x1F4B1; Methods for financially supporting liquid-utilities that maintains feed-json"


Thanks for even considering it!


Via Liberapay you may <sub>[![sponsor__shields_io__liberapay]][sponsor__link__liberapay]</sub> on a repeating basis.


Regardless of if you're able to financially support projects such as feed-json that liquid-utilities maintains, please consider sharing projects that are useful with others, because one of the goals of maintaining Open Source repositories is to provide value to the community.


______


## Attribution
[heading__attribution]:
  #attribution
  "&#x1F4C7; Resources that where helpful in building this project so far."


- [GitHub -- `github-utilities/make-readme`](https://github.com/github-utilities/make-readme)

- [GitHub -- Jekyll -- Issue `6521` How do I use absolute_url/relative_url in combination with link?](https://github.com/jekyll/jekyll/issues/6521)

- [Jekyll -- Liquid Filters](https://jekyllrb.com/docs/liquid/filters/)

- [JSON Feed -- Version 1](https://jsonfeed.org/version/1)

- [MDN -- MIME types (IANA media types)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types#JavaScript_types)


______


## License
[heading__license]:
  #license
  "&#x2696; Legal side of Open Source"


```
JSON feed from collection and FrontMatter data
Copyright (C) 2021 S0AndS0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```


For further details review full length version of [AGPL-3.0][branch__current__license] License.



[branch__current__license]:
  /LICENSE
  "&#x2696; Full length version of AGPL-3.0 License"


[badge__commits__feed_json__main]:
  https://img.shields.io/github/last-commit/liquid-utilities/feed-json/main.svg

[commits__feed_json__main]:
  https://github.com/liquid-utilities/feed-json/commits/main
  "&#x1F4DD; History of changes on this branch"


[feed_json__community]:
  https://github.com/liquid-utilities/feed-json/community
  "&#x1F331; Dedicated to functioning code"

[feed_json__gh_pages]:
  https://github.com/liquid-utilities/feed-json/tree/
  "Source code examples hosted thanks to GitHub Pages!"

[badge__gh_pages__feed_json]:
  https://img.shields.io/website/https/liquid-utilities.github.io/feed-json/index.html.svg?down_color=darkorange&down_message=Offline&label=Demo&logo=Demo%20Site&up_color=success&up_message=Online

[gh_pages__feed_json]:
  https://liquid-utilities.github.io/feed-json/index.html
  "&#x1F52C; Check the example collection tests"

[issues__feed_json]:
  https://github.com/liquid-utilities/feed-json/issues
  "&#x2622; Search for and _bump_ existing issues or open new issues for project maintainer to address."

[feed_json__fork_it]:
  https://github.com/liquid-utilities/feed-json/
  "&#x1F531; Fork it!"

[pull_requests__feed_json]:
  https://github.com/liquid-utilities/feed-json/pulls
  "&#x1F3D7; Pull Request friendly, though please check the Community guidelines"

[feed_json__main__source_code]:
  https://github.com/liquid-utilities/feed-json/
  "&#x2328; Project source!"

[badge__issues__feed_json]:
  https://img.shields.io/github/issues/liquid-utilities/feed-json.svg

[badge__pull_requests__feed_json]:
  https://img.shields.io/github/issues-pr/liquid-utilities/feed-json.svg

[badge__main__feed_json__source_code]:
  https://img.shields.io/github/repo-size/liquid-utilities/feed-json


[jekyll_rb__home]:
  https://jekyllrb.com/
  "Jekyll home page"

[jekyll_rb__github_pages]:
  https://jekyllrb.com/docs/github-pages/
  "Jekyll documentation for GitHub Pages setup"

[github_docs__github_pages__jekyll]:
  https://docs.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll
  "GitHub Pages documentation on Jekyll setup"


[sponsor__shields_io__liberapay]:
  https://img.shields.io/static/v1?logo=liberapay&label=Sponsor&message=liquid-utilities

[sponsor__link__liberapay]:
  https://liberapay.com/liquid-utilities
  "&#x1F4B1; Sponsor developments and projects that liquid-utilities maintains via Liberapay"


[link__json_feed__version_1]:
  https://jsonfeed.org/version/1
  "Specification documentation from JSON Feed (version 1)"

[link__json_feed__version_1_1]:
  https://jsonfeed.org/version/1.1
  "Specification documentation from JSON Feed (version 1.1)"

