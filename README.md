# ASP.NET core API setup 2020

This is a reference project, reflecting my learnings in making cloud ready (dockerized) .NET core
applications in 2020. Below are progressive steps to get from a traditional ASP.NET core project
to something more observable and deployable to the cloud.

## Initial steps

Make sure the [dotnet cli](https://github.com/dotnet/installer) is installed. Start an ASP.NET
core web api project:

```bash
    $ dotnet new webapi -o <project-name>
```

Inside the project directory, initialize a git repo and add a .gitignore file:

```bash
    $ dotnet new gitignore
```

To run the application on your local environment, enter the following commands:

```bash
    $ dotnet restore
    $ dotnet run
```

By default, dotnet binds the API to the https port 5001.

## Set up structured logging

To add json logging to your project, follow the instructions from
[Serilog's site](https://github.com/serilog/serilog-aspnetcore). Their guide is quite comprehensive
to customize your log middleware and log formatting as it suits your needs. For the impatient, the
required changes are in [Program.cs](./Program.cs)

## Dockerizing the API

Add [.dockerignore](./.dockerignore) and [Dockerfile](./Dockerfile) files to the root folder.
Version 3.1 of .NET core base image was used. Make sure the dll file specified in the Dockerfile
matches the project name.

Make sure to have Docker installed. Run the following to build your Docker image:

```bash
    $ dotnet build -t <image-name> .
```

Run your built docker image:

```bash
    $ dotnet run -it --rm -p 8000:80 <image-name>
```

which binds the API to port 8000. Test by making a request to http://localhost:8000/WeatherForecast