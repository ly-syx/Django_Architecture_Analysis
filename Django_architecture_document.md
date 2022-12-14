# Django Architecture Document

**Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.**



## Contributors & their participating parts:

+ Yun Lei: Feature, Quality attribute, Key Drivers, Architecture, Decision View, Stakeholder, Technical Context, Scenario, Tactic, Architectural Evaluation for Scenarios
+ Yuxiang Dai: Feature, Quality attribute, Key Drivers, Stakeholder and the Specific Concerns, Technical Context, Scenario
+ Yifan Liao: Context, Scenario, Tactic



## Feature

### Ridiculously fast

+ Django was designed to help developers take applications from concept to completion as quickly as possible.

### Fully loaded.

+ Django includes dozens of extras you can use to handle common web development tasks. Django takes care of user authentication, content administration, site maps, RSS feeds, and many more tasks — right out of the box.

### Reassuringly secure

+ Django takes security seriously and helps developers avoid many common security mistakes, such as SQL injection, cross-site scripting, cross-site request forgery and clickjacking. Its user authentication system provides a secure way to manage user accounts and passwords.

### Exceedingly scalable

+ Some of the busiest sites on the planet use Django’s ability to quickly and flexibly scale to meet the heaviest traffic demands.

### Incredibly versatile

+ Companies, organizations and governments have used Django to build all sorts of things — from content management systems to social networks to scientific computing platforms.



## Context:

+ **Origin**

	Django was invented to meet fast-moving newsroom deadlines, while satisfying the tough requirements of experienced web developers. Because Django was developed in a fast-paced newsroom environment, it was designed to make common web development tasks fast and easy. 

	With Django, you can take web applications from concept to launch in a matter of hours. Django takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.

+ **Web framework based on Python**

	Django is an open source web framework written in Python with full shelf capability. In addition to encapsulating network and thread operations, Django provides a framework for HTTP requests and responses, database management, HTML template rendering, and more.

+ **MTV framework**

	Django is a “MTV” framework , which means “model” “template” and “view.”

	**M** is for "Model": contains the basic functions, and are responsible for mapping business objects to the database (Object Relational Mapping, ORM).
	**T** is for "Template": responsible for how the page (HTML) is presented to the user.
	**V** is for "View": takes care of the logic business and calls Model and Template when appropriate.

<img src="Django_architecture_document_imgs/architecture diagram.png" style="zoom:65%;" />



## Quality attribute

### Rapid

+ **Easy to Learn**

    Django's template language aims to strike a balance between power and ease of use. It is designed to be comfortable and easy to learn for those who are used to using HTML, such as designers and front-end developers. 

+ **Agile to Develop**

    Django's main goal is to make it easy to develop complex, database-driven websites. Django focuses on component reusability and "pluggability", agile development, and the DRY rule (Don't Repeat Yourself). 

    

### Security

+ **Cross-Site Scripting (XSS) Protection**

    XSS attacks allow users to inject client-side scripts into other users' browsers. This is typically accomplished by storing malicious scripts in a database that is retrieved and displayed to other users, or by having the user click on a link that causes the attacker's JavaScript to be executed by the user's browser. However, XSS attacks can originate from any untrusted data source, such as cookies or Web services, as long as the data is not sufficiently cleaned before being included in the page.

+ **Cross-Site Request Forgery Protection (CSRF)**

    CSRF protection works by checking the confidentiality in each POST request. This ensures that a malicious user cannot "replay" the form to your site and allow another logged-in user to submit the form unknowingly. The malicious user must know the confidentiality, which is specific to the user (using a cookie).

+ **SQL injection protection**

    Django's query sets are protected from SQL injection because their queries are constructed using query parameterization. The SQL code of a query is defined separately from the parameters of the query. Since the parameters may be user-supplied and therefore unsafe, they are escaped by the underlying database driver.

