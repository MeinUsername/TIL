#Freemarker

Freemarker is a template language (similar to many other). This is especially about Freemarker in the Magnolia-Context

Info based on
[Fremarker Quickstart](http://freemarker.org/docs/dgui_quickstart_template.html)


##Globale Varialben
Some variable can be configured in Magnolia config (sitefn). 


## Assign

## Conditions

The belover If statement:
```Freemarker
<#if animals.python.price < animals.elephant.price>
  Pythons are cheaper than elephants today.
<#else>
  Pythons are not cheaper than elephants today.
</#if>
```

Elseif is also supported:

```Freemarker
<#if animals.python.price < animals.elephant.price>
  Pythons are cheaper than elephants today.
<#elseif animals.elephant.price < animals.python.price>
  Elephants are cheaper than pythons today.
<#else>
  Elephants and pythons cost the same today.
</#if>
```




## Loop and Conditions
```Freemarker
    <#list animals as animal>
          <div<#if animal.protected> class="protected"</#if>>
            ${animal.name} for ${animal.price} Euros
          </div>
    </#list>
```

### Loop

List can also have #else statements. Interesting for 0 Elements
```Freemarker
<#list misc.fruits>
  <p>Fruits:
  <ul>
    <#items as fruit>
      <li>${fruit}<#sep> and</#sep>
    </#items>
  </ul>
<#else>
  <p>We have no fruits.
</#list>
```

## Built-ins
[Fulllist](http://freemarker.org/docs/ref_builtins.html)


They are applied with ?{builtin-Nmae}. They can be compared with the pipes in Angular (2?).

From a first glance, the most useful seem to be:

    - has_content
    - trim                   : string
    - upper_case/lower-case  : string
    - join                   : for a list
    - split                  : split(",")
    - key / values           : in a interation
    - date/datetime/time     : [Ref](http://freemarker.org/docs/ref_builtins_string.html#ref_builtin_string_date)






## Include
Include file content
```Freemarker
<#include "/copyright_footer.html">
```
```Freemarker
<html>
<head>
  <title>Test page</title>
</head>
<body>
  <h1>Test page</h1>
  <p>Blah blah...
  <#include "/copyright_footer.html">
</body>
</html>
```
## Missing



