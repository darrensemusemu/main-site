---
title: "Building the Certify-d Platform"
date: 2022-09-19T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["certify-d", "c4-model"]
categories: ["docs"]
author: ["Darren Semusemu"]
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: ""
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "/post/images/certify-d-cta1.png" # image path/url
    alt: "Certify with" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Introduction

Getting certified copies of official documents should be a simple straightforward task. Currently, this is not the case. It is somewhat tedious, time-consuming, and requires an unnecessary amount of energy for all parties involved.  However, this can be automated into a simple online process. I introduce you to [***Certify-d***](https://certify-d.darrensemusemu.com).

> *Disclaimer: I provide the following only as a way to showcase my skills, learn,  and test the feasibility of such a complex system. Do not use this software in critical situations or projects.*

# What is Certify-d?

The purpose of Certify-d is to generate certified copies --- ie. documents regarded as true copies of the original. Useful in cases where the original is to be kept safe by the owner, the copies require an official signature from a legally authorised person.


Main features:

- upload original documents, e.g. identity documents and qualifications;
- generate certified copies, with a legally authorised signature/stamp; and
- share certified copies w/ relevant parties.


The application should only produce certified copies. Verifying that a document is genuine --- that is not forged --- is out of scope and falls not in our responsibility.


In order of importance and priority, the following are our quality goals: 
 
1. functional correctness: provide a high degree of accurate result for tasks;
1. time behaviour: system should handle tasks and deliver in well reasonable time;
1. interoperability: provide a simple API to allow for different and new clients to connect.

# System Scope and Context

At the highest level of abstraction, we differentiate the business context and technical context of our system.

![System Context Diagram](https://raw.githubusercontent.com/darrensemusemu/certify-d-api/main/docs/diagrams/out/c4_l1_context.png)

As for our business context, we identify:

- Person/Actors: the customer, staff, and commissioners;
- The System: the system at the highest level of abstraction;
- External Systems: Payment provider, Auth provider, Email service, and SMS service.

As for our technical context, within the "Certify-d System" boundary, there exist multiple containers (deployable units of work). The containers all use HTTP requests to interface and communicate.

# System Container

<!-- ## Solution Strategy -->

The Certify-d system will consist of multiple APIs running as containerised servers communicating with other services and front-end clients. 

Building the system using [Go(lang)](https://go.dev/) is a clear choice given the following benefits:

- compiles our services to relatively small statically linked native binaries,
- good support for concurrent programming, and
- *development team* has good experience with the language and eco-system.

We look at functional, unit, and integration tests as providing an acceptable level of functional correctness. 

Regarding time behavoiur as a quality goal, the process of generating certified copies can be a long-running task. The implementation of an event-driven system with a persistence log/queue allows us to achieve an acceptable time and guarantee.

Use of the [OpenAPI Specification (OAS)](https://spec.openapis.org/oas/v3.1.0) allows us to meet our Interoperability quality goal by providing clients a standardised interface to interact with our system through HTTP APIs. Further allowing the simplification of our API Documentation efforts, and code generation of clients. 

![System Container Diagram](https://raw.githubusercontent.com/darrensemusemu/certify-d-api/main/docs/diagrams/out/c4_l2_container.png)

# Read More

- [Certify-d API](https://github.com/darrensemusemu/certify-d-api)
- [Certify-d Front-end](https://github.com/darrensemusemu/certify-d-web)


![Call to action](/post/images/certify-d-cta2.png)
