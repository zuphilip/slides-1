---
title: SkoHub – KOS-based content syndication with ActivityPub
description: Presentation at SWIB19 in Hamburg, 2019-11-27
image: https://raw.githubusercontent.com/hbz/slides/swib19-skohub/skohub-swib19/img/slides-screenshot.png
slideOptions:
  theme: black

---

# SkoHub:
## KOS-based content syndication with ActivityPub

<small>Adrian Pohl ( [@acka47]()), hbz &
    Felix Ostrowski ([@literarymachine](https://twitter.com/literarymachine)), graphthinking GmbH)</small>

<small>SWIB19, Hamburg, 2019-11-27</small>

---

## Task:
### Set up infrastructure for publishing and finding Open Educational Resources (OER)

---

## Open Educational Resources (OER)
- various resource types: from task sheets to simulations & software
- anything text-based, audio, video, interactive
- published on different platforms on the web: video platforms, homepages, slide platforms, wikis, repositories etc.

---

## Possible approaches
- set up OER repos
- harvest data via OA-PMH
- normalize data and index into discovery services
- offer "information competence" courses so that people know how to use our infrastructure

---

## No, not again

---

## Why not?
- only resources in repos are covered, not elswhere on the web
- Users have to know where to find your service to start searching
- The approach is "off the web"

---


### Repository-centric, not web-centric
> <small>Conceptually, we have come to see [OAI-PMH] as repository-centric instead of resource-centric or web-centric. It has its starting point in the repository, which is considered to be the center of the universe. Interoperability is framed in terms of the repository, rather than in terms of the web and its primitives. This kind of repository, although it resides on the web, hinders seamless access to its content because it does not fully embrace the ways of the web.</small>

<small>– [Van de Sompel/Nelson 2015](https://dx.doi.org/10.1045/november2015-vandesompel)</small>

---

## How could a web-centric or resource-centric approach to discovery like?

---

## Make it subject-oriented
## & start with shared domain models

---

![](http://slides.lobid.org/kmk-oer/img/oeglobal2018_topic-orientation.png)

<small>Paul Gobee/Pim Bellinga (2018): [TOOLs. Topic-Oriented Open Learning platforms](https://schd.ws/hosted_files/oeglobal2018/5b/Topic%20Oriented%20Open%20Learning_TOOL_platforms_a%20novel%20approach%20for%20open%20education%20%E2%80%93%20experiences%20of%20two%20initiativesoeglobal18_tool_presentation_asPresented.pdf), presentation at OE Global 2018, Delft.</small>

---

## We build something,
## let's demo

---

### SkoHub Vocabs: Managing and publishing domain models as SKOS vocabs on the web
1. Publish SKOS vocab as turtle file on GitHub (GitLab integration is in the works)
2. Set up webhook
3. Vocab is published as HTML/JSON-LD via skohub.io
4. Each concept is also an ActivityPub actor (`Service`) that you can follow

----

<a href="https://github.com/hbz/vocabs-edu/blob/master/esc.ttl"><img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/esc-on-github.png?raw=true" alt="The SKOS turtle file for the Educational Subject Classification on GitHub" width=800 style="border: none; box-shadow: none;" /></a>
<small>Educational Subject Classification on GitHub</small>

----

<img src="http://blog.lobid.org/images/presenting-skohub-vocabs/add-webhook2.png" alt="Setting up a webhook in GitHub" width=750 style="border: none; box-shadow: none;" />
<small>Setting up a Webhook</small>

----

<a href="https://test.skohub.io/acka47/skos/w3id.org/class/esc/scheme.html"><img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/published-esc.png?raw=true" alt="The published ESC vocab as HTML view on skohub.io" width=800 style="border: none; box-shadow: none;" /></a>
<small>The published vocab on skohub.io</small>

----

<img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/follow-topic.png?raw=true" alt="The published ESC vocab as HTML view on skohub.io" width=700 style="border: none; box-shadow: none;" />
<small>Follow a subject using Mastodon</small>

---

### SkoHub Editor: Describing web content & notify followers of a subject
- Use SkoHub Editor to describe a web resource
- Notify followers of a subject by adding it to the description
- Editor is configured & input validated with JSON schema
- Metadata is published to inbox of assigned subjects & then distributed to followers

----

<a href="https://pad.gwdg.de/p/BJvl5sFiB"><img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/slides-screenshot.png?raw=true" alt="The title slide of this slide deck" width=800 style="border: none; box-shadow: none;" /></a>
<small>This is a nice slide deck. I would like to share it with others interested in ICT.</small>

----

<img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/describe-resource.png?raw=true" alt="Describing a resource with the SkoHub Editor browser extension" width=800 style="border: none; box-shadow: none;" />
<small>Describe the resource with basic metadata</small>

----

## Push information to interested people
<span>
    <h3>Based on which criterion?</h3>
</span>


---

## Fully open
- Free software
- based in open web standards
- anybody can develop additional clients

---

## Other use cases

- communicate updates (corrections, additions) for a concept, see Ilik/Koster 2019
- 