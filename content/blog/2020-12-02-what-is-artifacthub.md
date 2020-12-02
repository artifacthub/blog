---
title: "What Is The Artifact Hub?"
date: 2020-12-02T09:00:00-05:00
author: "Matt Farina"
authorLink: "https://mattfarina.com"
slug: "what-is-artifacthub"
---

Finding cloud native artifacts on the Internet can be difficult. When we talk about artifacts we mean things like [Helm](https://helm.sh) charts, Kubernetes operators, [Falco](https://falco.org/) rules, and [Open Policy Agent](https://www.openpolicyagent.org/) (OPA) policies. If you use a search engine to look for them the results will be mixed with articles, documentation, and discussion. This experience is far from ideal if you want to find a package or tool to install.

This has lead to the rise of Hubs like the Helm Hub (which now redirects to the Artifact Hub) and [Operator Hub](https://operatorhub.io/). These hubs made it possible to discover distributed artifacts for one project or another. These hubs improved the experience but were still missing an opportunity.

In November 2019, [Dan Kohn](https://en.wikipedia.org/wiki/Dan_Kohn) brought together people from the Helm, [Operator Framework](https://operatorframework.io/), and [KUDO](https://kudo.dev/) projects to discuss the idea of one hub that would make discovery of all these things possible. This happened over lunch at CloudNativeCon/KubeCon in San Diego. It was one of the many times that Dan brought people together to try and make something happen for the broader cloud native community.

The Artifact Hub was born out of this idea Dan had. It has come a long way since its initial release. You can now find artifacts from various projects distributed by different people and companies all over the world. You can find projects that relate to each other. You can perform simple searches and you can apply filters. You can be notified when an artifact is updated (webhooks and email). And, so much more.

This blog will serve as a place you can learn about the new developments, why features were developed the way they are, and some of the existing features that are little known but useful.