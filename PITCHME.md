@title[Title]

## Develop a service on cloud

---
@title[Table of contents]

### TOC

- IT infrastructure and cloud
- System design
- DevOps
- Deployment and monitoring
- Practice

---
@title[What is the infrastructure]

### Infrastructure

> Infrastructure is the fundamental facilities and systems serving a country, city, or other area, including the services and facilities necessary for its economy to function.

- https://en.wikipedia.org/wiki/Infrastructure

---

### Infrastructure (computing)

> Information technology infrastructure is defined broadly as a set of information technology (IT) components that are the foundation of an IT service; typically physical components (computer and networking hardware and facilities), but also various software and network components.

- https://en.wikipedia.org/wiki/IT_infrastructure
- https://en.wikipedia.org/wiki/Converged_infrastructure
- https://en.wikipedia.org/wiki/Dynamic_infrastructure

---

### Computer internal

![https://upload.wikimedia.org/wikipedia/commons/d/d8/Motherboard_diagram.jpg](https://upload.wikimedia.org/wikipedia/commons/d/d8/Motherboard_diagram.jpg)

---

#### Computer internal (brief ver.)

- Computing Unit
- Storage Unit
- IO/Bridge

Draw your system by above components!  
*The more abstract you think, the wider your view will be.*

---

@title[Cloud]

### Virtualization

> Virtualization refers to the act of creating a virtual (rather than actual) version of something, including virtual computer hardware platforms, storage devices, and computer network resources. It is as a method of logically dividing the system resources provided by mainframe computers between different applications.

- https://en.wikipedia.org/wiki/Virtualization

---

### Cloud virtualization

> Cloud Virtualization is the new computing paradigm and related businesses, as offered by companies. Cloud Virtualization is not a technology by itself, but rather - an architecture inside an existing framework. Cloud providers provide bare bones infrastructure allowing users to assemble it and use it in a number of ways.

- https://en.wikipedia.org/wiki/Virtualization#Cloud_Virtualization

---

### Cloud provider

- https://aws.amazon.com
- https://azure.microsoft.com
- https://cloud.google.com

*Should we know everything about them?*

---

I think we should know few things about them.  

**Let's see what they made.**

- https://aws.amazon.com/products/
- https://azure.microsoft.com/en-us/services/
- https://cloud.google.com/products/

---

And so,

- How do they make components?
- How do they category them?
- What services will they create?

Or,

- How abstract can you approach?
- How small can you divide?

---

There is simple points for you.  
Please think about,

- High availability
- Scalability
- Fault tolerance

How can we design a **very strong but cheap** service against users, fails or disasters?

---

@title[SLA]

### Simple design process

1. Predict **use cases** and a **scale** of users.
2. Find **weak points** of system.
2-1. Can't you find them? **Split** a system into more smaller one.
3. **Strengthen** your weak points with some technique like redundancy.

Before looking at what redundancy is, it might be helpful to look at the SLA.

---

### Service-level agreement

> A service-level agreement (SLA) is a commitment between a service provider and a client. Particular aspects of the service – quality, availability, responsibilities – are agreed between the service provider and the service user. The most common component of SLA is that the services should be provided to the customer as agreed upon in the contract.

- https://en.wikipedia.org/wiki/Service-level_agreement

---

### Failure

A service should work as expected, but it doesn't. Why?

- Bugs we didn't expected.
- User scale we didn't expected.
- User actions we didn't expected.
- A failure of external systems we didn't expected.
- A disaster we didn't expected.
- Unexpected things we didn't expected.

---

### Manage a failure

Then how?

- Test and deploy carefully.
  - Make rollback points.
  - Pack both of software and infrastructure.
- Make **scalable**.
  - Allocate more resources.
  - Automatic is better.
- Make **redundancy** to remove *Single point of Failure*.
  - Prepare standby resources.
  - Isolate and prepare a non-response.

---

### Monolithic vs Microservice vs Serverless

- *[Monolithic](https://en.wikipedia.org/wiki/Monolithic_system):* I can do it all by myself.
- *[Microservice](https://en.wikipedia.org/wiki/Microservices):* We are **integrated**.
- *[Serverless](https://en.wikipedia.org/wiki/Function_as_a_service):* Function as a service.

---

But please don't forget.

- Do not waste it.
- Borrow the power of **virtualization** and use the **right size** components.
- It not only makes the system **cheaper**, but also helps make it more **robust**.

Of course, you shouldn't forget *utilization factor* and *max capacity*.

---

@title[DevOps]

### DevOps

> **Dev**elopment **Op**erations is a software engineering culture and practice that aims at unifying development and operation. The main characteristic of the DevOps movement is to strongly advocate automation and monitoring at all steps of software construction, from integration, testing, releasing to deployment and infrastructure management.

- https://en.wikipedia.org/wiki/DevOps

---

![https://en.wikipedia.org/wiki/DevOps#/media/File:Devops-toolchain.svg](images/Devops-toolchain.png)

- https://en.wikipedia.org/wiki/DevOps#/media/File:Devops-toolchain.svg

---

### Infrastructure as code

> Infrastructure as code is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools. The definitions may be in a version control system. It can use either scripts or declarative definitions, rather than manual processes.

- https://en.wikipedia.org/wiki/Infrastructure_as_Code

---

### IaC Tools

- [Ansible](https://www.ansible.com/) *python*
- [Chef](https://www.chef.io/chef/) *ruby*
- [Puppet](https://puppet.com/) *python*
- [Terraform](https://www.terraform.io/)
- [AWS CloudFormation](https://aws.amazon.com/ko/cloudformation/)

---

### Continuous integration

> Continuous integration is the practice of merging all developer working copies to a shared mainline several times a day.

- https://en.wikipedia.org/wiki/Continuous_integration

Of course, consider with *infrastructure*.

- Every commit should be built and tested.
- Automate the build and keep the build fast.
- Test in a clone of the production environment.
- Make it easy to deliverables and automate deployment.

---

### Continuous delivery

![https://upload.wikimedia.org/wikipedia/commons/c/c3/Continuous_Delivery_process_diagram.svg](https://upload.wikimedia.org/wikipedia/commons/c/c3/Continuous_Delivery_process_diagram.svg)

---

For these things, we should

- manage development environment.
- manage release life cycle.
- manage test environment by virtualized system like docker and kubernetes.

---

### Development environment

> An environment or tier is a computer system in which a computer program or software component is **deployed and executed**. In industrial use the development environment and production environment are separated; often with several stages in between. This structured release management process allows phased deployment (rollout), testing, and rollback in case of problems.

- https://en.wikipedia.org/wiki/Deployment_environment

---

### Software release life cycle

> A software release life cycle is the sum of the stages of development and maturity for a piece of computer software: ranging from its initial development to its eventual release, and including updated versions of the released version to help improve software or fix software bugs still present in the software.

*Pre-alpha > Alpha > Beta > Release Candidate > Release to Marketing > General Availabily > Production or Live release*

- https://en.wikipedia.org/wiki/Software_release_life_cycle

---

Good. So we should,

- Design the system to be small and scalable,
- Integrate and manage both infrastructure and code,
- Abstraction of infrastructure to test like production,
- Continually test your code,
- Manage your deployment environment and steps well,
- Deploy appropriately to production.

But deployment seems difficult because there will be so many subsystems.

---

### Orchestration

- https://en.wikipedia.org/wiki/Orchestration_(computing)

> Orchestration is the automated arrangement, coordination, and management of computer systems, middleware, and services.

- [Docker swarm](https://docs.docker.com/swarm/overview/)
- [Apache Mesos](http://mesos.apache.org/)
- [Kubernetes](https://kubernetes.io/)

---

### Monitoring

- Are all systems green status?
  - Are all resources sufficient?
  - Are All users received expected result? 
- Collect system metrics and build a dashboard.
- Collect event logs and make them traceable.

---

### [12 factors](https://12factor.net/)

- **Codebase** One codebase tracked in revision control, many deploys
- **Dependencies** Explicitly declare and isolate dependencies
- **Config**  Store config in the environment
- **Backing services** Treat backing services as attached resources
- **Build, release, run** Strictly separate build and run stages

---

- **Processes** Execute the app as one or more stateless processes
- **Port binding** Export services via port binding
- **Concurrency** Scale out via the process model
- **Disposability** Maximize robustness with fast startup and graceful shutdown
- **Dev/prod parity** Keep development, staging, and production as similar as possible
- **Logs** Treat logs as event streams
- **Admin processes** Run admin/management tasks as one-off processes

---

@title[Epilogue]

### Practice more and more

So I recommend to you,

- Make it work,
- Make it scalable,
- Make it fault-tolerant,
- Make it deployable,
- Test it work as expected.

---

Something wrong if you repeat something many times.  
Make it work automatically.

Focus on more important things, such as **your domain**.

---

### Exercise

Try to design a system that already exists.

- [Pastebin](https://pastebin.com/)
- [Online judge](https://www.acmicpc.net/)

---

Split them into many fractions.

- Static front-end files.
  - Should we build our web server?
- Backend functionalities.
  - Is it read-intensive or write-intensive?
  - Is there need to ensure uniqueness?
  - How about concurrency? Should it use transaction?
  - What do the users really expect?
  - Is back-end really needed?

---

And discuss it with your friends!
