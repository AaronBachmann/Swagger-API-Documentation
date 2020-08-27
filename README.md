# Swagger-API-Documentation
A documentation exercise of the OpenWeatherMap.org API.

The Swagger Editor can be found [here](https://editor.swagger.io/). The Swagger Editor provides a split screen view where on the left you can write your code, and on the right a Swagger UI display forms in realtime.  
<br></br>
#### Add the openapi object  

The `openapi` object is the root-level property of the specification document. The latest version is "3.0.2".  

![image](https://user-images.githubusercontent.com/68202736/91367116-7b7dd980-e7ba-11ea-902e-ef32fbc579c9.png)
<br></br>
#### Add the info object  

The `info` object and its properties contains any important information about the API. The info object may indlude a title, description, contact information, license version, and/or terms of service. Many of the info object properties are optional. In this tutorial the API documentation is written in [YAML](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html). YAML indentation requires two spaces per level of identation. Tabs will not fit the formatting style. Text in the info object must be surrounded by quotations " ". Text in the info object is treated as a *"string"*.

>`info:`  
>&nbsp;&nbsp;`title: "OpenWeatherMap API"`
><br></br>
>The info object and its properties in a fully filled out menu:  

>![image](https://user-images.githubusercontent.com/68202736/91366845-b59aab80-e7b9-11ea-830d-da9c556b5c88.png)  
<br></br>
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
>    &nbsp;&nbsp;&nbsp;`description: Production server`
>
>Adding multiple servers to the servers object dropdown menu:
>
>![image](https://user-images.githubusercontent.com/68202736/91369700-504ab880-e7c1-11ea-80be-63dc3288631a.png)  
<br></br>

#### Add the paths object

The `paths` object refers to the endpoint of the URL call. The path contains an operation object, a parameters object, a responses object, and possibly more.  

The operation object refers to the methods GET, POST, PUT, DELETE, amongst others. The operation object describes a single action on an API path. For the OpenWeatherMap API there is only one path `/weather`, and one method `get` for that path.  

Adding an operation object to the API path:  

![image](https://user-images.githubusercontent.com/68202736/91376650-68770380-e7d2-11ea-94bd-4caad81fb43b.png)  

The operation object properties and subobjects:

| Field Name | Type | Description |
|----------- |----- | ----------- |
| tags       | string | A list of tags for API documentation control. Tags can be used for logical grouping of operations by resources or any other qualifier. |
| summary | string | A short summary of what the operation does. 5-10 words in length. The summary will display in the Swagger UI menu. |
| description | string | A longer explanation of the operation behavior. CommonMark syntax MAY be used for formatting. |
| operationId | string | A unique string identifier. MUST be unique amon all the operations of the API |
| parameters | parameter object / reference object | A list of parameters to help filter the information the operation returns. If a parameter is defined at the path item, this entry will override it. A unique parameter is described by a name and location. The parameter can also include a reference object that points to the compenents object. |