+ **Clickjacking Protection**

    Clickjacking is an attack in which a malicious site wraps another site in a frame. This attack can result in an unsuspecting user being tricked into performing an unexpected action on the target site.

    Django includes clickjacking protection in the form of a protection that prevents sites from being rendered within frames in supported browsers. Protection can be disabled or the exact header value sent can be configured on a per-view basis. x-Frame-Options middleware

    

### Extensibility

+ **Suppose the Template from Third Parties**

    Django projects can be configured with one or more template engines (or even zero if no templates are used.) Django provides its own template system (creatively called the Django Template Language (DTL)) as well as the popular alternative provides a built-in backend. Backends for other template languages are available from third parties.

+ **Powerful Forms Library**

    Django provides a powerful forms library that handles rendering forms to HTML, validating user-submitted data, and converting that data to native Python types. Django also provides a way to generate forms from existing models and use those forms to create and update data.

    

### Testability

+ **Transactions**

    Each web transaction and the primary source of the response (v view handlers, middleware, etc.) are measured and named. For slow transactions provide a detailed trace of the transaction, which can show the time spent on the various functional components that processed that particular request. Data coverage of the trace includes: call database time, view handlers, middleware, and template rendering.

+ **SQL queries**

    In addition to timing and counting database calls, OneAPM automatically grabs slow SQL statements and shows which functions are calling those SQL statements, and we have 100% support for Django and SQLAlchemy's ORM architecture and all DBAPI2 compliant databases.

+ **Error messages**

    In Django, runtime exceptions are converted to 500 errors by default by the architecture. OneAPM automatically intercepts these reports and reports them along with their stack trace, so users can easily fix these errors that are easier to overlook in production.

    

### Usability

+ **Powerful database access component**

    Django's Model layer comes with a database ORM component, making it unnecessary for developers to learn other database access technologies (SQL, pymysql, SQL ALchemy, etc.)

+ **Rich Template template language**

    Similar to jinjia template language, it is not only rich in native features, but also customizable template tags, and very similar to the use of its ORM.

+ **With back office management system admin**

    Just a few simple lines of configuration and code to achieve a complete backend data management control platform.



## Key Drivers

+ Security
+ Modifiability
+ Scalability



## Architecture

### Architecture Diagram

<img src="./Django_architecture_document_imgs/architecture diagram.png" style="zoom:65%;" />



##  In a Decision View

+ At the beginning of the project, the designers considered Django as a **tool library** of Python that would reduce web application development work, so programmers can focus on writing their app without needing to reinvent the wheel. 

+ The designers make following decisions:

    1. **Scalability**:

        For some of the busiest sites on the planet, they may have tens of thousands of visits per second during peak traffic periods. So Django should have ability to quickly and flexibly scale to meet the heaviest traffic demands.

        **Related Decisions**:

        Django uses a “shared-nothing” architecture, which means you can add hardware at any level – database servers, caching servers or web/application servers. 

        

    2. **Modifiability**:

        In order to ensure a highly **Modifiability**, it would be **loosely coupled** so that every module could maintain or modify more easily.

        **Related Decisions**:

        Django uses a "MVT" framework to separates the the business logic, display logic and the data manage logic. And Django cleanly separates components such as its database layer and application layer.



## Stakeholder And the Specific Concerns

The stakeholders are **users, developing department, maintenance organization:**

### **The specific concerns of stakeholders:**

#### User:

+ What functionality does the Django provide?
+ How well does it perform?
+ Whether is it scalable?
+ Whether is it secure?
+ Whether is it easy to use?
+ Whether is stable?

#### Developing department:

+ Whether could it delivery timely?
+ Whether is it developed at low cost and low work?

#### Maintenance organization:

+ Whether is it maintainable?



## Architecture in a Technical Context

### Security:

As a web application, if the data centre is damaged or compromised, the web service will be affected, so it is important to ensure the security of the web application, and the Django framework is designed to automatically perform the right actions to protect the network, thus helping developers to avoid many common security errors.

### Reusability:

Users want to save more time when developing and also want programs that are easy to maintain, in addition to having highly reusable programs that are well suited to high-load systems.

### Scalability:

