## Vanila JS to Jquery: The Noobs Guide

I have been haunted and daunted by Javascript for almost a decade i.e. 10+ Years. These years do make a history for me in programming. Today while teaching one of my newly made friends on a quick course to programming, I stumbled upon some things that I should share and that is Javascript. Let us try to understand it with some examples. 

#### Introduction and History

The web has been inclined towards Javascript which made its cover in 1996. A company by the name of Netscape which was famous for its speedy browsers in the mid 90s summited it to the ECMA International to produce a standardized language which other browsers could implement. I still remember the awe at Netscape Navigator in the 90s. Today we know an entity by the name of Mozilla, a portmanteau of Mosaic and Godzilla. The first version was Mosiac Netscape 0.9, released in 1994.

![Mosiac Netscape](https://i.ibb.co/S74Rd43/mosaic-netscape-0-9.png)

#### Implementation of Javascript in Browser Code

Lets create a folder on your desktop by the name of noobJS and make an index.html file in it. For HTML boilerplate code, I will be using http://htmlshell.com/ 

![Boiler Plate HTML Code](https://i.ibb.co/GktVMxm/Image-004.png)

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <title>Noob JS</title>
    </head>

    <body>
        <h3>Hello Noobs!</h3>
    </body>
</html>
```

Now if you double click the file, it will run in the browser.

![Hello Noobs!](https://i.ibb.co/4FVVyRy/Image-005.png)

##### Button Click Through Vanila JS

```
<body>
    <h3>Hello Noobs!</h3>
    <button id="myFirstButton">Click</button>

    <script>
        document.getElementById('myFirstButton').onclick = function(e) {
            console.log("Yo Noobs!");
        }
    </script>
</body>
```

To start Javascript, we open a "script" tag and then close it with the same tag name. Everything in between is Javascript.

"document " is a reference to the current screen which is in view. Now using the getElementById function for document means that Javascript is going to search all elements that have an ID of myFirstButton. An element can be anything from a button or a H3 or any HTML Tag which can be given an ID just by specifying id in it. 

![Console Log](https://i.ibb.co/r736yw3/Image-006.png)

Now if you right click the browser and click inspect, we will have a console where we can print information using the console.log() function. 

Now refresh on the browser and click the button. 

![Print Console](https://i.ibb.co/LYn9qN0/Image-008.png)



##### What is JQuery?

JQuery is javascript just making it easier to write and more easier to use. It is like re-arranging the same language so that I can make it shorter, more abbreviated hence faster to implement. I would like to metaphorize it as typing Laugh Out Loud again and again but I would prefer using Lol and expect the reader to understand it. 

Lets write the same click function in JQuery. We will first import JQuery using a CDN (Content Delivery Network). Head over to https://code.jquery.com/ and click on minified jQuery Core 3.4.1

![](https://i.ibb.co/hCrHm4g/Image-009.png)

![](https://i.ibb.co/rHGRrKT/Image-010.png)

```
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <title>Noob JS</title>

        <script src="https://code.jquery.com/jquery-3.4.1.min.js"
            integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
    </head>
```

Add it to the Head of the index.html file

```
<body>
	...
    <button id="mySecondBUtton">JQuery: Click</button>
	...
</body>
<script>
document.getElementById('myFirstButton').onclick = function(e) {
	console.log("Yo Noobs!");
}

$('#mySecondBUtton').click((e) => {
	console.log("Not a Noob Anymore!! Heh!!");
});
</script>
```

Now JQuery once imported initializes with the tag of "$" and then comes the brackets which in quotes becomes a selector from the document. If with context to javascript this is getElementBy, it can either be a class with a dot or a id with a Hash. Therefore, if you compare it is way shorted just like LOLs.

![Jquery Click](https://i.ibb.co/gmtcZVF/Image-011.png)





### Making a GET Call using Vanila JS

Lets try to fetch some data through a Get Call, so that we are now communicating in the Javascript. First we need some Mock API and we have a tool for it. Head over to https://www.mocky.io/ and scroll down to the body. We will write a simple response in JSON (Javascript Object Notation).

![Mock JSON](https://i.ibb.co/WG9kvYm/Image-013.png)

Now click on Generate and it will give you an endpoint for the Get Call. 

![Endpoint](https://i.ibb.co/Z1GHJrN/Image-014.png)

Next create a new button and call it in the script tab

```
<body>
...
<button id="myFirstCall">Javascript: Get Data</button>
...
</body>
<script>
...
document.getElementById('myFirstCall').onclick = function(e) {
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
            console.log(this.responseText);
        }
    };
    xhttp.open("GET", "http://www.mocky.io/v2/5da666b83400001528633045", true);
    xhttp.send();                
}
...
</script>
```

Javascript has an class that handles all the API in the form of an object. This object allows transfer of data between a web browser and a web sever. We have created an object as var xhttp. Next we are listening if there is a change of state which detects whether the call has been run or not. this.readyState is 4 when everything is OK, which puts in a nice check so that during the call we dont break the code and response of 200 means all is good that the webserver responded successfully with some data. this.responseText contains the required data that we want to attain. 

Next we open the connection and then we send the request. Lets refresh the page and click the button.

![](https://i.ibb.co/7Cr1Sw8/Image-016.png)

As you can see we now have the response with all the wiggly brackets. Let convert the response into an object by parsing the JSON. 

```
if (this.readyState == 4 && this.status == 200) {
	console.log(JSON.parse(this.responseText));            
}
```

![](https://i.ibb.co/rs5X4mW/Image-017.png)

As you can see by just using JSON.parse() we are able to convert the response from wiggly to usable object. To get the message you can use the following code now;

```
JSON.parse(this.responseText).msg
```

##### Making a Get Call using JQuery

Lets do the same thing with JQuery

```
<body>
...
<button id="mySecondCall">JQuery: Get Data</button>
...
</body>
<script>
...
$('#mySecondCall').click((e) => {
    $.ajax({
        type: 'GET',
        dateType: 'JSON',
        url: 'http://www.mocky.io/v2/5da66a18340000a99963304c',

        success: function (data) {
            console.log(data);
        },
        error: function (error) {
            console.log(data);
        }
    });
});
...
</script>
```

Jquery has a ajax function for making communication with a web server. Ajax stands for Advanced Java and XML. You provide it with the type of call, type of response and the url and it handles the states in simple readable language. 

![](https://i.ibb.co/2YKz2Wg/Image-018.png)

As you can see the same code has been made minimal with the same type of response. 

### Conclusion

Going through Vanilla JS really makes up concept to the what is happening first hand. I do recommend everyone to attleast go through it so that a better level of understanding can be made but do acknowledge on the other hand the importance of saving time and hassle. Re-inventing the wheel does not bring much change and innovation but in todays time utilizing libraries to speed up work and save time is what one should prefer. 



##### Complete Code ~ index.html

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <title>Noob JS</title>

        <script src="https://code.jquery.com/jquery-3.4.1.min.js"
            integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
    </head>

    <body>
        <h3>Hello Noobs!</h3>
        <button id="myFirstButton">Javascript: Click</button>
        <button id="mySecondBUtton">JQuery: Click</button>
        <hr>
        <button id="myFirstCall">Javascript: Get Data</button>
        <button id="mySecondCall">JQuery: Get Data</button>

        <script>
            document.getElementById('myFirstCall').onclick = function(e) {
                var xhttp = new XMLHttpRequest();
                xhttp.onreadystatechange = function() {
                    if (this.readyState == 4 && this.status == 200) {
                        console.log(JSON.parse(this.responseText));            
                    }
                };
                xhttp.open("GET", "http://www.mocky.io/v2/5da66a18340000a99963304c", true);
                xhttp.send();                
            }

            document.getElementById('myFirstButton').onclick = function(e) {
                console.log("Yo Noobs!");
            }

            $('#mySecondBUtton').click((e) => {
                console.log("Not a Noob Anymore!! Heh!!");
            });

            $('#mySecondCall').click((e) => {
                $.ajax({
                    type: 'GET',
                    dateType: 'JSON',
                    url: 'http://www.mocky.io/v2/5da66a18340000a99963304c',

                    success: function (data) {
                        console.log(data);
                    },
                    error: function (error) {
                        console.log(data);
                    }
                });
            });
        </script>
    </body>
</html>
```

References

https://en.wikipedia.org/wiki/JavaScript

https://www.webdesignmuseum.org/web-design-history/mosaic-netscape-0-9-1994

https://en.wikipedia.org/wiki/XMLHttpRequest
