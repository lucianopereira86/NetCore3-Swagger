![titulo](/docs/titulo.JPG)

# NetCore3-Swagger

Creating a .Net Core 3 web API with Swagger. This example in complete inside the [api folder](https://github.com/lucianopereira86/NetCore3-Swagger/tree/dev/api).

## Technologies

- [.Net Core 3](https://docs.microsoft.com/pt-br/dotnet/core/whats-new/dotnet-core-3-0)
- [Visual Studio 2019](https://visualstudio.microsoft.com/pt-br/vs/)
- [Swagger](https://docs.microsoft.com/pt-br/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-3.0&tabs=visual-studio)

## Topics

- [.Net Core 3](#net-core-3)
- [Swagger](#swagger)

### .Net Core 3

Download the Visual Studio 2019 [here](https://visualstudio.microsoft.com/pt-br/vs/) and install it.

Create a new project:

![netcore01](/docs/netcore01.JPG)

Choose ASP.Net Core Web Application:

![netcore02](/docs/netcore02.JPG)

Name the project and configure the local path:

![netcore03](/docs/netcore03.JPG)

Select an empty .Net Core project and uncheck the HTTPS and Docker support options:

![netcore04](/docs/netcore04.JPG)

After the solution be compiled, create a folder named "Controllers" and add into it a class named "TestController" with an async method:

![netcore07](/docs/netcore07.JPG)

Now, let's config the "Startup" class:

![netcore08](/docs/netcore08.JPG)

Run the project in debug mode and access the URL below:

```bash
http://localhost:<API-PORT>/api/Test
```

If the "OK!" message be displayed in the browser, our web API is running!

### Swagger

Inside the Visual Studio 2019, open the Package Manager Console and run the following commands to install the Swashbuckle version compatible with .Net Core 3:

```bash
Install-Package Swashbuckle.AspNetCore -Version 5.0.0-rc3
Install-Package Swashbuckle.AspNetCore.Filters -Version 5.0.0-rc3
Install-Package Swashbuckle.AspNetCore.Annotations -Version 5.0.0-rc3
```

Open the "Startup" class again and modify the "ConfigureServices" method:

![swagger01](/docs/swagger01.JPG)

And the "Configure" method as well:

![swagger02](/docs/swagger02.JPG)

Open the project's properties window, go to "Build", check the "XML documentation file" option and type your project name with the _XML_ extension:

![swagger03_04](/docs/swagger03_04.JPG)

Go to "Debug" and type "swagger" inside the input field above the environment variables list:

![swagger04](/docs/swagger04.JPG)

| WARNING: To avoid the MSB3073 error during the compilation, edit the project's _.csproj_ file by adding the tag _OpenApiGenerateDocuments_ inside _PropertyGroup_: |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |


```xml
  <PropertyGroup>
        <TargetFramework>netcoreapp3.0</TargetFramework>
	<OpenApiGenerateDocuments>false</OpenApiGenerateDocuments>
  </PropertyGroup>
```

Inside the "TestController", put a simple annotation above the "Get" method:

![swagger03](/docs/swagger03.JPG)

Now, let's run the project again. The Swagger page will open in this URL:

```bash
http://localhost:<API-PORT>/swagger/index.html
```

This will be the result:

![swagger08](/docs/swagger08.JPG)

Try the "Get" method and the "OK!" message will return from the API.

![swagger09](/docs/swagger09.JPG)
