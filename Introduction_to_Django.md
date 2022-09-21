# Introduction to Django

Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.



## Feature

### Ridiculously fast

Django was designed to help developers take applications from concept to completion as quickly as possible.

### Reassuringly secure

Django takes security seriously and helps developers avoid many common security mistakes, such as SQL injection, cross-site scripting, cross-site request forgery and clickjacking. Its user authentication system provides a secure way to manage user accounts and passwords.

### Exceedingly scalable

Some of the busiest sites on the planet use Django’s ability to quickly and flexibly scale to meet the heaviest traffic demands.

### Incredibly versatile

Companies, organizations and governments have used Django to build all sorts of things — from content management systems to social networks to scientific computing platforms.



## Context:

Django was invented to meet fast-moving newsroom deadlines, while satisfying the tough requirements of experienced web developers. Because Django was developed in a fast-paced newsroom environment, it was designed to make common web development tasks fast and easy. 

With Django, you can take web applications from concept to launch in a matter of hours. Django takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.



## Quality attribute

### Rapid

Django's template language aims to strike a balance between power and ease of use. It is designed to be comfortable and easy to learn for those who are used to using HTML, such as designers and front-end developers. But it is also flexible and highly extensible, allowing developers to extend the template language as needed.

### Security

**Cross-Site Scripting (XSS) Protection.**

XSS attacks allow users to inject client-side scripts into other users' browsers. This is typically accomplished by storing malicious scripts in a database that is retrieved and displayed to other users, or by having the user click on a link that causes the attacker's JavaScript to be executed by the user's browser. However, XSS attacks can originate from any untrusted data source, such as cookies or Web services, as long as the data is not sufficiently cleaned before being included in the page.

**Cross-Site Request Forgery Protection (CSRF).**

CSRF protection works by checking the confidentiality in each POST request. This ensures that a malicious user cannot "replay" the form to your site and allow another logged-in user to submit the form unknowingly. The malicious user must know the confidentiality, which is specific to the user (using a cookie).

### SQL injection protection.

Django's query sets are protected from SQL injection because their queries are constructed using query parameterization. The SQL code of a query is defined separately from the parameters of the query. Since the parameters may be user-supplied and therefore unsafe, they are escaped by the underlying database driver.

### Extensible

Django projects can be configured with one or more template engines (or even zero if no templates are used.) Django provides its own template system (creatively called the Django Template Language (DTL)) as well as the popular alternative provides a built-in backend. Backends for other template languages are available from third parties.

Django provides a powerful forms library that handles rendering forms to HTML, validating user-submitted data, and converting that data to native Python types. Django also provides a way to generate forms from existing models and use those forms to create and update data.