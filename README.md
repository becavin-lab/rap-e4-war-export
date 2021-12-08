# rap-e4-war-export
An example eclipse RAP e4 project which can be export to .war file

The war export tool is no longer maintain for Eclipse RAP

To export your Eclipse RAP e4 project into war, we use Maven Tycho.

0 - Install Eclipse for RCP and RAP developpers. 

1 - Clone the project in your working directory

2 - Click on File > Import > General : Projects from Folder or Archive.
Select the Directory where you cloned rap-e4-war-export
It should find 4 plugins:

rap-e4-war-export

rap-e4-war-export/rap.e4.export.demo

rap-e4-war-export/rap.e4.export.feature

rap-e4-war-export/target-platform-rap-e4

Click on Finish.
You should have the 3 plugins imported into on big project = rap-e4-war-export.

3 - Open target-platform-rap-e4/target-platform-rap-e4.target
The target platform is included in our project. This is the working environment in which Eclipse will pick all java and Eclipse RAP dependencies needed. 
In the target definition item (target-platform-rap-e4.target > Definition), check that it indicates around 300 plug-ins available. Otherwise click on "Reload". If no plug-ins is available then Eclipse will not know where to find the dependencies.
As soon as you have the plug-ins available, click on the top-right corner : "Set as active Target Platform".

The operation is complete if in "rap.e4.export.demo" there are no dependencies error. Meaning that all plug-ins have been found by Eclipse in the Target platform.

4 - We need to test if the Eclipse RAP can launch. 
Go to rap.e4.export.demo > plugin.xml and click on Overview > Update the classpath settings.
In the "Problems" View of Eclipse you should have no errors.

5 - Click on "Launch a RAP application" ! A browser at the adress : http://127.0.0.1:10888/ (the port might be different) should open. Update the browser, you should have an Eclipse RAP browser.
More explanation, when running your plug-ins it uses the file "rap.e4.export.demo.launch" to configure all run configuration (port, VM options, bundles dependencies).
IF SOMETHING IS WRONG AND THE WEBSITE IS NOT OPENING IT IS MOSTLY DUE TO "rap.e4.export.demo.launch".

Now that we are sure your website is running on local server, we can export it to a .war file.

6 - "rap.e4.export.feature" is the feature which define precisely for Maven Tycho how "rap.e4.export.demo" run and what are its dependencies. We will work with this features to export into war file.
First, fix the product definition which is your future executable. Click on rap.e4.export.feature.product > Overview > Synchronize. So the feature is synchronized with "rap.e4.export.demo". Then click on Overview > Launch a RAP Application. You should have the same website displaying.
Your good to go on export !

7 - We use Maven integration into Eclipse : m2e. It is installed by default in Eclipse.
Select rap-e4-war-export > pom.xml (at the root of your main project).
Right click on Run as > Maven build... and in Goals write "clean install"
It should create the war file after few minutes.
It can be found in rap.e4.export.feature/target/rap-e4-demo.war

The name of the .war is a parameter which can be fixed in: rap.e4.export.feature/pom.xml
with webapp.name property.

7+ - Maven can be ran in your shell. Go into the right path
cd rap-e4-war-export
and then
mvn clean install

For maven install use the appropriate package installer apt-get, yum, brew, etc...



