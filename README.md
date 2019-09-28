# Azure App Configuration Example
Basic example of using Azure App Configuration with ASP.Net Core Web Application

# Usage
Install the `Microsoft.Azure.AppConfiguration.AspNetCore` NuGet package. This package is still in preview, so you need to check *Include Prerelease* checkbox on Nuget Package Manager.

Add the `ConfigureAppConfiguration()` to the `Program.cs` and configure Azure App Configuration

```csharp
public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
    WebHost
        .CreateDefaultBuilder(args)
        .ConfigureAppConfiguration((context, config) =>
        {
            var settings = config.Build();
            config.AddAzureAppConfiguration(settings["ConnectionStrings:AppConfiguration"]);
        })
        .UseStartup<Startup>();
```