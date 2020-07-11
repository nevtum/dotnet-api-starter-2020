Make sure the dotnet cli is installed. Start an ASP.NET core web api project

```bash
    $ dotnet new webapi -o <project-name>
```

Add [.dockerignore](./.dockerignore) and [Dockerfile](./Dockerfile) files to the root folder.
Version 3.1 of .NET core base image was used. Make sure your dll file in the Dockerfile matches
the project name.

To add json logging to your project, follow the instructions from
[Serilog's site](https://github.com/serilog/serilog-aspnetcore)

To run your application on local, enter the following commands:

```bash
    $ dotnet restore
    $ dotnet run
```

Run the following to build your Docker image:

```bash
    $ dotnet build -t <image-name> .
```

Run your built docker image:

```bash
    $ dotnet run -it --rm -p 8000:80 <image-name>
```
