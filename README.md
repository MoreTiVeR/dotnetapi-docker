# dotnetapi-docker

A sample ASP.NET Core Web API project with Docker support.

## Folder Structure

```
dotnetapi-docker/
├── .dockerignore
├── docker-compose.yml
├── Dockerfile
├── DockerAPI.sln
├── DockerAPI.csproj.user
├── DockerAPI.http
├── README.md
├── certs/
│   └── aspnetapp.pfx
├── src/
│   └── DockerAPI/
│       ├── appsettings.Development.json
│       ├── appsettings.json
│       ├── DockerAPI.csproj
│       ├── DockerAPI.csproj.user
│       ├── Program.cs
│       ├── WeatherForecast.cs
│       ├── Controllers/
│       │   └── WeatherForecastController.cs
│       ├── Properties/
│       │   └── launchSettings.json
│       ├── certs/
│       │   └── aspnetapp.pfx
│       ├── bin/
│       └── obj/
```

## Getting Started

### Build and Run with Docker Compose

1. Build and start the containers:
   ```sh
   docker compose up --build
   ```
2. The API will be available at [http://localhost:8080](http://localhost:8080)

### Project Features
- ASP.NET Core 8 Web API
- Docker support (Dockerfile & docker-compose)
- Example WeatherForecast controller
- HTTPS development certificate included

---
Feel free to modify this template for your own project needs.