# Introduction to Django

Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.



## Feature

### Ridiculously fast

+ Django was designed to help developers take applications from concept to completion as quickly as possible.

### Reassuringly secure

+ Django takes security seriously and helps developers avoid many common security mistakes, such as SQL injection, cross-site scripting, cross-site request forgery and clickjacking. Its user authentication system provides a secure way to manage user accounts and passwords.

### Exceedingly scalable

+ Some of the busiest sites on the planet use Django’s ability to quickly and flexibly scale to meet the heaviest traffic demands.

### Incredibly versatile

+ Companies, organizations and governments have used Django to build all sorts of things — from content management systems to social networks to scientific computing platforms.



## Context:

+ Django was invented to meet fast-moving newsroom deadlines, while satisfying the tough requirements of experienced web developers. Because Django was developed in a fast-paced newsroom environment, it was designed to make common web development tasks fast and easy. 
+ With Django, you can take web applications from concept to launch in a matter of hours. Django takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.



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

    

### Extensible

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
+ Rapid
+ Usability
+ Extensible

