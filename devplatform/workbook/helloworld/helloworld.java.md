---
layout: default-devplatform
title: "HP Helion Development Platform Workbook Java Hello World Sample"
permalink: /helion/devplatform/workbook/helloworld/java/
product: devplatform

---
##Hello World JAVA
This is a very simple Servlet-based Java webapp.
##Prerequisites
**Stackato**

1. You must have a Stackato instance available. 
2. The  [Stackato command-line interface (CLI)](http://docs.stackato.com/user/client/index.html#client) must be installed. 
3. You must have access to the web-based Administration console.

**JDK**

Maven requires you to have the Java Development Kit (JDK) installed. The JDK can be installed with the following command:

	sudo apt-get install default-jdk

**Maven**

[Maven](http://maven.apache.org/ "Maven") must be installed. 
The simplest way to install Maven is:

	sudo apt-get install maven 

##Download the Application Files
[Click here to access the download directory.](https://gitlab.gozer.hpcloud.net/developer-experience/sampleapps) There are several sets of files here; download only the Hello-World-Java sample files. 

The `pom.xml` file in the root directory of this sample is used by Maven to build the application. 
 
##Build the Application
The specific commands listed below are intended for Unix-like machines.

Use the [Stackato command-line interface (CLI)](http://docs.stackato.com/user/client/index.html#client) to `cd` into the root directory of the sample and execute:

	mvn clean package

This builds the application with Maven. It will create the *hello-world-java-1.0.war* file within the `target` directory. 

##Deploy the Application

To deploy the application, make sure you are logged in successfully for your desired target environment; for example, *https://api.yourapp.com*.

1. Open the  [Stackato command-line interface (CLI)](http://docs.stackato.com/user/client/index.html#client).

2. *cd* into the app's root directory.
3. Execute `stackato push -n` 

##Run the Application

1. Open the Management Console. This is the web-based administrative interface.
2. Click **Applications**.
3. If the file push was successful, you should see Hello World in the list of available applications. 
4. The status of the application should be **Online**. Click the name of the application to launch it. 
5. In the upper right-hand corner, click **View App**.
6. You should see a simple text message: Hello World!
	

[Exit Workbook](/helion/devplatform/) | [Next Sample](/helion/devplatform/workbook/database/java/)