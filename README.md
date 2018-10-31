# Sandbox

## TODO:
1. Debugging
2. Find nice tutorial for showing the ropes
3. Yeoman workflow
4. Testing

## Getting Started

`docker run -it microsoft/dotnet:2.1-sdk bash`

`docker run -it -v $(pwd):/app -w /app -p 5001:5001 -p 5000:5000 microsoft/dotnet:2.1-sdk bash`

## Commands to remember
`dotnet new` - shows templates that it can create or start with

`dotnet run` - to run the project

## Learning

Properties/launchSettings.json - had to adjust to use 0.0.0.0 for docker

Startup general infromation from here is good: https://docs.microsoft.com/en-us/aspnet/core/fundamentals/startup?view=aspnetcore-2.1#the-startup-class

## Useful links
1. https://www.blinkingcaret.com/2018/03/20/net-core-linux/
2. Debugging: https://github.com/sleemer/docker.dotnet.debug, https://github.com/OmniSharp/omnisharp-vscode/issues/1369, https://github.com/OmniSharp/omnisharp-vscode/issues/1683
https://github.com/OmniSharp/omnisharp-vscode/wiki/Attaching-to-remote-processes

## Tutorials to try
1. https://docs.microsoft.com/en-us/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=netcore-cli


## Vscode notes:

```
    {
        // Use IntelliSense to learn about possible attributes.
        // Hover to view descriptions of existing attributes.
        // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
        "version": "0.2.0",
        "configurations": [
            {
                "name": ".NET Core Attach",
                "type": "coreclr",
                "request": "attach",
                // brings up UI for you to pick the process to attach to
                "processId": "${command:pickRemoteProcess}",
                "sourceFileMap": {
                    "/app": "${workspaceRoot}"
                },
                "pipeTransport": {
                    "pipeCwd": "${workspaceRoot}",
                    "pipeProgram": "docker",
                    "pipeArgs": [
                        "exec -i modest_engelbart" // TODO: find a way to make this docker container dynamic or static
                    ],
                    "quoteArgs": false,
                    "debuggerPath": "/root/vsdbg/vsdbg"
                }
            }
        ]
    }
```

## dotnet tool

1. How do we maintain tooling dependencies like gulp?


## mssql
1. do we ignore appsettings? or do we configure another file with local password settings?

### conneciton string example
```
  "ConnectionStrings": {
    "SchoolContext": "Server=mssql;Database=sandbox;User=sa;Password=Passw0rd123!;Trusted_Connection=False;MultipleActiveResultSets=true"
  }
```