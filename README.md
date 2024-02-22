## Description

Spring Security provides functionality to ensure application security. Using this framework, you can, for example, carry out an authentication process, thanks to which you can compare the entered password with the password that is stored in the database. You can also carry out the authorization process, that is, checking permission to access resources.

This application is designed to carry out both procedures - authentication and authorization. The user enters some address into the browser. After this, he is asked for a username and password. If the data is entered correctly, the user gains access to a web page, the content of which depends on his position. The application covers three different positions: employee, HR and manager.

## Configuration

To create such an application, you can use IntelliJ IDEA or another development environment. Select the Maven build system and "maven-archetype-webapp". My project is designed using Java code only, so without creating an XML file. Maven includes some dependencies by default, but you need to add some more ones from [mvnrepository.com](https://mvnrepository.com/) (see pom.xml file). Don't forget to make sure the dependency versions are compatible!

After adding the necessary dependencies, you need to create the **MyConfig** class, add some required annotations and create two beans - *ViewResolver* and *DataSource*.

Class **MyWebInitializer** should extend its superclass with veeeeery long name **AbstractAnnotationConfigDispatcherServletInitializer** and override some tis methods.

Add *Local Tomcat Server* using *Edit Configurations* in the application settings. You need to download it first from https://tomcat.apache.org/download-90.cgi (if you have not done it yet) and place it in the same folder where your project is located.

Create the **MySecurityInitializer** class that should just extend **AbstractSecurityWebApplicationInitializer**. Without this, there will be no form prompted for authentication where the user must enter a username and password.

Class **MySecurityConfig** contains annotation *@EnableWebSecurity* that makes it responsible for the security configuration. For this reason annotation *@Configuration* is not needed here. In this class we write usernames, passwords and worker roles. To do this, the class must extend **WebSecurityConfigurerAdapter** and override its method *configure* with parameter of type *AuthenticationManagerBuilder*. You can use the **UserBuilder** class to store passwords directly in the application, but no one does this today, so it’s better to use, for example, a database to store passwords. Nevertheless, you can find how to store data in the app in my project.

## Running

To create an authentication procedure, add the **MyController** class that contains *@Controller* annotation. This class contains three methods that render jsp-pages for different workers. These jsp-pages should be created in the **view** package using HTML. These pages, of course, can be made much more beautiful using CSS, for example, but this project shows functionality of Spring Security framework.

If you only apply the authentication procedure (entering a username and password), then all employees will be able to see all the information on all web pages. To limit access to certain workers, we must also implement an authorization procedure. To do this, we should override another method in the **MySecurityConfig** class. This method also has name *configure*, but it takes a parameter of type *HttpSecurity*. This method distributes specific URLs among specific employee roles.
