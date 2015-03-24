---
layout: docs
title: Configuration
permalink: /docs/configuration/
---
SFDC Dev Tool Plugin
=============

This is an open source plugin
## Plugin Requirements
 * Java JDK 1.7
 * Gradle 2.0 or greater
 * Operation System
       a) Windows 7
       b) Linux Ubuntu
 * build.gradle File
 * gradle.properties File (Optional)
 * credential.dat File1
 * User account in a Salesforce Organization and the related security token

###Tentative files configuration for User:

Files Gradle
-----------

* build.gradle has the configuration of gradle for user.
* gradle.properties has values that build.gradle will use.
* credentials.dat has all credentials to use
See below the tentative file

#### build.gradle
```groovy
   buildscript {
       repositories {
           mavenLocal()
           mavenCentral()
           maven {
               url "http://10.31.2.240:8081/artifactory/salesforce"
           }
       }
       dependencies {
           classpath 'com.jalasoft.sfdc.devtool:SFDC-Dev-Tool:1.0.62.b13'
       }
   }
   
   apply plugin: 'force'
   
   force {
       srcPath = 'src'
       standardObjects = ["Account.object"]
       poll = 200 //times
       waitTime = 10 //seg
       //integration = 'yes'
       //foldersToDownload = "classes"
      
   }
```

#### gradle.properties
```groovy
    credentialId=
```

#### Setup Salesforce organization credentials

<div class="note info">
  <h5>Credential support</h5>
  <p>Create a *credentials.dat* file at your HOME folder, which should contain at least one entry for your development Org, below an example of the content</p>
</div>

```json
{
 "default": {
        "username": "user@org.com",
        "password": "mypassword",
        "token": "2B9UvHKK2E1ky1EkkYBPFvbLM",
        "sfdcType" : "login",
        "type": "normal"
    }
}
```


> **Note:** Notice that the example uses the "default" key which by convention is the one to be used by default when a task is executed. You can have several entries to different salesforce accounts but each entry needs to have an unique key.

## Project gradle tasks
The gradle project contains tasks that will help on development and packaging.
> **Note:** You have to execute the gradle tasks from the project folder

------------------------------------------------------------
All tasks runnable from root project
------------------------------------------------------------

Build Setup tasks
-----------------
    -init = Initializes a new Gradle build. [incubating].
    -wrapper = Generates Gradle wrapper files. [incubating].

Credential Manager tasks
------------------------
    -addCredential = Adds credential.
    -updateCredential = Updates credential.

Deployment tasks
----------------
    -deploy = This task deploys all the project.
    -undeploy = This task removes all components in your organization according to local repository.
    -update = This task deploys just the files that were changed.
    -upload = This task uploads all specific files or folders as user wants.

File Monitor tasks
------------------
    -status - You can display elements that were changed.

Package Management tasks
------------------------
installPackage - Installs a package to an organization.
        -Ppkg.namespace = (*)Package namespace.
        -Ppkg.version = (*)Package version to install.
        -Ppkg.password = (-)Package password.
uninstallPackage - Uninstalls a package to an organization.
        -Ppkg.namespace = (*)Package namespace.

Help tasks
----------
    dependencies - Displays all dependencies declared in root project 'user'.
    dependencyInsight - Displays the insight into a specific dependency in root project 'user'.
    help - Displays a help message
    projects - Displays the sub-projects of root project 'user'.
    properties - Displays the properties of root project 'user'.
    tasks - Displays the tasks runnable from root project 'user'.

Retrieve tasks
--------------
    -download.
    -retrieve.

Test tasks
----------
    -runTests = This task runs unit tests and it also generates results of unit test and coverage.

Utils tasks
-----------
    -execute = This task executes apex code from a file or inline code.