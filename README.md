# asp-dot-net-core-2-sample
A Simple ASP.NET MVC 2.0 application slightly modified to run on Cloud Foundry

This example took a generated ASP.NET DotNet Core 2.0 MVC Application from Visual Studio 2017 Community Edition (File | New | Project | Asp.NET Core Web Application | Web Application (Model-View-Controller) | ASP.NET Core 2.0)  and modified it slightly to push to Pivotal Cloud Foundry.

The key change was to remove the all inclusive Microsoft.AspNetCore.All NuGet Dependency and replace it with the following:
* Microsoft.AspNetCore
* Microsoft.AspNetCore.Mvc
* Microsoft.AspNetCore.StaticFiles
* Microsoft.VisualStudio.WebBrowserLink

You will need to publish the application before deploying it on Cloud Foundry. You can do this within Visual Studio using Build | Publish | Folder | Publish. 

Once you do that you can then deploy by running the **cf push** command in the folder where you published the application

For example

  ```bash 
  cd bin\Release\PublishedOutput
  cf push myaspdotnetapp
  ```
Alternatively, if you would prefer to use the command line you can deploy this way to Linux (Ubuntu)

  ```bash
  dotnet restore
  dotnet publish -f netcoreapp2.0 -r ubuntu.14.04-x64 
  cf push myaspdotnetapp -p bin\Debug\netcoreapp2.0\ubuntu.14.04-x64\publish
  ```
Then visit the URL in the browser to see the application running.
