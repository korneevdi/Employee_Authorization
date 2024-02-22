Spring Security provides functionality to ensure application security. Using this framework, you can, for example, carry out an authentication process, thanks to which you can compare the entered password with the password that is stored in the database. You can also carry out the authorization process, that is, checking permission to access resources.

This application is designed to carry out both procedures - authentication and authorization. The user enters some address into the browser. After this, he is asked for a username and password. If the data is entered correctly, the user gains access to a web page, the content of which depends on his position. The application covers three different positions: employee, HR manager and boss.

To create such an application, you can use IntelliJ IDEA or another development environment. Select the Maven build system and "maven-archetype-webapp". My project is designed using Java code only, so without creating an XML file. Maven includes some dependencies by default, but you need to add some more ones from [mvnrepository.com](https://mvnrepository.com/) (see pom.xml file). Don't forget to make sure the dependency versions are compatible!
