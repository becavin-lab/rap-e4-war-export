# rap-e4-war-export
An example eclipse RAP e4 project which can be export to .war file

The war export tool is no longer maintain for Eclipse RAP

To export your Eclipse RAP e4 project ino war, we use Maven Tycho.

1- Import the project with Eclipse -> import from folder
2- Run the export with mvn clean install
3- The war file is in rap.e4.export.feature/target/rap-e4-export.war
4- Deploy your website on Apache Tomcat 9
