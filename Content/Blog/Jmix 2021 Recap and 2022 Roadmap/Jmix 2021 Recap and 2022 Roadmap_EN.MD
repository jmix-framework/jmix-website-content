# Jmix 2021 Recap and 2022 Roadmap 

One more year is almost gone, so it’s time for the traditional recap of what the team was working on and what we plan for the upcoming year.  

## 2021 

2021 turned out to be super busy, with extensive R&D and multiple new features in development. We have grown to over 60 to support all these activities. The adaptation of new members put high pressure on the rest of the team in the first half of the year, but proved worth it – now we are capable to undertake much more than we could imagine a year ago. 

The most important task was releasing a stable version of Jmix. [Version 1.0](https://jmix.io/blog/jmix-1-0-is-released/) was released in June, though to be honest I think we can only consider this task complete since the [recently released v. 1.1.](https://jmix.io/blog/jmix-1-1-is-released/) It brought multiple usability and stability improvements, and most of CUBA Add-ons supported by Haulmont were ported to Jmix.  

We understand that enterprise projects are long-living, so facilitating migration to the latest version of the framework has always been our priority. In Jmix 1.1 we implemented [a special compatibility module and Studio support](https://docs.jmix.io/jmix/cuba/index.html) for easy migration from its predecessor CUBA Platform. We hope to see more CUBA projects converted to Jmix soon.  

This year also gave birth to a new product – an IntelliJ IDEA plugin [JPA Buddy.](https://plugins.jetbrains.com/plugin/15075-jpa-buddy) In very simple words, we used the experience of working with data model in Jmix, and adapted it to generic Java and Kotlin projects using JPA. The success was beyond any expectations – over half a million unique downloads in a year! This proved that our ideas, presented as lightweight, non-invasive tools are appreciated by broad developer community. You are welcome to learn more in JPA Buddy’s [recap article](https://www.jpa-buddy.com/blog/the-first-annual-recap-from-jpa-buddy/).  

![logo jpa buddy]({{strapiUrl}}/uploads/Logo_JPA_Buddy_1b97eec30f.png)

You might think that JPA Buddy is irrelevant to Jmix community, however it brought an interesting side effect.  Such a small and widely popular tool has very fast feedback and release cycles. This in turn results in a very polished product with great developer experience. And we copy many of JPA Buddy ideas and features back to Jmix! For example, this is how we moved from custom DB migration scripts to industry-standard Liquibase.  

One major feature that we started is CloudControl, a project which extends Jmix with DevOps and cloud deployment capabilities. When it is rolled out, Jmix will support the full SDLC (software development lifecycle) of an application. CloudControl will support two scenarios:  

- one-click deployment from Studio directly to a public cloud like AWS, which is ideal for prototypes, one-man projects or demos;  
- a complete infrastructure and collaborative environment for managing and deploying your projects without the need for deep DevOps knowledge.  

Let me elaborate on the last point. Inline with our “do not reinvent the wheel” mantra, CloudControl relies on GitLab under the hood, and it can either procure you a fully configured instance, or connect to your current one. So, you get a ready-to-use issue tracker, CI/CD engine, git and binary artifacts repositories. On top of that CloudControl adds:  

- Code generation and drag & drop designers for Terraform, Docker Compose and Kubernetes, so you can easily describe the desired project infrastructure.   
- Procurement and management of environments for your project in a public cloud or a private Kubernetes instance 
- Code generation for standard CI/CD pipelines 
- Governance policies for access to projects and environments 
- Simplified and focused web interface, integrated with Jmix Studio  

In essence, CloudControl is a bridge between development tools, DevOps infrastructure, and environments.  

Another key direction of our work has been the new front-end technologies. Initially, we planned that the new React client would be a 1:1 alternative for Vaadin over generic GraphQL API. However, as we progressed with R&D, we realized that support for two equal UI clients turns Jmix into a mess: double documentation, different APIs, etc. Moreover, Jmix’s generic API approach encountered reservations among web developers, who are used to working with dedicated endpoints.   

The above made us reconsider our strategy. Jmix will retain Vaadin as the primary client and focus on seamless, pure Java/Kotlin full-stack development. In addition, Jmix Studio will automate generating custom REST/Graph QL endpoints (in addition to the generic API) to facilitate using a Jmix application as a backend. With this in mind, we started work on upgrading to the latest Vaadin 23 LTS release. 

However, the work we did on the React client is not lost. Recently, we released a beta version of [React Buddy](https://plugins.jetbrains.com/plugin/17467-react-buddy) – an IntelliJ IDEA/WebStorm plugin providing visual tools and coding assistance to React developers. Like with JPA Buddy, we hope that it will become widely popular and benefit the Jmix community. React Buddy can offer RAD experience for a React UI client over Jmix GraphQL endpoints with some additional work currently in progress. And being a separate product, it will not clutter the Jmix codebase. 

![logo React Buddy]({{strapiUrl}}/uploads/Logo_React_Buddy_a2e1766bdf.png)

As planned, we started R&D on the Flutter mobile client on the back of the same GraphQL API. Other smaller directions included such Jmix improvements as JPQL designer, support for code snippets, and a BPM designer in Studio. All of these are well on the way and look promising. Perhaps the only planned feature that we did not even start due to the lack of resources was support for design-time reports. 

Finally, in December we launched the new website. It was the first step in realigning our marketing strategy. We see that Jmix’s ease of use and high productivity resonate first of all among those who care about the business result: technical managers, freelancers, members of small IT agencies. So now we talk more about business values and position Jmix as a healthy alternative to the overhyped Low Code platforms: flexible, open-source, developer-friendly, and without crazy runtime fees.  

Together with the new product features, we hope that it will help us ramp up sales and see faster community growth. By the way, this year we have grown by over 20% with almost zero marketing activities – which backs our confidence.  

I want to finish off 2021 with a massive “thank you” to all our community members for understanding the reasons behind the recent price change. Your support is greatly appreciated and will help us build a better product and professionally maintain it in the future.  

## 2022

As you can see, we started multiple new directions this year. We made good progress, but most required extensive R&D work, and we did not even expect to finish them in one year. So for 2022, the ultimate goal is to complete this work.  

Here is a high-level release plan for the key features, and you can also track the live roadmap [here](https://github.com/orgs/Haulmont/projects/1). 

- Q1. JPQL designer, BPM designer, Business Calendar, and User Notifications Add-ons 
- Q2. Preview versions of CloudControl and the new Vaadin 23 UI client  
- Q3. Stable versions of CloudControl and the new Vaadin 23 UI client  

As discussed above, we keep working on making Jmix and React Buddy work together to offer faster React front-end development for your Jmix applications. I am confident that we can release something this year. Flutter work has been put on hold as we first focus on finalizing other projects.  

Of course, we also plan to release many other improvements and a few Add-ons this year. We also have one more major development direction, which I will keep secret and announce later in the upcoming year. Stay tuned!  

I hope that you will enjoy what’s coming for Jmix in 2022. Our team wishes you a great New Year and many successful projects. Thank you all for staying with us! Your ideas and suggestions are always welcome as comments in this [post](https://forum.jmix.io/t/jmix-2021-recap-and-2022-roadmap/919). 