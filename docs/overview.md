# Overview

WpDotNet is the latest unmodified WordPress, compiled purely on .NET, available as a NuGet package ready to be used as a part of an ASP NET Core application. As a part of WpDotNet, there are additional components and features making it easy to be used from C# and .NET development environment in general.

The project does not require PHP to be installed, and is purely built on top of .NET technologies.

## Requirements

- .NET Core SDK 3.0 or newer. ([dotnet.microsoft.com](https://dotnet.microsoft.com/download) or [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/))
- MySQL Server ([dev.mysql.com](https://dev.mysql.com/downloads/mysql/) or [docker](https://hub.docker.com/_/mysql))

Make sure you have valid credentials to your MySQL server and you have created a database in it. The quick start expects a database named `"wordpress"`. Charset `"UTF-8"` is recommended.

## Quick Start

A demo wordpress application is available at [github.com/iolevel/peachpie-wordpress](https://github.com/iolevel/peachpie-wordpress).

Open or create an ASP NET Core application, version 3.0 or newer.

Add a package reference to `"Peachpied.WordPress.AspNetCore"` (note it is a pre-release package).

Add WordPress middleware within your request pipeline, in `Configure` startup method:

```C#
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        // ...
        app.UseWordPress();
        // ...
    }
```

Add WordPress configuration service within `ConfigureServices` startup method and setup your database connection and other options:

```C#
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddWordPress(options =>
        {
            options.DbHost = "localhost";
            options.DbName = "wordpress";
            // ...
        });
    }
```

> Note: A recommended approach is to place the configuration within `appsettings.json` configuration file. See [../configuration](configuration) for more details.

## Related links

- https://wpdotnet.peachpie.io/