### Jmix Roadmap 2021-2022

First of all, let me wish all of you a Happy New Year and congratulate on surviving 2020! It has been a rough year for the world, and I hope that 2021 will bring us more positive news. 

First of all, let me wish all of you a Happy New Year and congratulate on surviving 2020! It has been a rough year for the world, and I hope that 2021 will bring us more positive news. 
In this article I would like to recap the results of 2020 for our team, and share some plans for the upcoming 2021.

We kept mostly silent about our plans over the last year. I hope that now, as [Jmix is released](https://www.cuba-platform.com/blog/jmix-the-future-of-cuba-platform/), you can see why. The amount of changes and R&D work meant that it was just too hard to give promises. We needed to be flexible and move at a comfortable pace. 
But even though most of the team was focused on Jmix, we delivered some cool features for CUBA as well:
- Kotlin support and design-time security roles in [CUBA 7.2](https://www.cuba-platform.com/blog/cuba72-whats-new/) 
- The new [Helium](https://www.cuba-platform.com/blog/helium-announce/) theme with a visual theme editor
- Support for React Native in the frontend [generator](https://www.cuba-platform.com/discuss/t/frontend-20-1-beta-published/12275/10) 
- [CUBA SDK](https://www.cuba-platform.com/blog/development-in-isolated-network/), helping to develop your projects in isolated environments
  
Of course, there were hundreds of other evolutionary improvements in Studio, the framework and the frontend generator.

On the community side, we added [Italian](https://www.cuba-platform.it/) and [French](https://www.cuba-platform.fr/) versions of the website and forum. We also rolled out a simplified form for the academic license requests, so [more and more](https://www.cuba-platform.com/blog/cuba-platform-helping-it-education/) universities are using CUBA for their enterprise software courses! 
We welcome new big brands among our customers, including Ingenico and Sber - the largest bank in Eastern Europe. Sber has [signed](https://www.sberbank.ru/en/press_center/all/article?newsID=1ffbb179-f30e-4a14-b230-c04d38123fe5&blockID=1539&regionID=77&lang=en&type=NEWS) a large-scale agreement to adapt and use CUBA Studio to speed up the development of applications for in-house users across the whole bank.

## What’s coming in 2021?

The recent release of Jmix provides us a solid foundation, so we look  into the future with confidence. We have ambitious plans and currently we are scaling the team to support them. We expect that over 50 developers will be working on Jmix by the end of next year!

Our first priority is of course the release of a stable version of Jmix. This includes complete documentation, migrating remaining addons and thorough testing. We are aiming at Q2 2020 to finish this work. 

New features are described below. Keep in mind that many of them still require R&D so don’t ask me for implementation details. Still, this should give sufficient clue of where we are heading, and I hope you’ll like it!

### Frontend

Now, as our CUBA backend is rebuilt around Spring Boot, the most widely used server side technology for enterprise projects, it is time to shift focus towards the frontend. Well, to be honest, the time has come a couple of years ago, as Vaadin 8 got outdated. However, we always keep long term sustainability and backwards compatibility in mind. Unfortunately for us, the web frameworks world is changing so fast that it was hard to make a safe bet. Even the Vaadin components set [is still actively evolving](https://www.cuba-platform.com/blog/vaadin-10-evaluation/) in the latest releases. 
So we just had to keep Vaadin 8 UI which, with all its limitations, “just works”. Nevertheless, the frontend team was exploring new approaches in the portal module and recently in the TypeScript SDK and the React frontend generator. You can already scaffold React and React Native clients, though it is still a much more complicated and manual process compared to the Vaadin-based UI. You can plug in any other web framework with the help of Typescript SDK of course, but it is an even more manual process.

Anyway, the quest is over. We believe that React is “here to stay” for long enough. So the main focus for 2021 is to push React UI client to the state when it is as productive and as easy to use as Vaadin. Naturally, this assumes full support in Studio, including visual designer with screen templates, hot reload, theming, and a complete suite of components, at least equivalent to their Vaadin counterparts. As usual, we will try to abstract (not isolate) developers from the intricacies of the JS ecosystem to the possible extent. The benefits are obvious: faster and better scalable UI with wider customization options and massive community support.
However, there is also a price to pay. Basic understanding of Typescript, HTML, CSS will be required. You will also require the commercial IntelliJ IDEA Ultimate for comfortable work with Typescript. We plan to release a version of Studio bundled with it. 

What happens to Vaadin? No worries, its story also continues. We still believe that it is a great choice in many scenarios. It is perfect for backend developers who do not have much love for web stuff. Unless you expect tens of thousands of users or high latency networks it will perfectly do the job, and such assumptions are valid for most back office applications. We keep monitoring the progress of Vaadin folks in the latest versions, and we are expecting to be able to upgrade from version 8 to one of those in 2022. 

What about mobile applications? As mentioned above, we are already supporting React Native client generation, as well as PWA in the React client. In addition, we have started small-scale R&D around [Flutter](https://flutter.dev/), a very promising UI technology backed by Google. Flutter’s ultimate goal is to deliver a single UI technology for all platforms: mobile, web and even desktop. It will also be much more familiar to backend developers, while its ideology is similar to React: everything is a component (aka Widget) and UI is a function of state.
Flutter is gaining traction fast and is already the most popular choice for cross platform mobile apps, while web support is in beta. However, we are yet to see if it becomes mainstream. 

Our main use case - “line of business” applications - assumes manipulating with complex data graphs. So both Flutter and React require a convenient server-side API for this purpose. After some experiments, we ended up with GraphQL, which seems to be a very natural fit and which will become a shared part for both clients.

To wrap it up, Jmix will be supporting more options to deliver frontend of any scale and complexity, for both web and mobile platforms, and both for those who love and hate JS :) 

### DevOps and Clouds

For years, we considered deployment “out of scope” and focused purely on the development side of things. However, we get more and more requests to simplify this side of the application lifecycle too. So we decided to form a “DevOps” team within Jmix to handle this. The task is inline with our general approach: abstract (but - I’ll stress that again - not isolate) the developer from the specifics of underlying technologies like Jenkins, Docker, Kubernetes, Terraform and provide simple and convenient visual tools to configure your environments and CI/CD pipelines.

What this means in practice:
- Configuring, generating and publishing Docker images
- Configuring environments, e.g. test and production
- Describing required infrastructure using a visual designer - based on Kubernetes and Terraform
- Configuring CI/CD pipelines
  
We are planning to rely on public clouds infrastructure - AWS to start with - for part of these features. But AWS (Azure, Alibaba, etc) offers so much more than just hosting your app, that it would be a crime to ignore its capabilities! So we will give you a choice to build truly cloud-native applications on top of cloud services including database, file storage, authentication, full text search, monitoring, logging, load balancing, etc. 

The ultimate goal is to provide you everything to deploy and run your applications in the cloud with minimal efforts. As this is an absolutely new direction, it is hard to declare deadlines. But we are aiming to release a beta version at the end of 2021.  

### Tools

Studio team is gradually becoming the largest in Jmix. Indeed, every direction, be it cloud or frontend, assumes relevant tooling support on the Studio side. In addition, we want to introduce some important enhancements this year:
- New visual designers - for JPQL and GraphQL queries, string messages and simple logical expressions. I hope everyone will love the idea of not having to write JPQL strings!
- Code generation based on templates for typical actions: open a screen, save/load data, show message, invoke a service, start a business process.
- Visual reports configuration at design-time. 
- BPM processes configuration at design-time.

### Moving things to design-time

I would like to highlight the last two features. Up till now, both Reporting and BProc addons only supported configuration at runtime. From one point of view, this is great: reports and business processes can be configured by non-developers without the need to redeploy the application. However, this has a number of side effects:
- If the data model changes, your report or business process may stop working, and you will not even notice it until you run it. 
- Instances of reports and business processes might easily get out of sync between different installations of an application. You may be testing one version on the test stand, at the same time someone changes something in production…
- For complex reports, a developer has to use inconvenient runtime code editors.
- When configuring a business process, a developer has to switch back and forth between Studio and a running application with frequent restarts to add new forms, services, etc.  
  
All in all, this becomes a fragile and cumbersome process, leaving lots of room to errors. Considering this, we decided to implement BPM and report designers in Studio. 
The option to build reports and edit business processes at runtime will also be preserved. You may notice that this is inline with the recently implemented design time support for access groups and security roles.

For reports, this means that a report is becoming a Java class, configured using a Studio wizard. This enables compile time validation, ability to test and debug reports and better visual tools. 

For BPM, the idea is similar. Design-time editor will enable testing and debugging process definitions, as well as creating many things inline: services, forms, handlers and so on. This will result in a seamless developer environment, powerful enough to compete with some BPMS solutions on the market.  

As many other features, we are aiming to release a beta version of these new tools at the end of 2021. 

### Timeline  

Here is the timeline to summarize the expected releases for your convenience:
- Q2 2021 - stable version of Jmix
- Q4 2021 - stable version of the React client
- Q4 2021 - beta versions of:
&nbsp;&nbsp;&nbsp;&nbsp;- DevOps and Cloud tools
&nbsp;&nbsp;&nbsp;&nbsp;- cloud native applications support
&nbsp;&nbsp;&nbsp;&nbsp;- visual reports and business processes configuration at design time
&nbsp;&nbsp;&nbsp;&nbsp;- other tools in Studio
- Q2 2022 - stable versions of everything released in Q4 2021

This is a challenging schedule and some deadlines might slip, but we are determined to do what’s possible to stick to it.

### The Future

Implementing everything described above will mean that Jmix becomes a powerful platform for building modern enterprise applications, providing:
- Scalable UI for mobile and web applications
- Cloud native capabilities and full deployment automation 
- More visual tools, facilitating productive development and easier onboarding
 
In fact, Jmix should become a strong competitor on the blooming Low Code Application Platforms (LCAP) market. With at least the same level of productivity, Jmix addresses many of the LCAP shortcomings, so we hope it will be a fresh breeze on this controversial market. 
Jmix is built for and offers a comfortable working environment for developers, while most LCAPs are focused on business users (aka “citizen” developers) and hence provide poor developer experience. Jmix is also open and flexible enough to build even the most complex applications like ERPs - this fact has been proven multiple times by our community projects. Finally, unlike most LCAPs, it is built around an open source framework - meaning that your applications are truly yours. 

We hope that this combination of Jmix features will help you deliver powerful yet beautiful applications in record time, and will be attracting new members to our community. As usual, your feedback is much appreciated - feel free to leave your comments on the forum or contact us directly. 