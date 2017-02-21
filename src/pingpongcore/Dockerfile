FROM microsoft/dotnet:nanoserver-sdk 

# create a directory, copy project.json, restore 
RUN mkdir app 
WORKDIR app 
COPY src/pingpongcore/project.json . 
RUN dotnet restore 
# copy app files and build the app
COPY src/pingpongcore/ . 
RUN dotnet publish -c Release -o out 

# set the entry point for the container on run
ENTRYPOINT ["dotnet", "out/pingpongcore.dll"] 

# set up network 
ENV ASPNETCORE_URLS=http://+:5000 
EXPOSE 5000 
