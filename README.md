<table class="table" style="margin-top: 10px">
    <thead>
    <tr>
        <th>Title</th>
        <th>Last Updated</th>
        <th>Summary</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Dall-E package</td>
        <td>December 22, 2023</td>
        <td>Detailed description of the API of the Dall-E package.</td>
    </tr>
    </tbody>
</table>

## Overview

The Dall-E package has the following features:

- Authorization with API Token

Please make sure you take a look at the documentation from Dall-E as features are based on its API:

- [API Reference](https://platform.openai.com/docs/introduction)

## Quick start

Once you configured the package, you can list current models with this call:

```js
for(var model of pkg.dalle.api.get("/models").data)
{ 
    log(JSON.stringify(model))
}
```

Or you can generate a completion with this call:

```js
var res = pkg.dalle.api.post("/completions", {
    prompt: "Once upon a time",
    model: "text-davinci-003",
    max_tokens: 5
})
```

## Configuration

Before configuring the package you will need to create an account in OpenAI:
[OpenAI login](https://platform.openai.com/signup?launch)

Once you have your account you will be able to configure the package.

### API Token

The API token of the account. This field is required. [API Token list](https://platform.openai.com/account/api-keys)

### Organization ID

The organization ID of the account. This field is optional. [Organization ID](https://platform.openai.com/account/org-settings)


# Javascript API

The Javascript API of the dalle package has two pieces:

- **HTTP requests**
- **Flow steps**

## HTTP requests
You can make `GET`,`PUT`,`PATCH`,`DELETE` requests to the [dalle API](https://platform.openai.com/docs/introduction) like this:
```javascript
var response = pkg.dalle.api.get('/v1/models')
var response = pkg.dalle.api.post('/v1/edits', body)
var response = pkg.dalle.api.post('/v1/edits')
```

Please take a look at the documentation of the [HTTP service](https://github.com/slingr-stack/http-service)
for more information about generic requests.

## Flow Step

As an alternative option to using scripts, you can make use of Flows and Flow Steps specifically created for the package:
<details>
    <summary>Click here to see the Flow Steps</summary>

<br>

### Generic Flow Step

Generic flow step for full use of the entire package and its services.

<h3>Inputs</h3>

<table>
    <thead>
    <tr>
        <th>Label</th>
        <th>Type</th>
        <th>Required</th>
        <th>Default</th>
        <th>Visibility</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>URL (Method)</td>
        <td>choice</td>
        <td>yes</td>
        <td> - </td>
        <td>Always</td>
        <td>
            This is the http method to be used against the package. <br>
            Possible values are: <br>
            <i><strong>GET,PUT,PATCH,DELETE</strong></i>
        </td>
    </tr>
    <tr>
        <td>URL (Path)</td>
        <td>choice</td>
        <td>yes</td>
        <td> - </td>
        <td>Always</td>
        <td>
            The url to which this package will send the request. This is the exact service to which the http request will be made. <br>
            Possible values are: <br>
            <i><strong>/testPath<br>/path3<br>/path1/{testPath}<br>/path2?param2=' + httpOptions.query.param2 + '&param3=' + httpOptions.query.param3 + '<br>/path4<br></strong></i>
        </td>
    </tr>
    <tr>
        <td>Headers</td>
        <td>keyValue</td>
        <td>no</td>
        <td> - </td>
        <td>Always</td>
        <td>
            Used when you want to have a custom http header for the request.
        </td>
    </tr>
    <tr>
        <td>Query Params</td>
        <td>keyValue</td>
        <td>no</td>
        <td> - </td>
        <td>Always</td>
        <td>
            Used when you want to have a custom query params for the http call.
        </td>
    </tr>
    <tr>
        <td>Body</td>
        <td>json</td>
        <td>no</td>
        <td> - </td>
        <td>Always</td>
        <td>
            A payload of data can be sent to the server in the body of the request.
        </td>
    </tr>
    <tr>
        <td>Override Settings</td>
        <td>boolean</td>
        <td>no</td>
        <td> false </td>
        <td>Always</td>
        <td></td>
    </tr>
    <tr>
        <td>Follow Redirect</td>
        <td>boolean</td>
        <td>no</td>
        <td> false </td>
        <td> overrideSettings </td>
        <td>It Indicates that the resource has to be downloaded into a file instead of returning it in the response.</td>
    </tr>
    <tr>
        <td>Download</td>
        <td>boolean</td>
        <td>no</td>
        <td> false </td>
        <td> overrideSettings </td>
        <td>If true, the method won't return until the file has been downloaded, and it will return all the information of the file.</td>
    </tr>
    <tr>
        <td>File name</td>
        <td>text</td>
        <td>no</td>
        <td></td>
        <td> overrideSettings </td>
        <td>If provided, the file will be stored with this name. If empty, the file name will be calculated from the URL.</td>
    </tr>
    <tr>
        <td>Full response</td>
        <td> boolean </td>
        <td>no</td>
        <td> false </td>
        <td> overrideSettings </td>
        <td>Includes extended information about response</td>
    </tr>
    <tr>
        <td>Connection Timeout</td>
        <td> number </td>
        <td>no</td>
        <td> 5000 </td>
        <td> overrideSettings </td>
        <td>Connect a timeout interval in milliseconds (0 = infinity).</td>
    </tr>
    <tr>
        <td>Read Timeout</td>
        <td> number </td>
        <td>no</td>
        <td> 60000 </td>
        <td> overrideSettings </td>
        <td>Read a timeout interval in milliseconds (0 = infinity).</td>
    </tr>
    </tbody>
</table>

<h3>Outputs</h3>

<table>
    <thead>
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>response</td>
        <td>object</td>
        <td>
            Object resulting from the response to the package call.
        </td>
    </tr>
    </tbody>
</table>


</details>


## Additional Flow Step


<details>
    <summary>Click here to see the Customs Flow Steps</summary>

<br>



### Create an Image

This flow step send a prompt to the service to create an image based on the provided parameters.

<h3>Inputs</h3>

<table>
    <thead>
    <tr>
        <th>Label</th>
        <th>Type</th>
        <th>Required</th>
        <th>Default</th>
        <th>Visibility</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Prompt</td>
        <td>text</td>
        <td>no</td>
        <td> - </td>
        <td>Always</td>
        <td>
            The prompt to generate the image.
        </td>
    </tr>
    <tr>
        <td>Url</td>
        <td>boolean</td>
        <td>no</td>
        <td> true </td>
        <td>Always</td>
        <td>
            The posible return of the service.
        </td>
    </tr>
    <tr>
        <td>Size</td>
        <td>choice</td>
        <td>no</td>
        <td> 256x256 </td>
        <td>Always</td>
        <td>
            The size of the resulting image. <br> 256x256 is the default value. <br> 512x512 <br> 1024x1024 is the maximum value.
        </td>
    </tr>
    <tr>
        <td>N</td>
        <td>number</td>
        <td>no</td>
        <td> 1 </td>
        <td>Always</td>
        <td>The number of posible generations.</td>
    </tr>
    <tr>
        <td>Follow Redirect</td>
        <td>boolean</td>
        <td>no</td>
        <td> false </td>
        <td> overrideSettings </td>
        <td>Indicates that the resource has to be downloaded into a file instead of returning it in the response.</td>
    </tr>
    <tr>
        <td>Connection Timeout</td>
        <td> number </td>
        <td>no</td>
        <td> 5000 </td>
        <td> overrideSettings </td>
        <td>Connect timeout interval, in milliseconds (0 = infinity).</td>
    </tr>
    <tr>
        <td>Read Timeout</td>
        <td> number </td>
        <td>no</td>
        <td> 60000 </td>
        <td> overrideSettings </td>
        <td>Read timeout interval, in milliseconds (0 = infinity).</td>
    </tr>
    </tbody>
</table>

<h3>Outputs</h3>

<table>
    <thead>
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>response</td>
        <td>object</td>
        <td>
            Object resulting from the response to the package call.
        </td>
    </tr>
    </tbody>
</table>


</details>


For more information about how shortcuts or flow steps work, and how they are generated, take a look at the [slingr-helpgen tool](https://github.com/slingr-stack/slingr-helpgen).

## Dependencies
* HTTP Service (v1.3.7)

## About SLINGR

SLINGR is a low-code rapid application development platform that accelerates development, with robust architecture for integrations and executing custom workflows and automation.

[More info about SLINGR](https://slingr.io)

## License

This package is licensed under the Apache License 2.0. See the `LICENSE` file for more details.
