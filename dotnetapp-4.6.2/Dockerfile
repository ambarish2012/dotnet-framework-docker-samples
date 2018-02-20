FROM microsoft/dotnet-framework-build:4.7.1 AS build-env
WORKDIR /app
COPY . .
RUN nuget.exe restore
RUN msbuild.exe /t:Build /p:Configuration=Release /p:OutputPath=out
RUN Get-ChildItem -Recurse | Select-Object -ExpandProperty FullName

FROM microsoft/dotnet-framework:4.6.2
WORKDIR /app
COPY --from=build-env /app/out ./
ENTRYPOINT ["dotnetapp-4.6.2.exe"]
