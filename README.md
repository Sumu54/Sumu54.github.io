# My Personal Website
- [Website](https://Sumu54.github.io/)

# Website Edits
- About yourself (Homepage): `_pages/about.md`
- Profile Photo: `images/profile.png` which is included as author avatar in `_config.yml`.
- Settings: `_config.yml`
- Select Website Tabs: `_data/navigation.yml`
    + For example to add the tab `Workshops` add a section in `navigation.yml` and create a file in `_pages/workshops.md` and write the contents there.
- Notes
  + Once we have each markdown files for the publications, the CV can read them automatically using for-loop as given in original template.
- To update new resume replace the file `files/SumedhaDahal_CV_Scientist.pdf`

# Automatic include multiple markdown files in folder to another file
- Step 01: Create files like `_myworkshops/date-title.md`
- Step 02: Include collection in `_config.yml`
```
collections:
  myworkshops:
    output: true
    permalink: /:collections/:title/


or like this:


collections:
  myworkshops:
    output: true
    permalink: /:collection/:path/
```
- Step 03: Create many files in the new folder `_myworkshops` with names like `2025-01-01-workshop-01-my-good-workshop`
```
---
title: "Workshop on Intellectual Property Rights in Lifesciences"
collection: workshops
type: "Workshop"
permalink: /workshops/2013-11-14-ipr-biotech
venue: "REVA University & IIPTA"
date: 2013-11-14
location: "Bangalore, India"
---
```
- Step 04: Include all these in another markdown such as cv.md like this: (Note that name for all of them is `archive-single-cv.html`
```
## Workshops

<ul>
  {% for post in site.myworkshops reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}
</ul>

```

# Automatic include one markdown in another markdown
- create file `_includes/workshops-section.md` and write normal markdown or html without any yaml headers.
- create: `_pages/workshops.md`
```
---
layout: single
title: "Workshops"
permalink: /workshops/
author_profile: true
---

{% include workshops-section.md %}

```

- Then, we can include this in `cv.md` as:
```
{% include workshops-section.md %}
```
