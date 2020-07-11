Make sure the dotnet cli is installed. Start an ASP.NET core web api project

```bash
    $ dotnet new webapi -o <project-name>
```

Add Dockerfile and .dockerignore to root folder. Version 3.1 of .NET core base image was used.

To add json logging, follow the instructions from [Serilog's site](https://github.com/serilog/serilog-aspnetcore)

Build your Docker image:

```bash
    $ dotnet build -t <image-name> .
```

Run your built docker image:

```bash
    $ dotnet run -it --rm -p 8000:80 <image-name>
```
