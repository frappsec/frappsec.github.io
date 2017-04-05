---
layout: page
title: Framework for Application Security
permalink: /FrAppSec/
---

[v2017.1](/about/#history)

___

<!-- MarkdownTOC depth=3 autolink=true autoanchor=true bracket=round -->

- [Introduction](#introduction)
  - [Pitfalls of the traditional approaches](#pitfalls-of-the-traditional-approaches)
- [Business Case](#business-case)
- [Definitions](#definitions)
- [Risk Management](#risk-management)
  - [Risk calculation](#risk-calculation)
    - [Application criticality](#application-criticality)
    - [Traditional vulnerability risk scoring](#traditional-vulnerability-risk-scoring)
    - [Vulnerability risk scoring in the business context](#vulnerability-risk-scoring-in-the-business-context)
    - [Application risk score](#application-risk-score)
  - [Risk appetite](#risk-appetite)
  - [Prioritizing mitigation work](#prioritizing-mitigation-work)
  - [Production and development applications](#production-and-development-applications)
- [Actors](#actors)
  - [Perspectives](#perspectives)
    - [FrAppSec Q Matrix](#frappsec-q-matrix)
    - [Activities](#activities)
- [FrAppSec Taxonomy](#frappsec-taxonomy)
  - [Layers](#layers)
  - [Organization](#organization)
- [Service catalog](#service-catalog)
- [Putting it all together](#putting-it-all-together)
- [Supporting documentation and templates](#supporting-documentation-and-templates)
  - [Useful and referenced links](#useful-and-referenced-links)

<!-- /MarkdownTOC -->
___

_FrAppSec_ or the _Framework for Application Security_ is a model for the organization of a successful application security program at an enterprise level.

<a name="introduction"></a>
# Introduction

Application security has evolved as a discipline and supporting function for application development over the past decades. The efforts for a consistent approach have usually been focused around the development lifecycle and have been less concerned with the overarching requirements and activities at an enterprise level.

The Framework for Application Security aka FrAppSec is the blueprint providing a holistic view of the application security landscape, identifying the actors involved in the process, their needs and ways to achieve those needs. The end goal is to deliver the acceptable level of security with the minimum amount of investment.

FrAppSec is also concerned with flexibility and provides a practical approach for smaller teams that want to deliver secure applications.

Over the past few years, application security started to get recognition as an independent and relevant discipline in the information security field.

[ISC2](https://www.isc2.org/) introduced a new domain as part of the [CISSP](https://www.isc2.org/cissp/default.aspx) certification called &quot;Software Development Security (Understanding, Applying, and Enforcing Software Security)&quot; accounting for 10% of the exam questions. CISSP is seen as one of the major certifications for information security professionals (e.g., Director of Security, Chief Information Security Officer) and the introduction of this individual domain is a reflection of the their agenda. The main topics for Software Development Security listed on [their website](https://www.isc2.org/cissp-domains/default.aspx) are:

- Security in the software development lifecycle
- Development environment security controls
- Software security effectiveness
- Acquired software security impact

[SANS](https://www.sans.org/) and more recently the Center for Internet Security ( [CIS](https://www.cisecurity.org/)) included &quot;Application Software Security&quot; in their critical [security controls list](https://www.cisecurity.org/critical-controls/). The security controls list is a starting point for strategic security architectural roadmaps. It provides a generic prioritized approach and a dissemination of the controls into more actionable items. The scope of the Application Software Security control is to &quot;manage the security lifecycle of all in-house developed and acquired software in order to prevent, detect, and correct security weaknesses&quot;. Nine sub-controls are emphasizing:

- Patch management
- Application level firewall
- Input validation
- Automated security testing
- Suppression of error messages
- Separation of environments
- Hardening and testing in depth
- Security training for developers
- Suppression of development artifacts

_The Building Security In Maturity Model (_ [_BSIMM_](https://www.bsimm.com/about/)_) is a study of existing software security initiatives. By quantifying the practices of many different organizations_, it describes _the common ground shared by many as well as the variation that makes each unique_. _BSIMM is not a &quot;how to&quot; guide, nor is it a one-size-fits-all prescription. Instead, BSIMM is a reflection of software security._ The aim is to measure and report the activities, not judge and propose models. All in all, BSIMM is structured in 4 domains, 12 practices and 113 activities:

- Governance
  - Strategy &amp; Metrics
  - Compliance &amp; Policy
  - Training
- Intelligence
  - Attack Models
  - Security Features &amp; Design
  - Standards &amp; Requirements
- SSDL Touchpoints
  - Architecture Analysis
  - Code Review
  - Security Testing
- Deployment
  - Penetration Testing
  - Software Environment
  - Configuration Management &amp; Vulnerability Management

Other initiatives are also addressing aspects related to application security. One of the most notable is [OWASP](https://www.owasp.org) (Open Web Application Security Project). As the name suggests, the initial focal point was web applications' security but the initiative grew over time to cover other aspects of the more general application security. According to their core purpose, OWASP is _the thriving global community that drives visibility and evolution in the safety and security of the world's software_. There are numerous projects addressing various aspects, starting from documentation to technology and support for application security. The quality of the projects varies and investigation is necessary in order to identify if the information is up to date or still relevant. The [flagship projects](https://www.owasp.org/index.php/OWASP_Project_Inventory#tab=Flagship_Projects) are more reliable since they are usually funded and regularly maintained.

One of the OWASP flagship projects is the [Software Assurance Maturity Model](https://www.owasp.org/index.php/Category:Software_Assurance_Maturity_Model) (SAMM), _an open framework to help organizations formulate and implement a strategy for software security that is tailored to the specific risks facing the organization_. It has a similar structure to BSIMM, 4 business functions, 12 security practices and 3 levels of maturity for each practice.

The examples above are just a drop in the ocean of research, publications, tools and other elements related to application security. We can easily be diverted by the massive amount of available information and lose focus when building a consistent approach to application security. Paralysis by analysis becomes likely and can be followed by the tendency to over simplify or simply ignore the problem.

Certain patterns or recurring themes can be identified. While efforts have been made to build a one-size fits all approach, the reality is that particular situations require particular solutions which can in turn be based on more standardized but also abstract themes.

FrAppSec doesn't hold all the answers nor is providing specific solutions but delivers the blueprint on which layers of abstraction can be disassembled to reach actionable items in order to achieve the end goal.

<a name="pitfalls-of-the-traditional-approaches"></a>
## Pitfalls of the traditional approaches

The main pitfall of the traditional approach on application security is the lack of consistency, doing whatever comes in hand and not having appropriate knowledge or proper understanding of all the aspects of an application. All the other pitfalls derive from this and it is a broader concept which is also applicable in other areas. Poor understanding of the problem will lead to poor decisions by the management which will in turn propagate down the organizational chart.

Some people have and unfortunately, still are, considering penetration testing equal to application security. While it is a vital part of the development lifecycle and later in production, it is a blind process to certain aspects depending on the rules of engagement. It also comes too late in the application development process and therefore the cost of mitigation is high.

Application security budget increase is another approach which will not generate the expected results if it is not planned properly. As a business function, application security has to deliver the best return on investment for every monetary unit spent. Resources are necessary to deliver results, but how much is needed and how to distribute them is a byproduct of implementing a consistent approach like the one proposed by FrAppSec.

Focusing the investments around technology and neglecting the other aspects such as people and processes is not going to deliver results either. Buying expensive tools without the knowledge of how to use them and the manpower to do so can be a dead end.

The automation of security testing is important for large scale implementations. However it must be seen as an initial activity in a maturity model and should not be used as the only way to assess the applications' security. Depending on the risk profile of the application in question, manual security testing becomes a mandatory task. Automated tools detect only what they were programed to detect and do not provide sufficient testing coverage. They are usually unable to detect problems in the business logic and other multi-step attack vectors.

Snapshot security can also give a false sense of security. Annual audits provide a snapshot of the situation at a particular point in time and typically have a very limited coverage. Relying solely on these audits rather than a continuous process allows for extended windows of opportunities for attackers.

Trusting third party components by default is also a pitfall. Just because they come from a third party, it should not be assumed that they have a proper application security process in place. Open source libraries are a particular example of third party components which might be trusted by some because they have existed for a long time and are regularly updated. However this does not guarantee that security was ever considered. Building trust is a lengthy process and one that requires regular checks that the security bar is still at an acceptable level on the third party's side. A party able to deliver secure applications today might change completely in a year's time.

<a name="business-case"></a>
# Business Case

Digital transformation is embraced by companies who want to stay relevant in the current  economic landscape. The new constant is change and this is driving the agile approach to development of new business opportunities. Industries realized that they will no longer be relevant without leveraging the potential of new technologies.

We have to look no further than the Blockbuster vs Netflix case to understand the need for adoption of technology as an enabler to remain relevant in a changing market. Netflix started as a competitor to Blockbuster, renting hard copies via post but managed to leverage the Internet and the increasing bandwidth capacity, eventually taking their competitor out of the market. Digital markets are less stable than traditional ones and niche players can make a difference with limited resources. Disruption is the name chosen to depict the rapid paradigm shift.

The abundance and quick development of technologies is a blessing for adaptive organizations and a curse for traditional ones. This challenge was recognized by Gartner when coining the concept of Bimodal IT. This way, an established business can set a Mode 2 independent group to be less constrained by governance and more able to quickly react to changes in the environment.

At the heart of digital transformation lies the ability to process information efficiently. With Moore's law losing relevance, the focus now is on building software to do more, create connections and learn unassisted from apparently dispersed data. Software became indispensable to our everyday life and increased productivity exponentially.

Software development emerged as a discipline and moved to become a major economic driver in just a few decades. It's amazing strength is the large availability of tools to build more software. Anybody can write software given the knowledge. In the physical world, one needs materials, tools and knowledge to build things. All these have been refined over centuries and unfit products in the physical world rule themselves out or are regulated. This is not necessarily the case for software and it shows in the abundance of defects that software products are shipped with.

A particular set of software defects are the security vulnerabilities. What makes them different from other defects is that they can be abused by malicious actors for profit or for other malicious acts. We have seen examples of security vulnerabilities which not only reduced the value of the companies producing or using insecure software but, in certain cases, endangering the very existence of the business. Larger organizations have better resilience when faced with the exploitation of security vulnerabilities but the shareholders won't be happy with the value reduction of their assets. The long term impact of a security vulnerability is the decrease of customers' trust in the organization. One of the major themes of Digital Transformation is the Client Centric approach and thus a decrease of trust is a measurement of failure to meet the business requirements.

When we're talking about software, we're usually referring to a set of instructions telling the hardware what to do. In a real world scenario, multiple sets of instructions are used to create a complex environment, an application, from which the an entity, end user or business, can benefit. The application is a much more complex ecosystem since it is dependent not only on the instructions but also on the environment.

Traditional organizations failed to accept application security as a major discipline in the same way that traditional companies failed to adopt new technologies. Treating application security the same way as network security is a flawed approach since the application environment is rarely under control. Another pitfall of the traditional approach is to approach application security solely from a compliance perspective. A soft approach of compliancy lacks the necessary means to check and enforce the technical side of application security.

Most applications are not stand alone blocks but rather they depend on a multitude of interconnected  applications to deliver the desired functionality. In an effort to simplify the architecture, development teams are relying on third parties to provide information and they treat them as black boxes. Black boxes might rely on other black boxes and so on, generating a very complex architecture for those willing to go into details. If the trust model between the boxes is overlooked, then the security level of the application is reduced.

The key application security challenge is to manage complexity. This is nothing new at the enterprise level, as other departments are facing the same challenge. Layers of abstraction must be build to offer relevant views to various actors and an overview for the upper management.

FrAppSec or the Framework for Application Security is providing a feasible approach for dealing with securing applications. It's focal points are:

- Business case. What are the things that can be achieved with minimum investment and maximum velocity in order to match the risk appetite.
- Risk Management. A business conscious approach takes the risk appetite as a major enabler in pursuing business opportunities.
- Actors and Perspectives. Different roles in the organization need  different views on application security for improved efficiency. Centralization of perspectives rather than stacking them up in a pyramid provides a better understanding of the application.
- Taxonomy. All elements of a functional ecosystem must be optimally interconnected. FrAppSec provides the blueprint for achieving this.
- Flexibility. Providing a framework that is customizable to fit small groups, enterprises, anything in between and all the possible combinations.

<a name="definitions"></a>
# Definitions

This chapter is of importance because several ambiguities appeared over time in respect to how some of the terms are used. The following definitions and explanations depict the spirit in which they are used in FrAppSec.

**Application**

In the context of the current framework, _an application is a set of digital instructions designed to perform a group of coordinated functions_.

FrAppSec needs a unified definition to include all flavours of applications that are in the scope of the framework but also leave outside those paradigms which are not suitable. The term _System_ was avoided as it usually goes beyond the digital boundaries and includes hardware as part of the concept.

In practice, defining an application and its boundaries is more complex as the application is evolving and merging with other applications to deliver ever more enhanced sets of functions. A good rule of thumb is to apply the [divide and conquer algorithm](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithm) until the application is reaching a manageable size and can be addressed within the limits of the framework and according to the maturity level of the organization.

**Application Security**

_Application Security is the group of activities performed before, during and after the lifecycle of the application._ As an enterprise program, application security is dedicated to  managing the resources to perform the activities in an optimal fashion.

In a broader context, application security includes the paradigms and actors outlined in the FrAppSec Taxonomy.

**Business Owner**

_An application business owner is the entity who holds the rights to run the application in an attempt to profit from the successful operation._

Individuals are preferred over group ownership as they will have to sign for risk acceptance.

Not that the profit is not always monetary, an example would be the business support applications like an office suite which don't generate financial value directly.

**Security Champion**

_Security champions are the satellites of the Information Security function in other departments. They are active members of their departments, acting as subject matter experts in security related issues._

Security champions can and should be found in both non-technical (business) teams as well as in the technical implementation teams. They are usually hired by the department in which they activate and have a percentage of their time allocated to the security agenda.

**Application security audit**

_An application security audit is a measurable and repeatable technical assessment of the application's security against a specified baseline._

Traditionally, the application security audit is perceived as a non-technical compliance check.

It's important to have a strict ruleset around audits including:

- The scope
- Methodology
- Standard output (like reporting)
- Clear baselines (standards, best practices)
- Timeframe
- Observations outside the scope of the audit but with an impact on the outcome (blockers)

**Static analysis**

_The practice of analyzing the source code of the application in order to identify potential vulnerabilities._

The activity is usually conducted with the help of automated tools and the results are manually reviewed. It can and should be integrated as part of the continuous integration pipeline, defects must be triaged, tracked and fixed.

**Dynamic analysis** or **Penetration testing** or **Pentesting**

_Dynamic analysis is a runtime simulated attack on an application that aims to identify and potentially exploit security weaknesses, with the goal of gaining access to the application's functions and data._

It can be automated, manual or anything inbetween. Depending on the information that is provided to the expert performing the activity, it can be white, grey or black box.

A white box approach means that the expert gets everything, from documentation to access to the infrastructure. He can conduct interviews with the actors involved to understand the functionality of the system and find flaws in the operating processes, not just on the technology side. The white box approach is highly desirable but not always feasible.

In a black box approach, the expert gets the minimum necessary information to isolate the scope. It is perceived as a real world type of exercise. It's far less efficient that the white box approach as the expert has to spend time gathering information.

Most of the dynamic analysis is a shade of grey box testing. The rules of engagement are important to maximize the return on investment and focus the attention on the important items. At a minimum they should include:

- A clearly defined scope
- Contact people
- Communication protocol
- Clear authorization for the analysis
- Timeline
- Generic methodology
- Particular methodology to match the scope
- Generic checklist against standards and/or best practices
- Particular focus areas

<a name="risk-management"></a>
# Risk Management

Risk management as a broader concept is the identification, assessment and prioritization of risks followed by an economical application of resources to minimize, monitor, and control the probability and/or impact of unfortunate events or to maximize the realization of opportunities.

Risk management's objective is to assure uncertainty does not deflect the endeavor from the business goals.  ([https://en.wikipedia.org/wiki/Risk\_management](https://en.wikipedia.org/wiki/Risk_management))

Risk appetite is the level of risk which an organization is willing to tolerate.

For application security this means that a successful program must measure the risk posture of applications and, if need be, apply controls to reduce the risk to an acceptable level.

<a name="risk-calculation"></a>
## Risk calculation

When measuring risk, it's important to differentiate between several concepts which might seem related, but they reflect different aspects.

<a name="application-criticality"></a>
### Application criticality

Application criticality provides the business context and is an indicator for application security spendings. It can be expressed in absolute terms or relative to the other applications. Without this context, all applications have the same importance in the face of the auditor, thus they will get an equal share of the resources. This situation is unlikely and resources must be spent in order to provide the best return on investment.

The business owner is responsible for providing this figure which is a variable for the risk calculation formula.

One way of determining the application criticality is to look at the revenue or profit generated by that application. This is not always correct, as some applications might not generate revenue but support other applications that do so. Also, strategic applications might not yet be profitable during the initial iterations but are still critical for the success of the business.

The security function must align with the business owners and upper level strategy staff in order to determine this scale which is critical for the success of the application security program.

A sample application criticality scale in absolute terms:

| How important is the application for the business? | Score |
| --: | :-: |
| Very important | 3 |
| Important | 2 |
| Not important | 1 |

Once the absolute terms have been determined for all the applications, a relative scale can be computed. Here is an example:

| Application | Absolute criticality <br>(e.g. a maximum score of 10) | Relative criticality |
| --: | :-: | --- |
| App1 | 9 | 100% or 1 |
| App2 | 7 | 77.7% or 0.78 |
| App3 | 3 | 33.3% or 0.33 |

In an established enterprise, the applications' inventory and criticality is maintained by an enterprise risk management function. A less established environment can create the processes in order to map the applications for inventory and calculate the system criticality based on interviews with the business owners.

<a name="traditional-vulnerability-risk-scoring"></a>
### Traditional vulnerability risk scoring

An application vulnerability is a flaw that could be exploited to compromise the desired secure state of the application. Vulnerabilities are identified during the activities performed throughout the lifecycle of the application.

The risk associated to a vulnerability is expressed as the product between the likelihood of exploitation and the impact following a successful exploitation of that vulnerability.

Vulnerability Risk (VR) = Vulnerability Likelihood (VL) \* Vulnerability Impact (VI)

$$ \boldsymbol{VR = VL * VI} $$

A sample vulnerability risk scoring matrix with a scale of 3 for likelihood and impact:

[![vulnerability risk scoring matrix](/FrAppSec resources/vulnerability risk scoring matrix.png)](https://github.com/frappsec/frappsec.github.io/blob/master/FrAppSec%20resources/vulnerability%20risk%20scoring%20matrix.xlsx){:target="_blank"}

Color coding is used in conjunction with the risk appetite statement to illustrate the zones which are not accepted.

<a name="vulnerability-risk-scoring-in-the-business-context"></a>
### Vulnerability risk scoring in the business context

The traditional approach of risk calculation lacks the business context. Consider the exact same vulnerability affecting a business critical application on one hand and a sandboxed test environment application on the other. The business will be far more interested in fixing the business critical application vulnerability if it is outside the risk appetite.

Efforts have been made to include this factor in the impact element of the traditional risk calculation formula. However it is a forced approach and most of the times the auditor is blind to the business context.

A better vulnerability risk scoring formula includes the relative application criticality (RAC) of the application which can be easily passed to the auditor or applied afterwards.

Considering the above application criticality scale, we can derive the relative application criticality needed for the formula.

| How important is the application for the business? | Score | Relative application criticality |
| --- | --- | --- |
| Very important | 3 | 1 |
| Important | 2 | 0.66 |
| Not important | 1 | 0.33 |

<br>

The formula for vulnerability risk scoring calculation is now:

$$ \boldsymbol{VR = VL * VI * RAC} $$

This formula addresses the problem presented above. The exact same vulnerability will have different scores depending on the relative application criticality (business context) and will be addressed differently.

It's useful to create separate risk scoring matrices for each level of relative application criticality.

<a name="application-risk-score"></a>
### Application risk score

Once all the vulnerabilities have been identified an overall application risk score (ARS) can be calculated as the sum of all the individual vulnerability risks (VR).

$$ \boldsymbol{ARS = \sum_{i=1}^n VR_i} $$

If color coding is used for vulnerability risk scoring, the application risk score will have the highest vulnerability risk color code.

The application risk score tells two things:

- The total amount of risk for a particular application
- The highest level of risk for any particular vulnerability

Thresholds can be set for both indicators in terms of risk appetite. For example an enterprise might not accept individual vulnerabilities above a certain score. On the other hand, if an application doesn't have any vulnerability with a risk above that level but has too many vulnerabilities below that risk score, a threshold can be set for the total amount of risk which must be met by the application.

<a name="risk-appetite"></a>
## Risk appetite

Risk appetite is the level of risk that an organization is prepared to accept in pursuit of its objectives. For application security, risk appetite statements can be prepared for three situations:

- Individual vulnerabilities
  - Example: The organization does not tolerate any vulnerabilities with a score higher than X
- Application risk score
  - Example: The organization does not tolerate applications with a total risk score higher than Y
- Enterprise application risk score (the sum of ARS of all the applications)
  - Example: The organization does not tolerate an aggregate enterprise risk score (the sum of all the application risk scores) above Z

<a name="prioritizing-mitigation-work"></a>
## Prioritizing mitigation work

Prioritizing the order in which vulnerabilities are mitigated is guided by the risk statements.

For individual vulnerabilities the situation is straight-forward, all vulnerabilities with a risk score above the appetite must be fixed.

In case the application risk score exceeds the risk appetite but no individual vulnerabilities are above the previous risk appetite statement, a top-down approach is recommended, fixing the vulnerabilities with the highest risk score. Another approach is to have a good relationship with the development and business teams in order to identify the vulnerabilities that are most cost-efficient to mitigate while still managing to meet the risk appetite statements.

<a name="production-and-development-applications"></a>
## Production and development applications

When assessing application risk, the applications can be in two stages: production and pre-production.

For pre-production applications, the policies and procedures can prevent the application from making it to the production environment until the risk is below or equal to the organizational appetite.

For applications which are in production, the policy or procedure must specify a deadline for mitigation.

A sample situation where the risk is expressed on a scale of three:

| **Vulnerability Risk** | **Time to mitigate (production applications)** |
| --- | --- |
| High | 5 days |
| Medium | 30 days |
| Low | Risk accepted |



<a name="actors"></a>
# Actors

This chapter aims to identify the important individuals or groups who are involved in application security. These are not all the actors and depending on the organizational structure others might be identified. Clearly identifying the actors and their responsibilities is necessary to build a functional RACI matrix and the framework processes.

**Chief Executive Officer** - the head of the business is ultimately responsible for risk, including information security related risks. He or she needs to be informed on the aggregated risk of applications and consulted whenever risks are above the enterprise appetite.

**Application Business Owner** - the most senior business role involved in the application lifecycle. This individual is able to make critical decisions within his or her mandate in respect to information security. Clear identification of this role for every application is crucial in respect to risk acceptance and go / no-go decisions.

**Data owner** - the individual responsible with the ownership of the information processed by the application. This actor is responsible for creating and monitoring the roles and permissions which grant access to data.

**Project manager** - the organizer. Making sure that all the actors are synchronized and aiming towards a common goal. With respect to application security, the project manager makes sure that there are no blind spots in the process and the security team is aware and prepared to support the development efforts. The project manager must be trained in the process of application security and involve the relevant parties at the proper time. Maintaining the security calendar is also a part of the project manager's role.

**Architect** - comes in several flavors: business, enterprise, domain, solution, security, etc. The IT Architect is combining Information Technology resources to meet business requirements. Depending on their role, they view the application from a different perspective. At each layer, fundamental security principles, generic security requirements and specific technical requirements must be known, understood and applied. The security architect is usually operating at an enterprise and not on an application level. However he can provide guidance for the other architects to make sure that security is embedded in the application and not added as an extra layer.

**Developer** - the actor in charge of building the application. A traditional view of the role would point out that the actor is responsible for writing code. In today's world the developer has more attributes, which can include among others deployment and operations. This is the role ultimately responsible for producing secure code.

**Auditor** - in charge of checking the compliance. The auditor has a compliance list to check against. Can be technical or non-technical (list checking).

**QA Tester** - testing the functional requirements. All the functional security requirements can be tested during the QA phase. Criteria for non-functional requirements can be set in order to derive specific tests that can be performed by QA specialists.

**Head of Information Security (CISO / Director / Manager)** - the leading role of the information security department. In charge with the strategy for application security, responsible for the necessary policies and procedure, taking care of the obtaining and distributing the resources.

**Security Tester / Penetration Tester** - the technical actor in charge of identifying vulnerabilities. The security tester must act structured and procedural within the time constraints that apply for a particular test.

**Security Champion** - this actor is usually part of the development team, has been identified through training or other means and is showing a genuine interest in information security. The security champion is in charge of relaying the messages between the information security department and the development team, both ways. He acts as the point of presence for the information security department within the development team. A formal designation and recognition of the role and time allocation for security specific activities is needed in order to empower the security champion to act on behalf of the information security department.

These are not all the possible actors and depending on the particularities of the organization more or less actors will be involved in the application security process.

Dealing with too many actors might be an overhead so we can group them based on interests:

- Executives - defining the strategy and owning the risk
- Architecture - transforming the business strategy and describing the technological functions to achieve the goals
- Development - building the applications that are supporting the strategy based on the instructions provided by architecture
- Security - an overarching group whose goal is to make sure that the applications supporting the business strategy are meeting the risk appetite

Just like with actors, the groups can be defined depending on the particularities of the business.

<a name="perspectives"></a>
## Perspectives

In the spirit of the current framework, a perspective is the point of view of a particular actor. Multiple actors will see the same application in different ways, will perceive certain aspects and be blind to others.

[![perspectives](/FrAppSec resources/perspectives.png)](https://github.com/frappsec/frappsec.github.io/blob/master/FrAppSec%20resources/perspectives.pptx){:target="_blank"}

A successful application security framework is able to collate all perspectives in order to provide a holistic view, understand each actor's needs in respect to security and provide the optimal solutions within the risk appetite. An ideal framework aims also to minimize the overlaps.

The way to achieve this is to ask each actor the right questions:

- What - the application
- Why - the motivation
- How - the processes
- Who - the people
- Where - the geographical considerations
- When - the timeline

<a name="frappsec-q-matrix"></a>
### FrAppSec Q Matrix

For simplicity, the framework is providing the **Q(uestions) Matrix** as a mean to collect information focusing on the four actor groups identified in the previous chapter. A successful matrix is one that minimizes overlaps whilst avoiding blind spots.

[![frappsec q matrix](/FrAppSec resources/frappsec q matrix.png)](https://github.com/frappsec/frappsec.github.io/blob/master/FrAppSec%20resources/frappsec%20q%20matrix.xlsx){:target="_blank"}

In the spirit of the framework, the matrix is flexible and will be defined on an individual basis.

For established organizations and large application projects it makes sense to build a full Q Matrix adding the relevant stakeholder groups and asking all the questions. In such a situation, each answer might be more elaborate (an entire document) that can be attached to the matrix.

A small team developing one application in a startup fashion can reduce the size of the matrix on both dimensions. Most likely the business stakeholders are also acting as architects and even developers of the application. As a rule of thumb, the minimum number of stakeholders should be three, with Development and Security being mandatory. The other dimension can also be reduced. For example, small teams working in the same office without a geographically distributed technological stack can eliminate the &quot;Where&quot; column.

The Security stakeholder in the Q Matrix should be a reflection of the other ones. The matrix provides visibility and alignment between stakeholders and allows for gap identification in the initial phases of the project. Not only Security can benefit from having such a mapping.

_FrAppSec Q Matrix_ is to be complited as part of the [hard layer](#layers), during the customization of the [intelligence group of activities in the maturity model](#activities). It is a specific document or set of documents for individual applications. It might not make sense to have a full matrix for all applications and this should be documented in the [service catalog](#service-catalog).

<a name="activities"></a>
### Activities

The scope of FrAppSec is not to detail the activities. Other initiatives ( [BSIMM](https://www.bsimm.com/) and [OpenSAMM](http://www.opensamm.org/) in particular) already did this and they have been through a number of iterations, making them mature and robust. FrAppSec aims at providing the interconnection between the activities in order to achieve a successful application security program.

In alignment with BSIMM and OpenSAMM, FrAppSec defines 4 areas and 12 activities that constitute the core of the application security program. FrAppSec is not debating the maturity model but is rather interested in the overarching taxonomy of the activities. A brief description is provided for the activities to better explain the connections between them and the way they should be understood in the current context.

- Governance - Organization, management and measurement of application security
  - Strategy - defining the mission, roles and responsibilities, high level processes
  - Policy - collecting requirements and publish the top level policy and the associated processes
  - Training - providing targeted training for all the stakeholders
- Intelligence - Collection of knowledge to guide the secure development cycle
  - Requirements - creating generic and specific requirements derived from the regulatory and strategic specifications
  - Features - building a set of standard features, customizing based on needs, guiding the reuse of secure blocks
  - Attacks - inventorying data according to classification, building a list of common attacks, using real world events to enhance
- Secure Development - Activities to be performed during the development life-cycle
  - Architecture Analysis - reviewing the specific Intelligence items, standardizing architectural descriptions and analysis process, creating checklists for testing
  - Static Analysis - running manual and automated source code security specific analysis
  - Dynamic Analysis - performing manual and automated runtime security specific analysis
- Production - Configuration, maintenance and monitoring of the application ecosystem
  - Vulnerability Management - running continuous automated testing on the production environment, feeding the results back into the cycle
  - Hardening - providing secure default states for the eco-system, reacting to Intelligence changes
  - Operational Intelligence - gathering feedback from operations and provide knowledge back into the cycle

Even though FrAppSec is not addressing maturity levels, they must be considered for all the activities, aligning with the [ITIL](https://en.wikipedia.org/wiki/ITIL) principle of continual service improvement.

<a name="frappsec-taxonomy"></a>
# FrAppSec Taxonomy

The taxonomy of activities, actors and paradigms provides the blueprint of FrAppSec. The paradigms introduced by the taxonomy are:

- Applications - the entire pool of the organization's applications in the scope of the security program
- Application - an individual instance of the Applications paradigm

[![FrAppSec Taxonomy](/FrAppSec resources/FrAppSec Taxonomy.png)](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=FrAppSec%20Taxonomy#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Ffrappsec%2Ffrappsec.github.io%2Fmaster%2FFrAppSec%2520resources%2FFrAppSec%2520Taxonomy){:target="_blank"}

The connectors starting and ending points are important. Elements are grouped and connections can start or end either in a group or in a particular element. For example, the _Intelligence_ activities are grouped and the entire group is specific for an application and generic for all the applications. The _Training_ activity is for all the actors while only _Executives_ dictate on _Strategy_.

The taxonomy is a blueprint. It does not depict all the elements nor all the connections between them. Activities, actors and paradigms can be added or removed according to organizational needs. The blueprint serves as a base for customization. It is a live document both from a framework perspective and also from an organizational implementation point of view.

<a name="layers"></a>
## Layers

The taxonomy has three distinct layers.

[![FrAppSec Layers](/FrAppSec resources/FrAppSec Layers.png)](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=FrAppSec%20Layers#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Ffrappsec%2Ffrappsec.github.io%2Fmaster%2FFrAppSec%2520resources%2FFrAppSec%2520Layers){:target="_blank"}
 
The **Soft Layer** revolves around the _Governance_ and _Intelligence_ groups of activities and apply to the _Applications_ paradigm. It is the basis for the other layers and includes the generic documentation projects outlining the strategic approach on application security. The better and more comprehensive this layer is, the less work is needed for customization of specifics for each Application.

The **Hard Layer** encompasses the specific _Intelligence_ items which are derived for an individual _Application_ and the Secure Development activities. This layer deals with the technical aspects of developing a secure application.

The **Real World Layer** is about the production ecosystem. Once the hard layer delivered the application, the real world layer is responsible for security.

The Layers diagram is an abstraction of the general taxonomy, depicting the applicability of certain areas on the paradigms of _Application_ and _Applications_. It is useful for determining functional zones, determining organizational structure and relationships. Communication between layers is ensured by the taxonomy, functional process are necessary for optimization.

<a name="organization"></a>
## Organization

An abstraction of the _Layers_ diagram is useful for providing an organizational overview of the _Taxonomy_.

[![FrAppSec Organization](/FrAppSec resources/FrAppSec Organization.png)](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=FrAppSec%20Organization#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Ffrappsec%2Ffrappsec.github.io%2Fmaster%2FFrAppSec%2520resources%2FFrAppSec%2520Organization){:target="_blank"}

While the _Soft_ layer needs _Technology_ as much as the _Hard_ and _Real World_ layers need _Processes_, it's clear who is the major enabler and driver for each layer. People are involved in all the layers.

<a name="service-catalog"></a>
# Service catalog

Having a complete activities or service catalog is a must for a mature application security initiative. Applying the service catalog to individual applications must have a business context. Treating all applications equally can have two unwanted consequences:

- Overspending of resources
- Proportionality is not assured in respect to criticality

Budget driven decisions are to be avoided. A statement saying "we can spend that much on security for that application" is not going to produce the optimal ROI or assure proportionality.

The decision of customizing the service catalog for categories of applications should be driven by the risk appetite statements and the application criticality definition and inventory.

Risk identification happens in the Hard and Real World layers. Depending on the maturity level of the activities, more or less risks will be identified. If more resources are invested there is a higher likelihood of finding more risks, thus increasing the application risk score. Applying a certain level of services is a byproduct of applications' inventory and categorization according to criticality which ensures business alignment.

The maximum service catalog is defined as the top level services that can be offered according to the maturity level for each activity.

The focus in creating the service catalog should be around defining the minimum catalog as a baseline to tackle all applications. Everything that can be automated and require minimum resources after the initial setup must be automated and included in the minimum service catalog.

Examples include:

- A strong and well documented soft layer can minimize the customization of the Intelligence items which are part of the  Hard layer.
- Running static and dynamic automated security analyzers, defining the risk acceptance policy and feed the defects above the risk appetite automatically into the bug tracking system
- Performing vulnerability management on the entire infrastructure and at the application level if automation is possible

A proposed minimum service catalog can include:

- Generic non-technical training  outlining the security principles, to be delivered as part of the on-boarding process and on a regular schedule afterwards
- Standard application security requirements
- Standard application security features
- Automated source code security scanning
- Automated penetration testing
- Vulnerability assessment for the production environment

The service catalog must be aligned with the applications' criticality. An initiative with three levels of criticality can extend the table of criticality with an extra column to indicate the service catalog applicable.

| How important is the application for the business? | Score | FrAppSec Service Catalog Level |
| --- | --- | --- |
| Very important | 3 | Premium |
| Important | 2 | Intermediate |
| Not important | 1 | Minimum |

The _Intermediate_ service catalog level in this example can be described as the middle ground between the minimum and maximum levels presented above. This can be done according to the organization's needs as it is expected that a good percentage of the applications will be in this category.

The service catalog is an indication of what services to be performed for which application. Particular applications, especially the ones which are important from a business perspective will have specific needs. They can be used as a driver for the maturity model.

<a name="putting-it-all-together"></a>
# Putting it all together

Application security is a complex field. The following approach is to be understood in the context of the current framework and the paradigms described in it.

1. Perform [inventory of the applications](#application-criticality)

2. Define the [application security strategy](#business-case) based on the inventory and the business strategy

3. Build the [taxonomy](#frappsec-taxonomy)

4. Build the [soft layer](#layers)

5. Build the [service catalog](#service-catalog)

6. Build and execute the [hard layer](#layers)

7. Execute the [risk management activities](#risk-management)

8. Build and execute the [real world layer](#layers)

9. Improve the [maturity model](#activities)

10. Repeat! 

<a name="supporting-documentation-and-templates"></a>
# Supporting documentation and templates

Applications Inventory

System Criticality Interview

Secure Application Development Policy
- Security principles
- Security requirements
- Security features
- Secure coding standards
- Security standards

RACI matrix for activities

Risk assessment form

Standard architectural descriptions

<a name="useful-and-referenced-links"></a>
## Useful and referenced links

[https://www.owasp.org/index.php/OWASP\_Risk\_Rating\_Methodology](https://www.owasp.org/index.php/OWASP_Risk_Rating_Methodology)

[https://en.wikipedia.org/wiki/Risk\_management](https://en.wikipedia.org/wiki/Risk_management)

[https://en.wikipedia.org/wiki/Risk\_appetite](https://en.wikipedia.org/wiki/Risk_appetite)

[https://www.bsimm.com](https://www.bsimm.com/)

[http://www.opensamm.org](http://www.opensamm.org)

[https://en.wikipedia.org/wiki/ITIL](https://en.wikipedia.org/wiki/ITIL)
