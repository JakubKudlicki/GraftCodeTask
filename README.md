# GraftCodeTask – .NET Class Library for Testing Graftcode Gateway

This project is a simple **.NET Class Library** created to test integration with **Graftcode Gateway** and the **Graftcode Vision** interface (Swagger-like UI).

The library exposes public methods that are automatically analyzed and made available through the Gateway.

---

## Requirements

### Local Environment
- .NET SDK (recommended: .NET 8.0 or later)
- Graftcode Gateway (`gg`) installed locally  
  OR
- Docker Desktop (Linux containers)

> Note: `--projectKey` is a JWT token and should be treated as a secret. Do not commit it to your repository.

---

## Project Structure

- `GraftCodeTask.csproj` – .NET class library project
- `*.cs` – classes exposing public methods
- `Dockerfile` – optional container-based Gateway setup

This is a **Library project** (`OutputType=Library`) and is not meant to be executed with `dotnet run`.

## Building and Testing

Graftcode Gateway requires the compiled DLL. 

`dotnet build .\\GraftCodeTask.csproj`

`dotnet publish .\\GraftCodeTask.csproj -c Release`


1. Running Locally:

`gg --projectKey project_key --modules your_module`

Then open the Graftcode Vision interface (`http://localhost:81/GV`) to test the exposed methods.

2. Running with Docker:

`docker build --no-cache --pull -t graftcodetask:test .`
`docker run -d -p 80:80 -p 81:81 --name graftcode_task graftcodetask:test`

Then open the Graftcode Vision interface (`http://localhost:81/GV`) to test the exposed methods.
