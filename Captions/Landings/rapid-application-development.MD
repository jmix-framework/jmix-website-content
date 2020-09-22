### What is Rapid Application Development

Rapid application development (RAD) model was formalized by James Martin in 1991 as an alternative to the rigid waterfall processes. The classic waterfall approach works perfectly in construction and many other industries where scope changes are rare and expensive. If you started building a bridge, it is unlikely that you would swap it for a ferry halfway through the process.

Software development is much more flexible. There are more variations of how the same business challenge can be resolved, and at the same time changes are cheaper. As a result, super-detailed design and planning often lose out to the trial and error approach. Moreover, users tend to provide better feedback only when they see something working.

### The Rapid Application Development methodology shifts focus from costly planning to prototyping. In particular, RAD model implies the process division into four stages:

#### REQUIREMENTS PLANNING

At this phase, users and the project team identify the objectives of the future system. The focus is on reaching business goals and the requirements are rather loose. The ability to adjust or change them during the prototyping stage is key.

REQUIREMENTS PLANNING

USER DESIGN

CONSTRUCTION

CUTOVER

#### USER DESIGN
Here, developers start with working on a prototype. The goal is to demonstrate something to the client as soon and as cheap as possible. It is acceptable that the prototype only satisfies part of the requirements or covers only certain scenarios. It is acceptable to cut corners at the code level.

After the prototype is ready, it is presented to the users. The team collects all possible feedback and this is where initial requirements are subject to inevitable changes. Something which seemed right on paper may look totally different in a working application. With this feedback at hand, developers return to the prototyping step, until users are satisfied with the result.

#### CONSTRUCTION
Now we know exactly what needs to be done. It is time to develop and test the system so that it is ready for production use. No more cutting corners, the focus is on quality, scalability, maintainability, etc. However, users continue to participate even at this late stage, providing feedback as features get implemented.

What we have developed at the prototype stage might even be thrown in a bin, depending on the tool we chose and other circumstances.

#### CUTOVER
This is the final phase including acceptance testing, rollout and user training.

### Rapid Application Development Pros and Cons
##### RAD shifts the balance from predictability to agility, with consequent positives and negatives.

### PROS:
#### HIGHER QUALITY
With users deeply engaged at the prototype stage, the resulting software will likely be more relevant for their tasks. And in any case, it will match their expectations.
#### LESS COSTS AND RISKS
With the waterfall approach users only see results and provide feedback when the project is delivered. The inevitable changes at this stage are expensive and time-consuming. With RAD methodology the risk of re-writing half of the solution after it is rolled out is minimal.
### CONS:
#### LACK OF SCALABILITY
The RAD model assumes very close collaboration between the team and the end users. When the team is too big, or there are too many stakeholders, the prototyping process inevitably slows down. It also becomes hard to communicate frequent scope changes between everyone involved. Thus RAD is considered optimal for small or medium-size teams.
#### POOR DESIGN
Chasing specific business features and cutting corners at the prototyping stage can sometimes lead too far ending in poor overall solution design.
#### LACK OF CONTROL
For obvious reasons, it is impossible to plan scope, budget and time until the project is out of the prototyping stage. However, rough expectations can still be set based on the results of the requirements planning phase.
#### COMMITMENT FROM END-USERS
RAD methodology assumes deep involvement of users at all stages of the project lifecycle. This is especially true for the most knowledgeable experts in the business, who are apparently the busiest people in the company.

### Is RAD the same as Agile?
The RAD term predates Agile by 10 years, and for its iterative approach it is often considered a “parent” of Agile. However, this is not the case. While RAD is a prescriptive development methodology, Agile is a philosophical position, encompassing much more than just development.

It would be fair to say that RAD belongs to the family of agile software development methodologies, together with Scrum, Kanban and many others.

### Is Rapid Application Development applicable to my project?
##### As we have discussed above, RAD does not work in rigid environments. It is not applicable when:
* the budget and timeframes have to be known in advance.
* you do not have regular access to the users or they are not motivated to commit their time and energy
* the project requires a large team due to its scale, or an excessive amount of stakeholders

