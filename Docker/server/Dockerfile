# build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish

# runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0
COPY --from=build /app/publish .
WORKDIR /app
ENV ASPNETCORE_URLS http://*:5000
ENTRYPOINT ["./AlcatrazGameServices.exe"]