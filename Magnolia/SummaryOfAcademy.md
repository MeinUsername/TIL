#This is a short summary of the Magnolia Academy 

Some used shorthands 
self explaining from here on = se


# Links zu Magnolia

[Liste of Magnolia Modules](https://documentation.magnolia-cms.com/display/DOCS/List+of+modules?&pagepropertiesreport.serverrender)



# M1: Gettings started


## Installation
Simple. Register. Download. Start in tomcat-bin with magnolia_control.bat start
Don't forget to add JAVA_HOME that points to the Java Installation DIR (bin and lib subfolder)


##Configuration
###Add User
In the security Tab. se
Dont forget to add group and/or task/role. 
It seems, that the groups can have assigned roles. 


###Language Settings
- Can be changed for a single user (in the user properties)
- Can be defined for 
	- System Controls --> User Settings
	- Authoring --> localized content entry.
	- Content -->  storing and serving of localized content in the JCR.
- Language node in the configuration (defines the fallback language)





# M2: System setup

## Author and public instances

Links: 
More information: https://documentation.magnolia-cms.com/display/DOCS/Instances


Author instance: here you can change the content. It is defined by the admin property on the configuration. 
Public instance: Seen by visitors.
An author instance can be turned into a public instance. 
In Enterprise Edition can one public instance server multiple sites. 

On a producation system it is necessary to have both a separate installation.

This approach increases the security (pubic instances can not alter content). 

### Subscriper
More infos: 
The author and publich instance follow the subsriber pattenr e.g. the public instance subs to an author instances and get notified about the content. 


##Config and Data

###Node2Bean
The configuration/the configuration nodes is displayed, porteted to a Java Object. 
Is used in different places and is a fundamental mechanism.


###Java Content Repository

Links

    - [Workspaces](https://documentation.magnolia-cms.com/display/DOCS/Workspaces)
    - [JCR Browser](https://documentation.magnolia-cms.com/display/DOCS/JCR+browser)
    - [Repos] ( https://documentation.magnolia-cms.com/display/DOCS/Repositories) 

All content is stored in the *magnolia* repository and uses Apache Jackrabbit. Thty are stored to the file system and can be copied and removed from there (if necessary).
Content Repository similar to file system.



repository = hdd
workspace = partition/drive
node = folder
property = file

JCR provides certain services:

    - Author based versioning
    - Full textual searching
    - Fine-grained access control
    - Content categorization
    - Content event monitoring


The JCR Browser allows to file all content. [More Info](https://documentation.magnolia-cms.com/display/DOCS/JCR+browser)

Workspaces subdivide a repository and have there own root node ('/'). A new workspace is clasiscally needed for a new app and has to be specified in the module configuration.

```xml
<repositories>
    <repository>
      <name>magnolia</name>
      <workspaces>
        <workspace>SPECIFY_YOUR_WORKSPACE_HERE</workspace>
      </workspaces>
    </repository>
  </repositories>
</module>
```

The JCR also provides the configuration:

 Parsing/processing order | Type of properties | Location 
--------------------------| ------------------ | ------------------ 
1 |  Module properties module descriptor | (META-INF/magnolia/*.xml)
2 |  Global file properties | WEB-INF/config/magnolia.properties
3 |  Default file properties | WEB-INF/config/default/magnolia.properties
4 |  Web application file properties | WEB-INF/config/(webapp)/magnolia.properties
5 |  Context path based file properties | WEB-INF/config/(contextPath)/magnolia.properties
6 |  Server file properties | WEB-INF/config/(servername)/magnolia.properties
7 |  Web application at server file properties  | WEB-INF/config/(servername)/(webapp)/magnolia.properties
8 | System properties |  existing properties will be overwritten by available System properties


###Filter

Magnolia uses filter to intercept Request (Auth, Image Processing, etc). [Details] ( http://documentation.magnolia-cms.com/display/DOCS/Request+processing+diagrams)

The filter-chain can be configured here: Configuration  in  /server/filters.



# M3: UX and Interfaces
## The App Framework
> The most common type of app is called a 'content app'. Content apps can be created by configuration alone.

Details: 
[Apps]( http://wiki.magnolia-cms.com/display/DOCS/Apps )
[Magnolia Shell](http://wiki.magnolia-cms.com/display/DOCS/Magnolia+Shell)

[List of official apps](https://apps.magnolia-cms.com/)
The docus claims ther is a sample app, but the link is not valid. 

Different aspects of a app can be configured by the "normal user":

- App Tile
- Subapps and Subapp Details
- Dialog &  Forms, with Tabs





## Dialogs and Forms

>  entry mechanisms for two core aspects of Magnolia CMS - templates and apps

### Dialog types

[Details](https://documentation.magnolia-cms.com/display/DOCS/Dialog+types)

Variantes: 
    - Simple: single tab, simple
    - Complex: multiple tabs, hierchical entry, complex
    - Light: just one *quick entry*
    - Chooce: select a property, assets e.g. file upload

### Template Dialogs

USed to enter content or define a interface to enter content. The composition can again be defined in the configuration.


#M4: Templating

##Templates Types:

Three Types

[More](http://documentation.magnolia-cms.com/reference/templating.html)

    - Pages
    - Area: Area can be inhertitant between Sites e.g. for footer 
    - Component

##Template Definition

Contains:

    Mandatory
    - templateScript 
    - renderType 
    - dialog  
    Optional
    - title 
    - description 
    - modelClass 
    - areas 
    - parameters 
    - autoGeneration (highly optional)


## Creating Templates



