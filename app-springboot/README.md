app-springboot: SpringBoot Application
===================================================

Level: Beginner
Technologies: SpringBoot, Spring MVC, Spring Security
Summary: SpringBoot, Spring MVC, Spring Security
Target Product: RH-SSO
Source: <https://github.com/keycloak/rh-sso-quickstarts>


What is it?
-----------

The `app-springboot` quickstart demonstrates how to write a SpringBoot application that is secured with RH-SSO.

This application contains 2 pages :

* A public landing page.
* A secured product page.

This application also show how to combine Spring Security with RH-SSO.


System Requirements
-------------------

The quickstart requires that you have the [SpringBoot Service](../service-springboot/README.md) running. It assumes the
services are located at `http://localhost:8081/products`. If the services are running elsewhere you need to edit
`resources/application.properties` and replace the value of `product.service.url`.

All you need to build this project is Java 8.0 (Java SDK 1.8) or later and Maven 3.1.1 or later.


Configuration in RH-SSO
-----------------------

Prior to running the quickstart you need to create a client in RH-SSO and download the installation file.

The following steps shows how to create the client required for this quickstart:

* Open the RH-SSO admin console
* Select `Clients` from the menu
* Click `Create`
* Add the following values:
  * Client ID: You choose (for example `app-springboot`)
  * Client Protocol: `openid-connect`
  * Root URL: URL to the application (for example `http://localhost:8080/app-profile-html5`)
* Click `Save`

Once saved you need to change the `Access Type` to `public` and click save.

If you deploy the application somewhere else change the hostname and port of the URLs accordingly.

Finally you need to update the adapter using SpringBoot's configuration file (application.properties) :

````
server.compression.enabled: true
server.compression.min-response-size: 1
server.connection-timeout=5000
server.port = 8081
keycloak.realm=springboot-quickstart
keycloak.auth-server-url=http://localhost:8180/auth
keycloak.ssl-required=external
keycloak.resource=app-springboot
keycloak.public-client=true

````



Build and Run the Quickstart
-------------------------------

1. Open a terminal and navigate to the root directory of this quickstart.

2. The following shows the command to deploy the quickstart:

   ````
   mvn spring-boot:run
   
   ````

Access the Quickstart
---------------------

You can access the application with the following URL: <http://localhost:8080/>.