With the rapid development of global information technology, the traditional back-end service framework can no longer meet the needs of some scenarios where traffic fluctuates instantly due to large activities or high-profile events, requiring a framework that can handle large amounts of data and traffic on the application. At the same time, it is becoming common for development teams to rent cloud servers, so it is essential that the framework is scalable.

### Environment——Python: 

The Django framework is built in Python and inherits the best of Python and its great community - with many useful libraries, such as some of the most popular ones, including the Django REST framework for building APIs (application programming interfaces) and the CMS-oriented framework for website CMS-oriented frameworks for content management.

### API and Front-end Frameworks:

Since Django inherits python's Django REST framework for building APIs (application programming interfaces), it adapts well to API request access from the main front-end frameworks on the market, such as Bootstrap, jQuery, Bootswatch, etc.

### Databases Supported:

PostgreSQL, MariaDB, MySQL, Oracle, SQLite



## Scenario

### A Modifiability Scenario:

The developer wishes to modify the rendered way to the home page at design time. And the modifications are successfully made within 5 hours.


| Portion of Scenario | Possible Values                              |
| ------------------- | -------------------------------------------- |
| Source              | Developer                                    |
| Stimulus            | Wish to change the rendered way to home page |
| Artifact            | Code                                         |
| Environment         | Design time                                  |
| Response            | Change code and unit test                    |
| Response Measure    | In 5 hours                                   |

<img src="Django_architecture_document_imgs/modifiability scenario.png" alt="Modifiability_Scenario" style="zoom:80%;" />

### A Scalability Scenario:

The developer wishes to add some new servers to the cluster of servers, so that the site could respond faster to more requests from customers with higher concurrency.


| Portion of Scenario | Possible Values                                              |
| ------------------- | ------------------------------------------------------------ |
| Source              | Developer                                                    |
| Stimulus            | Wish site could response faster to more requests concurrently |
| Artifact            | Code, components                                             |
| Environment         | Build time                                                   |
| Response            | Add the new servers and deploy them                          |
| Response Measure    | In 3 hours if renting cloud servers                          |

<img src="Django_architecture_document_imgs/scalability scenario.png" alt="Scalability_Scenario" style="zoom:75%;" />





## Tactic

### For modifiability:

+ **Reduce the Size of a Module** —— ***Split module:***

    In Django, the project would be split into some small modules, such as views, models and templates. If the module being modified includes a great deal of capability, the modification costs will likely be high. Refining the module into several smaller modules should reduce the average cost of future changes. 

+ **Reduce Coupling** —— ***Encapsulate:***

    In Django, the different functions would be encapsulate in different modules. And different modules interact and collaborate with each other through their interfaces to perform complex functions. For example, the WSGI module is responsible for handling API requests, and calling the corresponding business functions through the interfaces of the modules. WSGI doesn't care about how these functions are implemented, it just needs to know which interface to call. Encapsulation reduces the probability that a change to one module propagates to other modules.

    

    

    Such as followed project:

<div align=center><img src="./Django_architecture_document_imgs/architecture diagram.png" style="zoom:65%;" /><img src="./Django_architecture_document_imgs/modifiability tactic.png" alt="Modifiability Tactic" style="zoom:80%;" /></div>




+ In the project, the various functions were encapsulated in different classes, and the classes with highly close related or similar functions were encapsulated in the same module file. 

    For example, the code about processing cookies are encapsulated in the module named cookie.py.

    

+ Different business modules were split into different packages clearly. 

    For example contrib package contains system the system's configuration file; forms package contains the code about generating form and parsing form information.



### For scalability:

The web applications developed using Django have the ability to handle multiple client requests at the same time. Django projects are very scalable and can handle requests on. 

