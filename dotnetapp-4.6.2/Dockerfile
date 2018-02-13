FROM microsoft/dotnet-framework-build:4.7.1 AS build-env
WORKDIR /app
COPY . .
RUN nuget.exe restore
RUN msbuild.exe /t:Build /p:Configuration=Release /p:OutputPath=out
RUN dir /s

# FROM microsoft/dotnet-framework:4.6.2
# WORKDIR /app
# COPY bin/Release/net462 .
# ENTRYPOINT ["dotnetapp-4.6.2.exe"]

FROM microsoft/dotnet-framework:4.6.2
WORKDIR /app
COPY --from=build-env /app/out ./
ENTRYPOINT ["dotnetapp-4.6.2.exe"]
