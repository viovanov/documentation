---
layout: default-devplatform
title: "HP Helion Development Platform Workbook Java Hello World Sample"
permalink: /helion/devplatform/workbook/helloworld/java/
product: devplatform

---
<!--UNDER REVISION-->
##Java Hello World Sample
This sample displays the text "Hello World!". This is a demonstration of the minimum requirements to build a functional application in the form of a Servlet-based Java web app.  Use this sample to ensure that you have set up your environment for deployment to Helion Development Platform.

##Prerequisites
If you are missing any of these items, you will need to [install them](/helion/devplatform/appdev/).

1.	You must have access to an ALS cluster.
2.	The Helion command-line interface (CLI) must be installed.
3.	You must have access to the web-based Helion Management console.

###JDK
You must have the Java Development Kit (JDK) installed before you can install the other prerequisites.

On a Mac/UNIX environment, the JDK can be installed with the following command:

    sudo apt-get install default-jdk


On a PC environment, the simplest way to install the JDK is to visit the [JDK installation page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html/) and run the appropriate installer for your chosen platform.

###Maven

[Maven](http://maven.apache.org/ "Maven") must be installed. 
The simplest way to install Maven on a Mac/UNIX environment is:

	sudo apt-get install maven 

The simplest way to install Maven on a PC environment is to [download the latest version of Maven](http://maven.apache.org/download.cgi) and then follow the [installation directions](http://maven.apache.org/guides/getting-started/windows-prerequisites.html).

##Download the Application Files
[Click here to access the download directory.](https://github.com/HelionDevPlatform/helion-hello-world-java) 
 
##Build the Application
If you are not already there, `cd` to the root directory of the sample and execute:

	mvn clean package

This builds the application with Maven. It will create the *hello-world-java-1.0.war* file within the target directory. 

##Deploy the Application
Use the Helion client to deploy your app to Helion Development Platform.  If you have Eclipse installed, you have the option to [use the plugin](/helion/devplatform/eclipse/) to deploy.

1.	Open the [Helion command-line interface (CLI)](/als/v1/user/reference/client-ref/)
2.	Ensure that you are logged in to your desired environment.  <br>If you are not, execute `helion login` 
3.	Ensure that you are targeting your desired environment.  <br> If you are not, execute `helion target https://api.xx.xx.xx.xx.example.com`
4.	If you are not already there, `cd` to the root directory of the sample.
5.	Execute `helion push -n`

##Run the Application
1.	Open the Helion Management Console. <br> The Management Console is the web-based administrative interface that can be reached by typing the ALS endpoint URL into a browser window.
2.	Click **Applications**.
3.	If the file push was successful, you should see **hello-world-java** in the list of available applications.

##Key Code Snippets

    package org.hp.samples;
	
	import java.io.IOException;
	import java.io.PrintWriter;
	
	import javax.servlet.ServletException;
	import javax.servlet.http.HttpServlet;
	import javax.servlet.http.HttpServletRequest;
	import javax.servlet.http.HttpServletResponse;
	
	public class HelloServlet extends HttpServlet {
	
		private static final long serialVersionUID = 1L;
	
		protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
			response.setContentType("text/plain");
			response.setStatus(200);
			PrintWriter writer = response.getWriter();
			writer.println("Hello World");
			writer.close();
		}
	}

This simple Servlet prints "Hello World".

	<?xml version="1.0" encoding="UTF-8"?>
	<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	    <modelVersion>4.0.0</modelVersion>
	    <groupId>org.hp.samples</groupId>
	    <artifactId>hello-world-java</artifactId>
	    <version>1.0</version>
	    <packaging>war</packaging>
	    <dependencies>
	        <dependency>
	            <groupId>javax.servlet</groupId>
	            <artifactId>servlet-api</artifactId>
	            <version>2.5</version>
	            <scope>provided</scope>
	        </dependency>
	    </dependencies>
	</project>

## Run the Application

1. Open the Helion Management Console. This is the web-based administrative interface that can be reached by typing the ALS endpoint URL into a browser window..

2. Click **Applications**.

3. If the file push was successful, you should see **Hello World** in the list of available applications.

4. The status of the application should be `Online`. Click the name of the application to launch it.

5. In the upper right-hand corner, click **View App**.

6. You should see a simple text message: `Hello World!` 

##Key Learnings
1.	ALS requires configuration information to create an environment for your app. Tools like Maven generate the *pom.xml* file for you.
2.	You can deploy your app using either the Helion CLI or the Eclipse [deployment plugin](/helion/devplatform/eclipse/).

[Exit Samples](/helion/devplatform/) | [Next Sample](/helion/devplatform/workbook/database/java/)