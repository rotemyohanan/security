


#### Subject
------

When you’re securing your application, probably the most relevant questions to ask yourself are: 
1. “Who is the current user?” 
2. “Is the current user allowed to do X”? 

Think of it when writing code or designing user interfaces. Applications are usually built based on user stories, and you want functionality represented (and secured) based on a per-user basis. 

The most natural way for us to think about security in our application is based on the current user. 
Shiro’s API fundamentally represents this way of thinking in its Subject concept.

##### What is a Subject ?
-------

This is the currently executing user (human being, 3rd party process, daemon account...). 
(It's just not called a 'User' because the word 'User' is usually associated with a human being).
'the thing that is currently interacting with the software'


Acquiring a subject:

    import org.apache.shiro.subject.Subject;
    import org.apache.shiro.SecurityUtils;
    ...
    Subject currentUser = SecurityUtils.getSubject();


The shiro security mechnisem is thinking in ‘per-user’ security control (very intuitive).


#### SecurityManager 

While the **Subject** represents security operations for the current user, the **SecurityManager** manages security operations for all users. 



###### Set Up a SecurityManager

**Web application** will usually specify a Shiro Servlet Filter in **web.xml**, and that will set up the **SecurityManager** instance. 

> Always a single **SecurityManager** instance per application. (it does not need to be a static singleton).

It is essentially an application singleton (although it does not need to be a static singleton). 
The default **SecurityManager** implementations are POJOs and are configurable with any POJO-compatible configuration mechanism - normal Java code, Spring XML, YAML, .properties and .ini files, etc.

> Note: Shiro supports **Spring XML** configuration.


#### Realms

The third and final core concept in Shiro is that of a Realm. 
A Realm acts as the **‘bridge’** or **‘connector’** between Shiro and your application’s security data. 

- authentication (login)
- authorization (access control)

Shiro looks up many of these things from one or more Realms configured for an application.

A Realm is essentially a security-specific DAO: it encapsulates connection details for data sources and makes the associated data available to Shiro as needed. When configuring Shiro, you must specify at least one Realm to use for authentication and/or authorization. More than one Realm may be configured, but at least one is required.

Shiro provides out-of-the-box Realms to connect to a number of security data sources (aka directories) such as LDAP, relational databases (JDBC), text configuration sources like INI and properties files ...

    ldapRealm = org.apache.shiro.realm.ldap.JndiLdapRealm
    ldapRealm.userDnTemplate = uid={0},ou=users,dc=mycompany,dc=com
    ldapRealm.contextFactory.url = ldap://ldapHost:389
    ldapRealm.contextFactory.authenticationMechanism = DIGEST-MD5 


reached to Authentication


