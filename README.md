# hello-dotnetcore
Simple example of the API built on the top of the brand new .NET Core and Kestrel web server

## Get started

To create and run .NET Core project you need to:

1. Download and install [Visual Studio Code](https://code.visualstudio.com/) and [.NET Core SDK for Windows](https://www.microsoft.com/net/core).
2. Install yeoman and generate a aspnet project
    ```bash
    npm i -g yo generator-aspnet`
    yo aspnet
    # chose Web API Application
    ```

3. To locally run the app use this
    ```bash
    dotnet restore
    dotnet build #(optional, build will also happen when it's run)
    dotnet run
    ```

4. The cross-platform Kestrel web server will begin listening on port 5000.
    
5. Open a web browser, and navigate to [http://localhost:5000/api/values](http://localhost:5000/api/values).

## Docker

As a nice bonus this app is ready to run within docker

1. Build new image from `Dockerfile` and run
    ```bash
    docker build -t dotnetcore-api .
    docker run -it --rm -p 5000:5000 --name api dotnetcore-api
    ```

2. Open a web browser, and navigate to [http://localhost:5000/api/values](http://localhost:5000/api/values).
