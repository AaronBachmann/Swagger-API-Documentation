# Swagger-API-Documentation
A documentation exercise of the OpenWeatherMap.org API.

The Swagger Editor can be found [here](https://editor.swagger.io/). The Swagger Editor provides a split screen view where on the left you can write your code, and on the right a Swagger UI display forms in realtime.  

#### Add the openapi object  

The `openapi` object is the root-level property of the specification document. The latest version is "3.0.2".  

![image](https://user-images.githubusercontent.com/68202736/91367116-7b7dd980-e7ba-11ea-902e-ef32fbc579c9.png)

#### Add the info object  

The `info` object and its properties contains any important information about the API. The info object may indlude a title, description, contact information, license version, and/or terms of service. Many of the info object properties are optional. In this tutorial the API documentation is written in [YAML](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html). YAML indentation requires two spaces per level of identation. Tabs will not fit the formatting style. 

![image](https://user-images.githubusercontent.com/68202736/91366845-b59aab80-e7b9-11ea-830d-da9c556b5c88.png)  

#### Add the servers object  

The `servers` object specifies the path of the url when the API is called. The servers object is the basepath before the endpoint of the URL.  

In this case: https://api.openweathermap.org/data/2.5  

The `endpoint` is the end of the path of the URL.  

In this case: [/weather](https://api.openweathermap.org/data/2.5/weather)    

The servers object appends the endpoint to the server URL path when the API is called.  

https://api.openweathermap.org/data/2.5/weather  

Adding a servers object will create a dropdown menu in the Swagger UI layout. Mutiple servers can be added to the menu as needed. If you are doing testing, for example, you may use a test server for some API calls. 

The basic format for adding a servers object to the Swagger documentation:  

> `servers:`  
>   `- url: https://api.openweathermap.org/data/2.5`    
>         `description: Production server`

Adding multiple servers to the servers object dropdown menu:

![image](https://user-images.githubusercontent.com/68202736/91369700-504ab880-e7c1-11ea-80be-63dc3288631a.png)  











