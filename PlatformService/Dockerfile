FROM mcr.microsoft.com/dotnet/sdk:5.0-buster-slim AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim AS base
COPY --from=build /app/out .
ENTRYPOINT [ "dotnet", "PlatformService.dll" ]