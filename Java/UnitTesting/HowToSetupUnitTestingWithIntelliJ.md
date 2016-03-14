#How to setup unit testing with IntelliJ 


Sources:
[Configuring Testing Libraries](https://www.jetbrains.com/idea/help/configuring-testing-libraries.html)
[Maven for Junit](http://mvnrepository.com/artifact/junit/junit)


##How to install Junit4 ( so that it can be used with IntelliJ)
1. Open Junit in Maven and copy depency string 
2. Add depency to project.
   This is currently:
   ```XML
   <dependency>
		<groupId>junit</groupId>
		<artifactId>junit</artifactId>
		<version>4.10</version>
   </dependency>
	```



##How to create a  new test: 
1. Open Intention on the Class name  --> Click Create Test 
2. Configure the test library and the testing methods
3. Write the test code

###Remarks

- The assertEqual method expected a delta. The "old", not delte version, is declared as deprecated. 










