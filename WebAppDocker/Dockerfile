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


##���� `microsoft/dotnet:latest` ���������ǵľ���
#FROM microsoft/dotnet:latest
#
##������Ŀpublish�ļ����е������ļ��� docker�����е�publish�ļ�����  
#COPY /published
#
##���ù���Ŀ¼Ϊ `/publish` �ļ��У�����������Ĭ�ϵ��ļ���
#WORKDIR /published
#
##����Docker�������Ⱪ¶6000�˿�
#EXPOSE 6000
#
##ʹ��`dotnet HelloWebApp.dll`������Ӧ�ó���
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

# ��ʾ��ǰ�����ľ����������Ļ�������
FROM microsoft/dotnet:2.1-sdk

# ��ʾ��ǰ�����Ĺ���Ŀ¼ ��Ҫ���е�web������������е��Ǹ�Ŀ¼�£�û�л��Զ�����
WORKDIR /app

# ���ö��Ⱪ¶�Ķ˿ڣ�������Ĭ��Ϊ 80
EXPOSE  6000

# ��ʾ��ѵ�ǰĿ¼�µ�Web�����ļ� ������ ������ /app �ļ��£�
COPY  . .

# ��Ҫִ�е�����
CMD ["dotnet", "WebAppDocker.dll"]