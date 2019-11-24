---
title: SkoHub – KOS-based content syndication with ActivityPub
description: Presentation at SWIB19 in Hamburg, 2019-11-27
image: https://raw.githubusercontent.com/hbz/slides/swib19-skohub/skohub-swib19/img/slides-screenshot.png
slideOptions:
  theme: black

---

# SkoHub:
## KOS-based content syndication with ActivityPub

<small>Adrian Pohl ([@acka47]()), hbz &
    Felix Ostrowski ([@literarymachine](https://twitter.com/literarymachine)), graphthinking GmbH</small>

<small>SWIB19, Hamburg, 2019-11-27</small>
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" width="120px" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by.png" title="Licensed under a Creative Commons Attribution 4.0 International License"></a>

---

## Task:
### Set up infrastructure for publishing and finding Open Educational Resources (OER)

---

## Open Educational Resources (OER)
- various resource types: from task sheets to textbooks to simulations & software
- anything text-based, audio, video, interactive
- published all over the web: video or slide platforms, homepages, wikis, repositories etc.

---

## Possible approach
- set up OER repos
- ask people to upload / re-publish content there
- harvest data via OAI-PMH
- normalize data and index into discovery services
- tell people where to go for search

---

## No. Not again.

---

## Why not? Drawbacks of a repo approach
- only resources in repos are covered, not elswhere on the web
- users have to know where to find your service to start searching
- it's repository-centric & "off the web"
- we have little technical debt with OER & the chance to try out something new

---

### Repository-centric, not web-centric
> <span style="font-size:28px;">Conceptually, we have come to see [OAI-PMH] as repository-centric instead of resource-centric or web-centric. It has its starting point in the repository, which is considered to be the center of the universe. Interoperability is framed in terms of the repository, rather than in terms of the web and its primitives. This kind of repository, although it resides on the web, hinders seamless access to its content because it does not fully embrace the ways of the web.</span>

<small>– [Van de Sompel/Nelson 2015](https://dx.doi.org/10.1045/november2015-vandesompel)</small>

---

## How could a web-centric or resource-centric approach to discovery look like?

---

## Make it subject-oriented
## & start with shared domain models

Note:
  Sollen wir hier und unten wirklich von "domain models" sprechen? Oder besser "KOS", "classification"?
  FO: Würde nicht von "domain models" sprechen - KOS ist doch ok?

---

![Screenshot saying "To drive OER adoption, communities of practice are key. Topic-oriented technology can help foster them."](http://slides.lobid.org/kmk-oer/img/oeglobal2018_topic-orientation.png)

<small>Paul Gobee/Pim Bellinga (2018): [TOOLs. Topic-Oriented Open Learning platforms](https://schd.ws/hosted_files/oeglobal2018/5b/Topic%20Oriented%20Open%20Learning_TOOL_platforms_a%20novel%20approach%20for%20open%20education%20%E2%80%93%20experiences%20of%20two%20initiativesoeglobal18_tool_presentation_asPresented.pdf), presentation at OE Global 2018, Delft.</small>

---

## Enter SkoHub

- a project by hbz & graphthinking funded by the federal state of North-Rhine Westphalia
- second phase to make software production-ready just started
- software *and* a service
- software: https://github.com/topics/skohub (four modules)
- service: https://skohub.io

---

## Let's demo

---

### SkoHub Vocabs: Managing and publishing domain models as SKOS vocabs on the web
1. publish SKOS vocab as turtle file on GitHub (GitLab integration is in the works)
2. set up webhook
3. vocab is published as HTML/JSON-LD via skohub.io
4. each concept is also an ActivityPub actor (`Service`) that you can follow

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

<img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/follow-topic.png?raw=true" alt="Creenshot of following SKOS concept in Mastodon" width=700 style="border: none; box-shadow: none;" />
<small>Follow a subject using Mastodon</small>

---

### SkoHub Editor: Describing web content & send notifications
- use SkoHub Editor to describe a web resource
- notify followers of a subject by adding it to the description
- editor is configured & input validated with JSON schema
- metadata is published to inbox of assigned subjects & then distributed to followers

Note:
  Ideally, OER publishers will implement notifications when publishing a resource, for now we are using a SkoHub Editor-based browser add-on.

----

<a href="https://pad.gwdg.de/p/BJvl5sFiB"><img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/slides-screenshot.png?raw=true" alt="The title slide of this slide deck" width=800 style="border: none; box-shadow: none;" /></a>
<small>This is a nice slide deck. I would like to share it with others interested in ICT.</small>

----

<img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/describe-resource.png?raw=true" alt="Describing a resource with the SkoHub Editor browser extension" width=800 style="border: none; box-shadow: none;" />
<small>Describe the resource with basic metadata</small>

----

<img src="https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/notification-toot.png?raw=true" alt="A notification toot in mastodon" width=600 style="border: none; box-shadow: none;" />
<small>Followers of subjects will receive notification</small>

----

```json
{
   "id":"https://test.skohub.io/m/e3a4ca4a-23ee-4de2-a07f-fd3e03f465b8",
   "type":"Note",
   "name":"SkoHub – KOS-based content syndication with ActivityPub",
   "url":"https://pad.gwdg.de/p/BJvl5sFiB#/",
   "content":"<p>SkoHub – KOS-based content syndication with ActivityPub: <a href=\"https://pad.gwdg.de/p/BJvl5sFiB#/\" rel=\"nofollow noopener\" target=\"_blank\">https://pad.gwdg.de/p/BJvl5sFiB#/</a></p>",
   "attachment":{
      "name":"SkoHub – KOS-based content syndication with ActivityPub",
      "id":"https://pad.gwdg.de/p/BJvl5sFiB#/",
      "description":"Presentation at SWIB19 in Hamburg, 2019-11-27",
      "type":"PresentationDigitalDocument",
      "creator":[
         {
            "type":"Person",
            "id":"http://lobid.org/team/ap#!",
            "name":"Adrian Pohl"
         },
         {
            "type":"Person",
            "name":"Felix Ostrowski",
            "id":"https://github.com/literarymachine"
         }
      ],
      "about":[
         {
            "id":"https://w3id.org/class/esc/n06",
            "prefLabel":{
               "en":"Information and Communication Technologies (ICTs)"
            },
            "type":"Concept",
            "inScheme":{
               "id":"https://w3id.org/class/esc/scheme"
            }
         }
      ],
      "license":{
         "id":"https://oerworldmap.org/assets/json/licenses/cc-by",
         "prefLabel":{
            "en":"Creative Commons Attribution",
            "de":"Creative Commons Namensnennung"
         },
         "type":"Concept",
         "inScheme":{
            "id":"https://oerworldmap.org/assets/json/licenses/"
         }
      },
      "image":"https://github.com/hbz/slides/blob/swib19-skohub/skohub-swib19/img/slides-screenshot.png?raw=true"
   }
}
```
<small>The [payload](https://test.skohub.io/m/e3a4ca4a-23ee-4de2-a07f-fd3e03f465b8) of the notification with full resource description attached</small>

---

## Social requirements for successful SkoHub use
- agreement on shared domain models
- agreement on schema for resource description
- (to do set up a professional forum for agreements in the German-speaking world, there is another project calls "[StöberSpecs](https://wiki.dnb.de/x/nso8CQ)")

---

## Fully open, decentralized approach
- fully based on open web standards: [Linked Data Notifications](https://www.w3.org/TR/ldn/), [ActivityPub](http://activitypub.rocks/)
- modularized: we invite you to use the pubsub server together with your vocabs publishing solution
- create your own clients: clients are views, decoupled from the data (https://ruben.verborgh.org/blog/2017/12/20/paradigm-shifts-for-the-decentralized-web/#apps-become-views)

Note:
  Ich weiß noch nicht, wie wir das kurz und knapp abhandeln. Vielleicht mit einem Verweis auf Ruben o.ä.

---

## Using SkoHub for communicating KOS changes
as SkoHub provides a generic infrastructure, it might be used for other purposes e.g.:
- communicate new publications by a person based on their authority record
- communicate updates (corrections, additions) for a subject, person entry etc, see Ilik/Koster 2019
- any ideas?

---

## Get involved!

- Homepage: https:///skohub.io
- Blog: http://blog.lobid.org/tags/skohub
- Mailing list: tba

---

## References

de Sompel, Herbert Van / Nelson, Michael L. (2015): Reminiscing About 15 Years of Interoperability Efforts. D-Lib Magazine 21 , no. 11/12. DOI: [10.1045/november2015-vandesompel](https://doi.org/10.1045/november2015-vandesompel)

Ilik, Violeta / Koster, Lukas (2019): Information-Sharing Pipeline, The Serials Librarian, DOI: [10.1080/0361526X.2019.1583045](https://doi.org/10.1080/0361526X.2019.1583045). Preprint: [https://doi.org/10.31219/osf.io/hbwf8](https://doi.org/10.31219/osf.io/hbwf8)