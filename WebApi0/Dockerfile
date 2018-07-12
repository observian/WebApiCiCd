FROM microsoft/dotnet:2.1-sdk as build
WORKDIR /api

COPY WebApi0.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /publish

FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /publish
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "/publish/WebApi0.dll"]