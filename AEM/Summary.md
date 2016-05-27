#Summary of Tutorial



[Course](https://app.pluralsight.com/library/courses/building-website-adobe-experience-manager-2382/table-of-contents)
[Adoobe Docu](https://docs.adobe.com/content/docs/en/aem/6-1.html)
[Template Language/Sightly AEM 6.1](https://docs.adobe.com/docs/en/aem/6-1/develop/sightly.html)



[10 Things to know about Sightly](http://www.netcentric.biz/blog/2016/02/sightly-10-things-to-know.html)

[Adobe guide to develop components](https://helpx.adobe.com/experience-manager/using/creating-sightly-component.html)

[Sightly AEM 6.0](https://docs.adobe.com/docs/en/aem/6-0/develop/sightly.html)

AEM := Adobe Experience Manager

## Technology
    - jcr (Jackrabbit Oak )

## Terminolgy

Super Type: 
    - baseclass 
Reosurce Typoe:
    - Template that includes Page
Component: seems similar to AppBundles of Symfony/Magnolia

Templates: Similar to Magnolia
Sightly: Template language

## Directory structure

Folder:
    - apps: What we create goes here
        + /components
            + /content
                * image
                * text 
            + /structure
                * logo
                * page compoennt 
        + /templates   
        + 



Creation with Context


    - content: All content lies here (automatically build)
    - etc Design .. JS and Styles



##Building First AEM Project


Open CRXde with {Path of Instance:Port}/crx/de



Project building assistent: maven-project-setup 

Package: Java package convetion (no hyphons)
Whitespaces ("humand readable") in properties:
    - artifactName
    - componentsGroupName
    - siteName
    
After building:
```bash
    mvn clean install -P autoInstallPackage
```


Building: If ones fails, the other fail also
--> in tutorial he start mvn clean ... with sudo.



###Login :
AEM Default User/Passwort: admin/admin

##Creating a Template and Component

CRXDeLite: IDE for AEM in Quickstart Server

Templates link to Pages
TEmplates need allowed paths (globs?)

Form the template, we create a actual page 
--> asks for varialbe
--> name gives slug

The syntax defines, where to content is stored. Basically: u link your view hard against the model... strange. 


## Sightly 


### Data Types (more or less)
[Source](https://docs.adobe.com/docs/en/aem/6-0/develop/sightly/expression-language.html)

Boolean: `sightly ${true} ${false}`


String: ${'foo'} ${"bar"}
Single character escape  sequences: \\ \' \" \t \n \r \f \b  e.g .${'it\'s great'}
Unicode ${'it\u0027s great'}




### Variables

Variables access:
${properties.text}

${properties.jcr:title}   --> JCR properties

${properties['my property']} --> with spaces

${properties[myVar]} --> with variable


### Global objects

There are some global objects.
[Full List](https://docs.adobe.com/docs/en/aem/6-1/develop/sightly/global-objects.html)

Interesting (probably)

Enumerables:
    - properties
    - pageProperties
    - inheritedPageProperties

Java-backend:
    - log
    - sling
    - request
    - response
    - currentDesign
    - currentNode
    - component


### Expression Options

Act upon the variable they are attached to:

`html ${myVar @ optOne} `

Some useful expression:
- String Fomratting `${'Page {0} of {1}' @ format=[current, total]}`
- I18n 
     ```html
     ${'Page' @ i18n}
     ${'Page' @ i18n, hint='Translation Hint'}
     ${'Page {0} of {1}' @ i18n, format=[current, total]}
     ```
- Array Join
     ${['one', 'two'] @ join='; '}


### XSS Prevention --> Context 

Just html is automaitcally detected and correctly encoded. For CSS and JS a *context* has to be provided. IMHO: Actually a good thing.

```html5
<span style="color: ${properties.color @ context='styleToken'};">...</span>
<span onclick="${properties.function @ context='scriptToken'}();">...</span>
```

####Valid contexts:
[Full List](https://docs.adobe.com/docs/en/aem/6-0/develop/sightly/expression-language.html#Context Settings)

Most interesting:
    - attribute
    - scriptString   or scriptTopen
    - styleString or styleToken
  







### Conditions

#### Logical operator
Like Javascript, Java or C++

There seem to be not if statement, just a data-sly-test Block Statement

For example, the p element and its content will only be rendered if isShown is true:
```html
<p data-sly-test="${isShown}">text</p>
```

Test result can be assigned to a variable to mimic else statement. *There is no actual else statement
*
```html
<p data-sly-test.abc="${a || b || c}">is true</p>
<p data-sly-test="${!abc}">or not</p>
```

The variable, once set, has global scope within the Sightly file.


### Loops

The loop is similar to the "if"/test condition
```html
<dl data-sly-list="${currentPage.listChildren}">
    <dt>index: ${itemList.index}</dt>
    <dd>value: ${item.title}</dd>
</dl>
```

and the array can be accessed dynamically:

```html
<dl data-sly-list.child="${myObj}">
    <dt>key: ${child}</dt>
    <dd>value: ${myObj[child]}</dd>
</dl>
```

Item can be name differently like 
```
data-sly-list.parentItem


### Usage of external functions

5 ways are explained in [Sightly intro part 4](http://blogs.adobe.com/experiencedelivers/experience-management/sightly-intro-part-4/)


In general: Implement the use Interface on the Javaclass and then call the methods of the component.



### Misc

Some misc/common tricks can be found [here](http://blogs.adobe.com/experiencedelivers/experience-management/sightly-intro-part-5-faq/)



##Creating Additional Components Based on a Design PSD

##Using Clientlibs and Styles




#Interesting Links:
Search for: adobe widget api aem 6.0


