
FROM mcr.microsoft.com/dotnet/sdk:6.0  As base
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN  dotnet publish DockerizeMvc.csproj -c Release -o out
FROM mcr.microsoft.com/dotnet/core/aspnet
WORKDIR /app
COPY --from=base /app/out .
ENV ASPNETCORE_URLS="http://*:4500"
ENTRYPOINT ["dotnet", "DockerizeMvc.dll"]