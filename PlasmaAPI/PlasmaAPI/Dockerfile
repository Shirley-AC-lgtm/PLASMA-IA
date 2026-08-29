FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY ["PlasmaAPI.csproj", "./"]
RUN dotnet restore "PlasmaAPI.csproj"

COPY . .
RUN dotnet publish "PlasmaAPI.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app

COPY --from=build /app/publish .

ENV ASPNETCORE_URLS=http://+:10000

EXPOSE 10000

ENTRYPOINT ["dotnet", "PlasmaAPI.dll"]
