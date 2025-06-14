# dotnetapi-docker

A sample ASP.NET8 API project with Docker support.

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
```

## Getting Started

### Build and Run with Docker Compose

1. Build docker image:
   ```sh
   docker build -t dockerapi .
   ```
2. Build and start the containers:
   ```sh
   docker compose up --build
   ```
3. The API will be available at [http://localhost:8080](http://localhost:8080) and [https://localhost:8081](https://localhost:8081)

4. Stop the containers:
   ```sh
   docker compose stop
   ```
### Project Features
- ASP.NET Core 8 Web API
- Docker support (Dockerfile & docker-compose)
- Example WeatherForecast controller
- HTTPS development certificate included

## Continuous Integration (CI)

This project uses GitHub Actions for CI. On every push to `main`, `dev`, or any `feature/*` branch, the following steps are run:

- Checkout code
- Setup .NET 8
- Restore dependencies
- Build the project
- Run tests
- Build the Docker image

See `.github/workflows/ci.yaml` for details.

## Generating a Development Certificate for Testing

To generate a self-signed development certificate for local HTTPS testing, follow these steps:

1. Open a terminal in the project directory.
2. Run the following command:
   ```sh
      # 1. Create a self-signed cert in the user's certificate store
      $cert = New-SelfSignedCertificate `
      -DnsName "localhost" `
      -CertStoreLocation "cert:\CurrentUser\My" `
      -FriendlyName "ASP.NET Core Dev Cert"

      # 2. Prepare password for export
      $pwd = ConvertTo-SecureString -String "YourPasswordHere" -Force -AsPlainText

      # 3. Export the certificate to a .pfx file
      Export-PfxCertificate `
      -Cert "cert:\CurrentUser\My\$($cert.Thumbprint)" `
      -FilePath "E:\certs\aspnetapp.pfx" `
      -Password $pwd
      ```
   - Replace `YourPasswordHere` with a password of your choice.
   - This will create a `aspnetapp.pfx` file in the `certs` directory.
3. Update your `docker-compost.yaml` or Docker configuration to use this certificate and password if needed.

For more details, see [`docs/documents.md`](docs/documents.md).

---
Feel free to modify this template for your own project needs.