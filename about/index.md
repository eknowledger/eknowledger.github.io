---
layout: post
title: "Ahmed Elmalt"
share: true
comments: false
author_profile: true
toc: true
---

[Download Resume](/files/AhmedElmalt.Resume.pdf){: .btn .btn--info}

# Summary
Accomplished leader, architect, and technical evangelist with a strong and functional knowledge of core enterprise systems and architectures in multiple domains including SaaS Cloud Platforms, CRM Solutions, Government Gateways, Talent Management, Healthcare Management, E-Commerce, and E-learning Solutions. Proven track record of over 15 years of broad, deep, and rich software development hands-on experience and strong academic background in evaluating, implementing, evolving, and governing hardware, software and solutions. Creative professional with extensive support in the overall enterprise architecture across multiple lines of business, developing and driving short/long term architecture strategy, providing cost effective solutions, and supporting the development of architecture principles, styles, patterns and standards. 

## ✦ Core Competence
* **15 years** of experience in **enterprise architecture** on MS Stack .Net, C#, ASP, and SQL Server.
* **5+ years** of experience in delivering cloud first solutions on **Microsoft Azure cloud** platform.
* Hands-on diverse programming and technology platforms including Object-oriented languages (**C#, Java**), Functional Programming Language (**F#, Scala, ML**), Scripting Languages (**JavaScript, Ruby, PowerShell**), and RDMBS (**SQL Server, MongoDB, PostgreSQL**).
* Deep understanding of **distributed system architectures** for vertical industry solutions and LOB applications with focus on developing and delivering large scale platforms.
* Technical leadership in key technologies such as **SaaS enterprise cloud solutions**, **Data Warehousing**, **Business workflow** platforms, **Microservice Architecture**, **Content Management**, **Indoors geo-locating** platforms using **RFID**.
* Hands-on experience managing various aspects of enterprise solutions, such as Service Level Agreements (**SLA**), Business Continuity Plans (**BCP**), and Disaster Recovery Plans (**DRP**).
* Hands-on experience designing, building, and maintaining **Continuous Integration and Delivery pipelines (CI/CD)** and **DevOps Platforms**.
* A Strong handle on software building process, by establishing metrics, procedures, and mechanism to improve deliverable’s quality and building **highly efficient teams**.
* Solid background in **project management** processes; experience designing and running reliable, and predictable software development lifecycle within an agile iterative framework.
* Orchestrated and lead diverse technology oriented activities across **culturally and geographically disparate teams** and customer bases.

# Achievements

## ✦ GoFormz’s Data Capture Platform

As a lead architect, I was tasked to develop a scalable architecture & implementation strategy for the growing business and new business initiative of Enterprise Ready Platform [https://goo.gl/82XH4k](https://goo.gl/82XH4k). I was responsible for the overall application, data, and system architecture of the company’s **SaaS cloud hosted platform**. I designed a reference architecture for **SOA** enterprise solution and an implementation strategy on key pillars such as small automatous **microservices**, **domain driven design**, **polyglot data storage strategy**, and **automated Delivery and Devops platform**.

* I developed a **distributed scalable microservices reference architecture** as a transformation plan, documenting challenges, risks, opportunities, alternate solutions, and timeline.
* I designed and contributed to implementing identity management framework to handle authentication flows; designed to support `OAuth2/OpenId` & `SAML2` protocols. Developed on `C#`, `Owin`, `Web APIs`, `Identity Server`, with integrations to `AAD`, and `OKTA`.
* I modeled platform’s permission & authorization over `RBAC` standards and contributed to implementation of core permissions service to control resource access, it was built to load resources into distributed cache Redis and query user access permissions. 
* I designed & implemented internal API gateway providing reversed proxy entry point to all miroservices; handling cross cutting concerns such as authorization, auditing, and **distribute transaction using Sagas**. Built on Owin, `REST APIs`, `Redis`, `Azure Service Bus`.
* I designed & Implemented internal development platform, including resilient fault tolerant services, Throttling engine for APIs rate limiting, distributed transaction management using sagas, structured logging, and data management using `Event Sourcing/CQRS`.
* I designed & contributed to implementation of Continuous Integration and Delivery `CI/CD pipeline`, using several tools & frameworks to automate release process including `TeamCity`, `OctopusDeploy`, `Ruby Rake`, `PowerShell`, and `Azure Resource Manager Templates`.

## ✦ GoFormz’s Application Integration Platform

Leading the engineering group, I envisioned and designed the company’s **integration strategy**. I was responsible for the overall architecture of application integration platform [https://goo.gl/4hw9NY](https://goo.gl/4hw9NY) . With my team I built an extensible application development platform used by 3rd party integrators to build integration workflows, offering complete end-to-end data capture & automation experience through application platform. Applications including but not limited to `Salesforce`, `Box`, `Ignite`, and `Google Suite` were built, hosted, and ran on app runtime.

* I designed & implemented application framework, used by 3rd parties to build custom applications; offering application **metadata definition**, **versioning protocol**, **distribution marketplace**, application’s unit of work execution engine, and authentication framework.
* I designed & implemented an application runtime **cluster management algorithm** to balance and distribute work load between nodes based on application availability and current capacity using **node election patterns**, and **azure service bus messaging distribution**.
* I designed & implemented application runtime node **resiliency algorithm**, handling failure of long running commands, retrials, timeouts, fail fast for corrupt commands using **circuit breaker**, and **capacity distribution** using **bulkhead pattern**.
* I designed & implemented application runtime node **metric tracking framework**, measuring key metrics as number of commands executed, failed, retried, in a non-blocking manner using `.Net TPL`, `Rx`, and propagating data to dashboard built using `AngularJS`. 
* I contributed to design and implementation of backend services (**C#/REST APIs**) and data stores (**MongDB, and Azure Storage**) for application metadata & binaries storage, providing backbone for application marketplace, and application developer portal (`ReactJS`). 
* I designed & contributed to the implementation of **workflow engine**, empowering clients to define **business workflow** over data captured by GoFormz platform. I implemented **DSL compiler** to interpret workflows and translate it into **.Net IL code**.

## ✦ Cornerstone’s Edge Platform
As a member of platform team, I contributed to the design, architecture, implementation, and delivery of Edge platform [https://goo.gl/zf2uD1](https://goo.gl/zf2uD1) Cornerstone foundation of its **Platform-as-a-Service (PaaS)**. Enabling 3rd party developers to build and monetize business application on company’s talent management application platform. I was responsible of **domain language suite**, and **application execution cloud runtime**.

* I developed application’s development language (Shelby), implemented and delivered **Language DSL compiler** which generate intermediate platform language instructions to coordinate application actions throughout platform services.
* I co-designed and implemented Edge platform execution intermediate language, and built **platform runtime virtual machine** to execute and coordinate application instructions on platform’s cloud services.
* I contributed to implementation of platform data services engine to translate `OData 4.0` queries into in-memory object graphs descripted in **C# Expression Trees** and Compiled Queries for optimized data retrieval pipeline.
* I was a key member of small architecture group responsible for the overall platform design, implementation, and delivery using **microservices**. I developed many core services offered by the platform such as language, runtime, and cluster management services.

## ✦ Cornerstone’s Transformation Platform
Working with the data migration and transformation team [https://goo.gl/WDYgUW](https://goo.gl/WDYgUW) I was responsible for architecting next generation solution for mass data load & transformation from external systems. Challenged by defining complex transformation client’s workflows, efficient, and operate at hundreds gigabytes scale. I envisioned and built a platform for defining data transformation rules runs at mass on a large scale.

* I designed Lambda a **data transformation language** used by developers to write data transformation rules similar to the specification defined by business analysis team; I built **DSL compiler** to interpret Lambda’s rules to an optimized IL executed by runtime.
* I designed and built Rules Engine service written in `C#`, `WCF`, and `MSMQ`. Used by data transformation compiler to efficiently organize rules and create an **execution plans** for data to be loaded into system.
* I contributed to implementation of data wizard, used by clients to create, schedule, and manage, data transformation workflows.

## ✦ GE Healthcare’s Smart Room
As part of research & development group, I worked on building GE’s innovative next generation of hospital’s smart rooms, to help health professionals identifying & mitigating patient safety risks while offering meaningful solutions to improve patient outcomes. I was responsible for designing and developing services collecting sensory information from different room hardware sensors.

* I contributed to architecture and development of real time locating system **RTLS**, writing parsing engine to digest **RFID** tag’s beacons over several protocols `Radio Signals`, `Infrared`, and `Ultrasonic` from different vender such as `RFCode`, `Aeroscot`, `Cisco`, and `Centrack`.  
* I designed & implemented a pluggable RFID service, to interact with low level sensory from RTLS, designed using a PubSub to scale out for millions of beacons, then distribute to consuming apps. Built on `C#`, `.Net`, `Multithreading`, `WCF`, `Socket APIs`, and `ActiveMQ`.
* I was lead developer behind GE & Cisco project to its unified wireless network & context-aware software to manage flow of patients and medical assets. Bridging gap between WiFi sensory & RTLS systems, combined into one tracking solution. [https://goo.gl/2mgY6f](https://goo.gl/2mgY6f)  
* I implemented **indoor geometry locating algorithm** used by **RTLS server** to locate moving human & equipment indoors, using **triangulation & proximity algorithms** achieving high locating accuracy used by hundreds of health facilities around the world.

## ✦ GE Healthcare’s AgileTrac Hand Hygiene Platform
I was lead architect & engineer developing framework to accurately record, measure, and report hand-washing data throughout care facilities. Providing compliance platform for hand hygiene opportunities visualized using comprehensive metrics dashboards to determine success of facility’s sanitization program. [https://goo.gl/CHzfh5](https://goo.gl/CHzfh5)

* I architected & built **RTLS** for interacting with employee’s badges and sanitizer dispensers **RFID** beacons. I worked closely with Chief Hardware Designer to build data transmission protocols over wireless network using `Sockets APIs`, `WCF`, `C#`, and `ActiveMQ`.
* I contributed to the design & implementation of the core algorithm responsible for calculating hand hygiene missed opportunities, using **proximity and probabilistic algorithms**.
* I contributed to design & development of many services used by server to aggregate, store, and distribute information using `C#`, `ASP.Net`, `WCF REST`, `SQL Server`, `ActiveMQ`, and `Data warehouse`.
* I contributed to development of Platform interactive online dashboards designed for different users to monitor compliance workflow developed based on an **event-driven architecture** using `C#`, `Reactive Extensions (RX)`, `WCF`, `SQL Server`, `SSRS`, and `ActiveMQ`.

## ✦ Nuance’s OmniPage 16
Working with Microsoft & Nuance I was responsible for developing MS Office integration with **world’s #1 OCR software** [https://goo.gl/Bf4Q6p](https://goo.gl/Bf4Q6p) I developed an efficient service to interpret the output of **OCR engine** to newly developed standard **Open-Xml** office document format.

* I designed & developed interpreter to process binary files built by **OCR engine** to **Open-Xml** document structure using `C++`, `C#`, `XML`.
* I developed packaging component to compress generated Open-Xml artifices on MS standards generating readable office document.
* I contributed to the development of **OmniPage SDK** to enable OCR engine integration with **MS Workflow Engine** using `C++`, `C#`, `WF`.
* I contributed to the development of **OmniPage office designer** to customize document generation output using `C++`, `C#`, `WinForms`.

## ✦ Saudi’s National eGovernment Portal (Yesser)
As a senior software engineer, my team and I were responsible for design, architecture, and development of various module in the ambitious multi-million dollars program of Saudi Arabia to transform governmental workflow and transaction electronically. [https://www.saudi.gov.sa](https://www.saudi.gov.sa)

* I contributed to the design & development of national commerce module, managing millions of trade transactions verification and auditing. Solution developed using `C#`, `Asp.net`, `JavaScript`, and `SQL Server`.
* I contributed to the design & development of the national election module, managing local provenance assembly elections, the module handled voting process, candidate and voters registrations and verification following governmental workflows.

# Education

## ✦ Degrees

* **Master of Science in Computer Science**, MSC Jan 2012 • Maharishi University of Management • Fairfield, Iowa
* **Bachelor of Science in Computer Science**, BSC May 2004 • Minufiya University • Egypt

## ✦ Professional Certificates

* **Project Management Diploma (PMP)** • Training in RITI (Egypt) from  Oct 2007 to Mar 2008
* **Microsoft Certified Professional (MCP)**
* **Microsoft Certified Technology Specialist (MCTS)**

# Publications

## ✦ Speaker

* **Kalam Falsfa Podcast (Founder & Host)**: [https://kalamfalsfa.wordpress.com](https://kalamfalsfa.wordpress.com) A Weekly podcast in Arabic discussing philosophical topics such as knowledge, consciousness, identity, ethics, belief, justice and aesthetics. From Ancient Greek Philosophy, to Arab’s Kalam Philosophy, to Modern western philosophy.
* **Ask Developer Podcast (Co-Founder & Host)**: [http://www.askdeveloper.com](http://www.askdeveloper.com) An online audio/video podcast for technology & programming enthusiasts, the podcast is in Arabic and targets the Egyptian & Middle Eastern audience.

## ✦ Presenter

* Developing Scalable Micorservice Distributed Platforms.
* Compilers Construction.
* Building Domain Specific Languages.
* Data Transformation & Validation Rules Engine.
* Highly Efficient Agile Teams.
* Monthly Engineering Briefing at GoFormz Inc.

## ✦ Writer

Several articles, and publications on my personal blog such as **WCF in 10 minutes**, **What’s new in CLR 4.0**, **Agile+**, T**he Future of Programming Languages**, **Multicore Just-in Time**, **Unit Testing Wisdom**, and others. All articles can be accessed on my personal blog. [http://www.eknowledger.com](http://www.eknowledger.com)
