# Swagger-API-Documentation
A documentation exercise of the OpenWeatherMap.org API.

The Swagger Editor can be found [here](https://editor.swagger.io/). The Swagger Editor provides a split screen view where on the left you can write your code, and on the right a Swagger UI display forms in realtime.
<br></br>
### Add the openapi object  

The `openapi` object is the root-level property of the specification document. The latest version is "3.0.2".  

![image](https://user-images.githubusercontent.com/68202736/91619444-e9a0d880-e941-11ea-8b79-29eaf240f2de.png)
<br></br>
### Add the info object  

The `info` object and its properties contains any important information about the API. The info object may indlude a title, description, contact information, license version, and/or terms of service. Many of the info object properties are optional. In this tutorial the API documentation is written in [YAML](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html). YAML indentation requires two spaces per level of identation. Tabs will not fit the formatting style. Text in the info object MUST be surrounded by quotations " ". Text in the info object is treated as a `"string"`.

>`info:`  
>&nbsp;&nbsp;`title: "OpenWeatherMap API"`

The info object and its properties in a fully filled out menu:  

![image](https://user-images.githubusercontent.com/68202736/91619352-b5c5b300-e941-11ea-9d25-89a3a843cd41.png)

>The info object JSON example:  
>
>![image](https://user-images.githubusercontent.com/68202736/91621681-ce859700-e948-11ea-845e-ede0db60beb1.png)
<br></br>
### Add the servers object  

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

Adding multiple servers to the servers object dropdown menu:

![image](https://user-images.githubusercontent.com/68202736/91619217-5b2c5700-e941-11ea-98a2-99f1448ec031.png)

>The servers object JSON example:  
>
>![image](https://user-images.githubusercontent.com/68202736/91621865-87e46c80-e949-11ea-89a2-22335298b795.png)
<br></br>
### Add the paths object

The `paths` object refers to the endpoint of the URL call. The path contains an operation object, a parameters object, a responses object, and possibly more.  

The operation object refers to the methods GET, POST, PUT, DELETE, among others. The operation object describes a single action on an API path. For the OpenWeatherMap API there is only one path `/weather`, and one method `get` for that path.  

#### Add the operation object

Adding the necessary operation object and properties to the OpenWeatherMap API path:  

![image](https://user-images.githubusercontent.com/68202736/91619044-e6f1b380-e940-11ea-9cea-b5840d85bb35.png)
<br></br>
The operation object properties and sub-objects:

| Field Name | Type | Description |
|----------- |----- | ----------- |
| **tags**       | string | A list of tags for organizing API paths. Tags can be used for logical grouping of operations by resources. Swagger UI will group paths by tag headings. |
| **summary** | string | A short summary of the operation behavior. 5-10 words in length. The summary will display in the Swagger UI menu. |
| **description** | string | A longer explanation of the operation behavior. CommonMark syntax MAY be used for formatting. |  
| externalDocs | External Documentation Object | Optional link to further documentation describing the path. |  
| **operationId** | string | A unique string identifier. The ID MUST be unique among all the operations described by the API. |
| **parameters** | Parameter Object / Reference Object | A list of parameters to help filter the information the operation returns. If a parameter is defined at the path item, this entry will override it. A unique parameter is described by a name and location. The parameter can also include a reference object that points to the description in the  compenents object. |  
| requestBody | Request Body Object / Reference Object | The request body parameters for this path. The parameter can also include a reference object that points to the description in the  compenents object. Request body parameters are only applicable by cacheable HTTP methods, mainly GET and HEAD. For more [information](https://tools.ietf.org/html/rfc7231#section-4.3.1) | 
| **responses** | Responses Body Object | **REQUIRED**. Responses provided with requests from this path. The responses object can also include a reference object that points to the description in the components object. |  
| callbacks | Map[`string`, Callback Object / Reference Object] | A map of possible callbacks related to the parent operation. Initiated after a method executes. The key value is used to identify the URL for the callback operation. The callback operation can also include a reference object that points to the description in the components object. |  
| deprecated | boolean | Declares the operation should be discontinued. The operation SHOULD not be used. Default value is false. |  
| security | Security Requirement Object | Declares what authorization method can be used with the operation. Only one security object requirement is needed to authorize a request. This definition overrides the security object at the root-level. An empty array {} can be used to remove a root-level security declaration. |  
| servers | Server Object | An alternate server array to service the operation. An alternate server object will override the server declared at the root-level. |  

**Note:** **Bold** denotes properties and objects necessary for OpenWeatherMap API.  

The operation object and its properites before the parameters object is added:

![image](https://user-images.githubusercontent.com/68202736/91619800-fbcf4680-e942-11ea-9378-ca81ee694409.png)  

>The operation object JSON example:  
>
>![image](https://user-images.githubusercontent.com/68202736/91622504-39849d00-e94c-11ea-9e5f-b851a37f16a7.png)  


#### Add the parameters object  

The `parameters` object describes a single parameter object. A unique identifier is defined by a name and a location.  

##### Parameter locations  

There are four possible locations for the parameters object in the `in` field:
- path - Does not include the basepath of the URL endpoint. `/items/{item_endpoint}` Path parameter = `{item_endpoint}`  
- query - Parameters that are appended to the URL endpoint. `/items?id=9812` Query parameter = `id`  
- header - Custom headers that are added to the request. Headers are case sensitive.  
- cookie - Passes a specific cookie value to the API.  

Adding parameter objects to the Swagger UI. 
For OpenWeatherMap the parameters object structure is as follows:  

![image](https://user-images.githubusercontent.com/68202736/91915990-d5761780-ec70-11ea-87ef-f42a8b2f6d55.png)  


The parameters object with search parameter options for city name and city ID.  

![image](https://user-images.githubusercontent.com/68202736/91915375-3ac90900-ec6f-11ea-889a-09a60c6c5657.png)  

The parameter object with search parameter options for latitude, longitude, and zip code. **Note**: Latitude and longitude MUST be used together.  

![image](https://user-images.githubusercontent.com/68202736/91931716-1124d780-ec99-11ea-9fce-8181c78550e7.png)

The parameters object with search parameter options for units and language.  

![image](https://user-images.githubusercontent.com/68202736/91916708-a496e200-ec72-11ea-850c-3d38ef13ed59.png)  

The parameters object with search parameter options for the mode of the response.  

![image](https://user-images.githubusercontent.com/68202736/91916935-59c99a00-ec73-11ea-97d4-b1f70e0847a9.png)  






















