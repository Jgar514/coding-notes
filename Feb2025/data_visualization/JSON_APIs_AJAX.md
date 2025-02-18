# Json APIS and AJAX
- source: freeCodeCamp.org

## Get JSON with the JavaScript XMLHttpRequest Method

Remember that APIs - or Application Programming Interfaces - are tools that computers use to communicate with one another. You'll learn how to update HTML with the data we get from APIs using a technology called AJAX

Most web APIs transfer data in a format called JSON. JSON stands for JavaScript Object Notation.

JSON syntax looks very similar to JavaScript object literal notation. JSON has object properties and their current values, sandwiched between a { and a }.

However, JSON transmitted by APIs are sent as bytes, and your application receives it as a string. These can be converted into JavaScript objects, but they are not JavaScript objects by default. The JSON.parse method parses the string and constructs the JavaScript object described by it.

