# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

COPY *.sln .
COPY ./src ./src
WORKDIR /app/src/SmartCity-org-auth-api

RUN dotnet restore
RUN dotnet publish -c $BUILD_CONFIGURATION -o /app

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app .

ENV ASPNETCORE_URLS=http://+:80
EXPOSE 80

ENTRYPOINT ["dotnet", "SmartCity-org-auth-api.dll"]
