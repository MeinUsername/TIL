Links for Reference
[Mozialla] https://developer.mozilla.org/en-US/docs/Web/API/WindowEventHandlers/onhashchange
[selfhtml] https://wiki.selfhtml.org/wiki/JavaScript/Objekte/window/location/pathname


1. Define Routes. Like /test.html#Route1 
   - Here it is importrant, that the Links are using the local file path e.g. window.location.pathname
   	A very simple router could look like this:
	```typescript
	public Router()
    {
    	//get the hash part of the location
        switch(location.hash)
        {
            case 'Page1':
                this.DrawPage("Pages1");
                break;
            case 'Page2':
                this.DrawPage("Pages1");
                break;

            default:
                console.log('Hash change. Hash is ' + location.hash);

                this.DrawQuestionPage("Pages1");

        }
    }
    ```


2. Register Hashchange Event with function for Routing
    In Typesciprt you can do this like: 
    ```typescript
    	        window.onhashchange = ()=>this.Router();
    ```


This is really a very simplisitc and static router. But could be just enaugh to be useful in a small projekt (for example a teaser)



   











