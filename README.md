# SpringBootRestDataJPABasicAuth
Spring Boot Rest DataJPA with Basic Authentication


#Following technologies stack being used:

Spring Boot 1.4.3.RELEASE
Spring 4.3.5.RELEASE [transitively]
Spring data JPA 1.10.6.RELEASE [transitively]
Hibernate 5.0.11.Final [transitively]
MySQL 5.1.40 [transitively]
H2 1.4.187
Hikari CP 2.4.7 [transitively]
AngularJS 1.5.8
Maven 3.1
JDK 1.8
IntelliJ


#Property file [application.yml]

Although traditional .properties would just do fine, Spring Boot’s SpringApplication class also supports YAML out of the box provided SnakeYAML library is on class-path which usually would be due to starters. YAML is a superset of JSON, and as such is a very convenient format for specifying hierarchical configuration data. YAML file is also known as streams, containing several documents, each separated by three dashes (—). A line beginning with “—” may be used to explicitly denote the beginning of a new YAML document.YAML specification is a good read to know more about them.

src/main/resources/application.yml

1- Since our app will be running on an Embedded container, we would need a way to configure the port and context-path for our app. By-default, Spring-Boot will use no context-path, and the default port would be 8080, means your application would be available at localhost:8080. But you can overwrite these properties by declaring them in application.yml [or application.yaml/application.properties] file. In our case, the first document [top level part, above '---' line] is the one configuring port and context path.

2- Since we will be using profiles, we have created two separate documents each with it’s own profile.
By default if no profile is specified, ‘default’ profile is used, this is standard spring behavior. You can additionally create different profiles based on your environments and use them on run.

3- In our case, we are pointing both default and local to same profile, hence letting user to run the app directly, without specifying any profile, in that case the default profile will be used. But you are free to specify a profile. While running our example [via IDE or command-line], we can provide the profile information using -Dspring.profiles.active=local or -Dspring.profiles.active=prod in VM arguments[for IDE] or on command-line java -jar JARPATH --spring.profiles.active=local.

4- Notice the datasource part in yml file: here we are specifying all stuff related to database. Similarly if you have other aspects/concerns [security e.g.], you could create separate levels for that. We will be using H2 database while running under profile ‘local’ and MySQL while running with profile ‘prod’.

#Run the application

Finally, Let’s run the application, firstly with ‘local’ profile [H2]. Next shot will be with ‘prod’ profile [MySQL].

Via Eclipse:: Run it directly, in that case default profile will be used. In case you want a different profile to be used, create a Run configuration for you main class, specifying the profile. To do that from toolbar, select Run->Run Configurations->Arguments->VM Arguments. Add -Dspring.profiles.active=local or -Dspring.profiles.active=prod]

Via Command line::
On project root
$> java -jar target/SpringBootCRUDApplicationExample-1.0.0.jar –spring.profiles.active=local

Please take special note of two ‘-’ in front of spring.profiles.active. In the blog it might be appearing as single ‘-’ but there are in fact two ‘-’ of them.


Open your browser and navigate to http://localhost:8080/SpringBootCRUDApp/
