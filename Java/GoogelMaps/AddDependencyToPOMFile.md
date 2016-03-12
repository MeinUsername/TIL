	
Just a reminder.

In IntelliJ it is also important to add Framework Support for Maven to the Project. This creates a pom.xml. Enable then Auto-Import. 
Add this to the pom file, that is created by IntelliJ. The context menu of the POM file allow to trigger the download. 


```xml
<dependencies>
    <dependency>
        <groupId>com.google.maps</groupId>
        <artifactId>google-maps-services</artifactId>
        <version>0.1.11</version>
    </dependency>
</dependencies>
```

