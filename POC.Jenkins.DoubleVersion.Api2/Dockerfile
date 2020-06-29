#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["POC.Jenkins.DoubleVersion.Api2/POC.Jenkins.DoubleVersion.Api2.csproj", "POC.Jenkins.DoubleVersion.Api2/"]
RUN dotnet restore "POC.Jenkins.DoubleVersion.Api2/POC.Jenkins.DoubleVersion.Api2.csproj"
COPY . .
WORKDIR "/src/POC.Jenkins.DoubleVersion.Api2"
RUN dotnet build "POC.Jenkins.DoubleVersion.Api2.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "POC.Jenkins.DoubleVersion.Api2.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "POC.Jenkins.DoubleVersion.Api2.dll"]