+ **Shared-nothing Architecture**

    + **Introduction of shared-nothing architecure:**

        > **Shared Nothing Architecture (SNA) is a distributed computing architecture** that consists of multiple independent nodes that do not share resources. The nodes are independent and self-sufficient, as they have their own disk space and memory.
        >
        > In such a system, data sets/workloads are divided into smaller sets (nodes) that are distributed to different parts of the system. Each node has its own memory, storage and independent input/output interfaces. It communicates and synchronizes with other nodes through a high-speed interconnection network. Such connectivity ensures low latency, high bandwidth and high availability (backup interconnects can be used in case of failure of the primary node).
        >
        > **Since the data is horizontally partitioned, the system supports incremental growth.** You can add new nodes to horizontally expand the distributed system and increase the transmission capacity.
        >
        > 
        >
        > **Comparing Shared Everything, Shared Storage, and Shared Nothing:**
        >
        > **Shared Storage Architecture** is a distributed computing architecture where all nodes in a system are **linked to the same disk device**, but have their own private memory. The shared data is accessible from all cluster nodes and typically represents a shared disk (e.g., a database) or a shared file system (e.g., a storage area network or network-attached storage). The shared disk architecture is best suited for use cases where data partitioning is not possible. It is much less scalable than SNA.
        >
        > **Shared Everything architecture** consists of nodes that **share all resources within the system**. Each node has access to the same computational resources and shared storage. The main idea behind this system is to maximize the use of resources. The disadvantage is that shared resources can also lead to performance degradation due to contention.
        >
        > The following image shows the difference between the three most dominant sharing structures - **Shared Everything, Shared Storage, and Shared Nothing**:
        >
        > Unlike the others, SNA has no shared resources. The only thing that connects the nodes is the network layer, which manages the system and the communication between the nodes.
        >
        > <div align=center><img src="./Django_architecture_document_imgs/shared-nothing-architecture-diagram.png" /></div>
        >
        > **The advantages and disadvantages** of the shared-nothing architecture compared to other architectures are as follows:
        >
        > **Advantages:**
        >
        > + Easier to scale
        > + Eliminate the system failure from single node failures
        > + No downtime for upgrades and updates of server
        >
        > **Disadvantages:**
        >
        > + More cost
        > + Reduced performance

+ **Django with a shared-nothing architecure:**

    Django designed the web framework to efficiently use the hardware in developers' system. With a shared-nothing architecture, Django separates components like the database layer (the models) and the application layer (the views). Hardware can be added at any level without affecting the rest of the system. More database servers or application servers are allowed to be added into your system, and Django will use these resources efficiently to handle multiple visitors.

<div align=center><img src="./Django_architecture_document_imgs/scalability_scenario.png" /></div>

+ **Cache Framework**

    Caching is the process of saving some web page data on the client’s server or on intermediary servers so that your Django app can process requests faster, increasing scale. 

    Django offers a robust caching system with different levels of caching:

    1. **The per-site cache** —— You can cache your entire website:

        > Once the cache is set up, the simplest way to use caching is to cache entire site.

    2. **The per-view cache** —— You can cache specific view function output:

        > A more granular way to use the caching framework is by caching the output of individual views.

    3. **The low-level cache API** —— You can cache specific content that is time consuming to create:
    
        > Sometimes, caching an entire rendered page doesn’t gain you very much and is, in fact, inconvenient overkill.
        >
        > Perhaps, for instance, your site includes a view whose results depend on several expensive queries, the results of which change at different intervals. In this case, it would not be ideal to use the full-page caching that the per-site or per-view cache strategies offer, because you wouldn’t want to cache the entire result (since some of the data changes often), but you’d still want to cache the results that rarely change.
        >
        > For cases like this, Django exposes a low-level cache API. You can use this API to store objects in the cache with any level of granularity you like. You can cache any Python object that can be pickled safely: strings, dictionaries, lists of model objects, and so forth. (Most common Python objects can be pickled; refer to the Python documentation for more information about pickling.)

    Django projects also work well with third-party caches. You can write code that gives hints about these caches and tells them which part of your application you want to cache.

    <div align=center><img src="./Django_architecture_document_imgs/scalability_scenario2.png" /></div>

## Architectural Evaluation for Scenarios

### Architectural evaluation of scenario 1:

![evaluation](Django_architecture_document_imgs/evaluation.png)
