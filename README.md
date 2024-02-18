## .NET dependency injection

https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection

## Framework-provided services

When using any of the available host or app builder patterns, defaults are applied and services are registered by the framework. Consider some of the most popular host and app builder patterns:

* Host.CreateDefaultBuilder()
* Host.CreateApplicationBuilder()
* WebHost.CreateDefaultBuilder()
* WebApplication.CreateBuilder()
* WebAssemblyHostBuilder.CreateDefault
* MauiApp.CreateBuilder

## Service Lifetimes

Services can be registered with one of the following lifetimes:

* Transient: A new instance is created every time the service is requested.
* Scoped: A single instance is created per scope. The scope is typically determined by the HTTP request in a web application.
* Singleton: A single instance is created for the entire application lifetime.


## Example 

https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection-usage


```csharp
PS C:\Workspace\DependencyInjection> dotnet run
Lifetime 1: Call 1 to provider.GetRequiredService<ServiceLifetimeReporter>()
    IExampleTransientService: c69082dc-b946-45fa-88bc-f551a0f4db88 (Always different)
    IExampleScopedService: 37ef04a3-1c51-416e-a8b8-f0f0f66d1bc5 (Changes only with lifetime)
    IExampleSingletonService: 61dc4a0d-b37e-4d94-b8a3-8361a02d7d0a (Always the same)

Lifetime 1: Call 2 to provider.GetRequiredService<ServiceLifetimeReporter>()
    IExampleTransientService: 95dc46a7-db20-400d-bfbe-b4b7730b324f (Always different)
    IExampleScopedService: 37ef04a3-1c51-416e-a8b8-f0f0f66d1bc5 (Changes only with lifetime)
    IExampleSingletonService: 61dc4a0d-b37e-4d94-b8a3-8361a02d7d0a (Always the same)

Lifetime 2: Call 1 to provider.GetRequiredService<ServiceLifetimeReporter>()
    IExampleTransientService: ac238640-08e2-4978-87e9-94a090de3cd0 (Always different)
    IExampleScopedService: 255af65c-5ac7-4afd-b0c3-e9e3372b7b59 (Changes only with lifetime)
    IExampleSingletonService: 61dc4a0d-b37e-4d
```