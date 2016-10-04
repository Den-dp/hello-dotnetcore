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

## Swagger (Swashbuckle)

1. Add dependencies in `project.json`
    ```diff
    {
        dependencies: {
            ...
    +        "Swashbuckle.SwaggerGen": "6.0.0-beta902",
    +        "Swashbuckle.SwaggerUi": "6.0.0-beta902"
        },
        ...
    }
    ```

2. Bootstrap it in `Startup.cs`
    ```diff
    public void ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddMvc();
    +   services.AddSwaggerGen();
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        // ...
        app.UseMvc();

    +    // Enable middleware to serve generated Swagger as a JSON endpoint
    +    app.UseSwagger();

    +    // Enable middleware to serve swagger-ui assets (HTML, JS, CSS etc.)
    +    app.UseSwaggerUi();
    }
    ```

3. Navigate to [http://localhost:5000/swagger/ui/](http://localhost:5000/swagger/ui/)


## Docker

As a nice bonus this app is ready to run within docker

1. Build new image from `Dockerfile` and run
    ```bash
    docker build -t dotnetcore-api .
    docker run -it --rm -p 5000:5000 --name api dotnetcore-api
    ```

2. Open a web browser, and navigate to [http://localhost:5000/swagger/ui/](http://localhost:5000/swagger/ui/).
