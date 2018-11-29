#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat

#FROM microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-sac2016 AS base
#WORKDIR /app
#EXPOSE 60579
#EXPOSE 44333
#
#FROM docker.io/microsoft/aspnetcore
#WORKDIR /src
#COPY ["WebAppDocker/WebAppDocker.csproj", "WebAppDocker/"]
#RUN dotnet restore "WebAppDocker/WebAppDocker.csproj"
#COPY . .
#WORKDIR "/src/WebAppDocker"
#RUN dotnet build "WebAppDocker.csproj" -c Release -o /app
#
#FROM build AS publish
#RUN dotnet publish "WebAppDocker.csproj" -c Release -o /app
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app .
#ENTRYPOINT ["dotnet", "WebAppDocker.dll"]


##基于 `microsoft/dotnet:latest` 来构建我们的镜像
#FROM microsoft/dotnet:latest
#
##拷贝项目publish文件夹中的所有文件到 docker容器中的publish文件夹中  
#COPY /published
#
##设置工作目录为 `/publish` 文件夹，即容器启动默认的文件夹
#WORKDIR /published
#
##设置Docker容器对外暴露6000端口
#EXPOSE 6000
#
##使用`dotnet HelloWebApp.dll`来运行应用程序
#CMD ["dotnet", "WebAppDocker.dll","--server.urls", "http://*:6000"]
#
#FROM microsoft/dotnet:latest
#WORKDIR /app
#
## Copy csproj and restore as distinct layers
#COPY *.csproj ./
#RUN dotnet restore
#
## Copy everything else and build
#COPY . ./
#RUN dotnet publish -c Release -o out
#
## Build runtime image
#FROM microsoft/dotnet:aspnetcore-runtime
#WORKDIR /app
#COPY --from=build-env /app/out .
#ENTRYPOINT ["dotnet", "WebAppDocker.dll"]

#FROM microsoft/dotnet:2.1-aspnetcore-runtime
#WORKDIR /app
#COPY . .
#EXPOSE 80
#ENTRYPOINT ["dotnet", "WebAppDocker.dll"]

# 表示当前创建的镜像所依赖的基础镜像
FROM microsoft/dotnet:2.1-sdk

# 表示当前容器的工作目录 将要运行的web程序放在容器中的那个目录下，没有会自动创建
WORKDIR /app

# 设置对外暴露的端口，不设置默认为 80
EXPOSE  6000

# 表示会把当前目录下的Web程序文件 拷贝到 容器的 /app 文件下，
COPY  . .

# 将要执行的命令
CMD ["dotnet", "WebAppDocker.dll"]