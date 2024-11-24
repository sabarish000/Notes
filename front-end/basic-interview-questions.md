# Interview questions

### HTML/CSS
1. In HTML why do we use DOCTYPE?
   
    DOCTYPE provides the HTML version to browser. ```<!DOCTYPE html>```
2. What is the use of head tag?

   ```<head>``` tag is the container for metadata like title, scripts, style, and links for external style sheets, scripts.
3. What is the best place to link the js files in a HTML file?

    If we are sure that script is not accessing the DOM elements, then it is better to load it in```<head>``` asynchronously using ```<script async>```.
    Otherwise, it is better to load the scripts at the end of the ```<body>```  or use ```<script defer>``` to make sure all the DOM elements are available by the time script executes.
4. ```<script>``` VS ```<script defer>``` VS ```<script async>```
       
      ![img](https://www.growingwiththeweb.com/images/2014/02/26/legend.svg)
    - The HTML file is parsed until the ```<script>``` is hit, it pauses the HTML parse and fetches the external js file and executes it and then resumes.

      ![img](https://www.growingwiththeweb.com/images/2014/02/26/script.svg)

      - The ```<script async>``` downloads the file during HTML parsing and will pause the HTML parser to execute it when it has finished downloading. Does not gaurantee the order of execution.

      ![img](https://www.growingwiththeweb.com/images/2014/02/26/script-async.svg)

      - The ```<script defer>``` downloads the file during HTML parsing and will execute it after HTML parsing. Gaurantees the order of execution.

      ![img](https://www.growingwiththeweb.com/images/2014/02/26/script-defer.svg)
6. Does HTML allow custom elements?

    Yes, it allows and renders the custom tags. By default it treats them as inline elements.
7. What is the difference between inline and block elements?
    
| Feature          | Block Elements                                 | Inline Elements                                 |
|------------------|-------------------------------------------------|-------------------------------------------------|
| **Display**      | Take up full width available                    | Take up only as much width as needed            |
| **Line Breaks**  | Start on a new line                             | Do not start on a new line                      |
| **Examples**     | `<div>`, `<h1>`, `<p>`, `<ul>`, `<section>`    | `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`    |
| **Styling**      | Can set width, height, margins, and padding     | Can set horizontal padding and margins, vertical margin is not set, vertical padding is set but doesn't affect the position; width and height usually not affected |
| **Containment**  | Can contain both block and inline elements      | Typically contain text or other inline elements |


8. How does height\width affect on inline elements like ```<img>``` ```<video>```  ```<iframe>```

   These elements are inline replaced elements whose representation is outside the scope of CSS. [ref](https://stackoverflow.com/questions/55358492/why-does-width-height-work-on-an-inline-img-element)
3. What is box model?

    Every HTML element is treated as a box and consists of Content, Padding, Border, Margin. ![img](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_model/boxmodel.png)

  ### JavaScript
4. What are different datatypes in JS?

    There are **primitive (String, Number, Bigint, Boolean, Undefined, Null, Symbol)** and **non-primitive** datatypes contain **built-in objects** like **Array, Map, Set, Promise
5. What is the typeof a function and Class

```
    function myCallback({ quantity }) {
    return quantity > 200 ? "ok" : "low";
  }

  class Employee {
    id;
    name;
  }

  // Data types
  console.log("typeof myCallback:", typeof myCallback);
  // typeof myCallback: function

  console.log("typeof Employee:", typeof Employee);
  // typeof Employee: function
    
```
    
6. What is a Promise?

  A promise is an object representing the eventual completion or failure of an async operation. It has 3 states
  - Pending
  - Fullfilled/Resolved
  - Rejected
  
  Promises are immutable and executed only once.
  It's constructor accepts a callback with 2 arguments
  - resolve
  - reject
  
  Imporatant methods:
  - then: invoked when promise is resolved.
  - catch: invoked when promise is rejected.
  - finally: invoked when promise is resolved/rejected.
  
7. Primise.all vs Primise.allSetteled vs Promise.race vs Promise.any

  - Promise.all: All or none. it follows atomicity, fails fast.
  - Primise.allSetteled: All or none but doesn't fail fast, returns all the response in an array.
  - Promise.race: Who ever wins(settles) first, it wins i.e. returns the first settled.
  - Promise.any: Waits for first fullfilled promise, if all rejected, returns the aggregated error. ```AggregateError: All promises were rejected```
8. 
3. 
3. 
3. 
3. 
3. 
3. 
3. 

 
  


