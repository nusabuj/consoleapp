#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY "*.csproj" ./
RUN dotnet restore 
COPY . ./

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/runtime:3.1-buster-slim AS base 
WORKDIR /app
COPY --from=build /src/out .
ENTRYPOINT ["dotnet", "TestApp.dll"]