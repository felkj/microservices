# Etapa 1: build
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copiar csproj e restaurar
COPY *.csproj ./
RUN dotnet restore

# Copiar tudo e buildar
COPY . .
RUN dotnet publish -c Release -o /app

# Etapa 2: runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
WORKDIR /app
COPY --from=build /app .

# Aqui você coloca o nome EXATO do seu projeto gerado
ENTRYPOINT ["dotnet", "Stock.dll"]
