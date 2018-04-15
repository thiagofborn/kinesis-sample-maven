 <h1>  Steps to clone the sample project from AWS to Eclipse with Maven plugin </h1>  

1 - Steps to get the project sample working without trouble 

 - Eclipse Java EE IDE for Web Developers.  Version: Neon.2 Release (4.6.2) Build id: 20161208-0600
 - m2e - Maven Integration for Eclipse (includes Incubating components)	1.7.0.20160603-1933	org.eclipse.m2e.feature.feature.group	Eclipse.org - m2e

-> This files orginally comes from the awslab. I modified them to my needs. <-

 - 1a: First clone via command line the git repository: 
git clone --bare https://github.com/thiagofborn/kinesis-sample-maven.git

 - Go to Eclipse and create a Java Project 
 With your file explore (In my case Finder) copy the directory "com" from the original project cloned by git from the step 1a
 and paste at the directory "src" from Eclipse. 

 - At Eclipse:
 - Right click Java Project (the one you created) - Click "Configure" -> "Convert to a Maven Project"
 - Update the Maven pom.xml File with the content: 

 <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>kinesis-learning</groupId>
  <artifactId>kinesis-learning</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <build>
    <sourceDirectory>com</sourceDirectory>
    <plugins>
      <plugin>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.5.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>
  </build>
  <dependencies>  
    	<!-- https://mvnrepository.com/artifact/com.amazonaws/aws-java-sdk-kinesis -->
		<dependency>
    		<groupId>com.amazonaws</groupId>
    		<artifactId>aws-java-sdk-kinesis</artifactId>
    		<version>1.11.176</version>
		</dependency>
		<!-- https://mvnrepository.com/artifact/com.amazonaws/amazon-kinesis-client -->
		<dependency>
    		<groupId>com.amazonaws</groupId>
    		<artifactId>amazon-kinesis-client</artifactId>
    		<version>1.8.1</version>
		</dependency>
	</dependencies>  
</project>

- Go to Maven Menu and update the project 
- Go to the the red lined file from your "Eclipse Explorer" open it and click at the issue (the lines sublined in red) and  click in "Organize imports" to fix
- Go to Maven Menu and Build 

References: 
[1] Learning Amazon Kinesis Streams Development -  http://docs.aws.amazon.com/streams/latest/dev/learning-kinesis.html