These conditions are often true for large business or governmental organizations. However, certain elements of RAD can be applied even in such cases. E.g. fixed price projects can budget for prototype stage and certain amount of changes. Prototype scope could be limited to the most uncertain parts, considering that you have relevant users on board.

On the other side, RAD approach works very well for small and medium businesses, or departmental projects, where business users own the budget and are motivated to get the results. A classic example is various Line of Business (LOB) applications - a general term describing applications developed to automate and run certain parts of business more efficiently.

Similarly, RAD is perfectly applicable to creating websites. These are typically small projects with a limited set of stakeholders, but involving them early is crucial as design is a very opinionated thing, and everyone will have something to say!

### Rapid Application Development Tools
The success of RAD methodology heavily depends on prototyping speed and close collaboration, thus choosing the right tools to support this is utterly important. Fortunately, there is a long list to choose from.

### DESIGN AND PROTOTYPING

Examples: Figma, Balsamiq, Invision, Sketch, Adobe XD

Tools like Figma and InVision enable graphic designers and UX specialists to quickly knock up and share with end users clickable prototypes with a complete design to collect their feedback. Once an iteration of the prototype is approved, the project can be exported to formats reusable by frontend developers, thus moving into the Construction phase. These tools are most widely used for creating websites, but can also be used for prototyping user experience of more complex end-user applications or portals.

Collaborative website design with Figma

Other tools like Balsamiq are more frequently used by business analysts. They are focused on prototyping user experience with wireframes, while the final design can be applied later. These are a good choice for the initial shaping of larger systems with complex user interaction.

Creating mockups in Balsamiq

### DEVELOPMENT

Development is usually by far the most time consuming, expensive and uncertain part of creating an application. So, modern RAD platforms combine proven architecture, ready components implementing typical features, and of course tools facilitating rapid development. All of them help you deliver results quicker both at the Prototyping phase of the project and further during Construction.

Consulting firms like Gartner and Forrester keep introducing new terminology to distinguish between these platforms: Low/No Code Application Platforms (LCAP), High Productivity Application Platforms as a Service (HPAPaaS), Multi Experience Development Platforms (MXDP). However, ultimately all of them can be classified by their target audience.

### LOW CODE / NO CODE PLATFORMS

Examples: Mendix, Outsystems

The key idea of these platforms is to enable business users with no development skills (referred to as power users or citizen developers) to deliver working applications very quickly. Of course, this simplicity implies lack of flexibility and multiple limitations. I have covered these limitations and associated risks in my previous article. As a result, the niche of such platforms is either prototyping or very basic systems.

### DEVELOPER-FOCUSED PLATFORMS

Examples: Embarcadero RAD Studio, CUBA Platform, Ruby on Rails

These platforms leverage the speed and joy of software development mostly by providing higher-level API and code generation - so developers are kept away from repeating boilerplate code and typical functionality.

Embarcadero RAD Studio, previously known as Borland Delphi, is one of the pioneers in this space, famous for its visual UI designer. It appeared before the web era and is still applicable only for desktop and mobile applications.

Other platforms focus on the web as it is a dominant channel for interaction with end-users these days. For example, at Jmix we try to join the convenience and speed of visual data model and interface design with the power of modern open source technologies. Such approach not only boosts prototyping speed, but also enables you to grow your prototype into a full-featured enterprise application with a solid and scalable architecture. You can get a feel of how it works in several minutes by following the Quick Start video on our website.

Designing an application screen in Jmix Studio

If you are interested to investigate RAD platforms and their evolution deeper, I would recommend a good article by my colleague Aleksey Stukalov for further reading.

### Summary
Rapid Application Development is one of the development methodologies following the agile philosophy. The key principle of RAD is a close engagement of end users and fast, iterative prototyping based on user feedback. When the users are happy, the focus is shifted to the delivery of production-ready software.

Choosing the right tool(s) is critical to ensure fast prototyping and thus the successful implementation of RAD methodology in a project. Luckily, there is a wide choice of tools and platforms aimed at different types of applications, stages of a project and team skillset.

RAD is an old concept, but today it is experiencing a renaissance following the trends of digital transformation and the push towards faster time to market. For the right types of projects and team setup, RAD methodology helps to achieve better user satisfaction with reduced risks and in shorter timeframes.
