# Portfolio S3

## Project
As my induvidual project for i'm making a Content management system also known as a website creator. For this i have the following user stories
### User stories
|Title|User Story|Acceptance criteria|Priority|Estimate|
|---|---|---|---|---|
|Login|As a user i want to login so i can access my website creator|Given the user is not logged in when trying to log in then let user login|1|---|
|Register|As a user i want to be able to register so i can access my website creator|Given the user is not logged in when trying to register then show a register screen|2|---|
|Page creator|As a user i want to create a page so a visitor can see it|Given the user is logged in when trying to create a page then create a page with the given path|3|---|
|Page editor|As a user i want to able edit a page so there is content on it|Given the user is logged in when trying to edit content on a page then edit content on said page|4|---|
|Website viewer|As a visitor i want to see a website|Given the page exist when the visitor visit the website then show the user created page|5|---|
### Architecture:
Stack: <br/>
  React front-end<br/>
  ASP.NET back-end<br/>
  mySQL database<br/>

C4 Model:
C1:
C2:
C3:

## Learning outcomes:
### 1. You design and build user-friendly, full-stack web applications.
  #### Front-end
  For the user interface i use react due to two way data binding which means that when a UI input changes the state changes and vice versa and the great modularity of react components
  #### API gateway:
  I use an API gateway to refer all user requests to one singular access point to access all of the backend services. I decided to use ocelot a C# based api gateway this is due to me wanting to keep the languages used consistent and ocelot having support for kubernetes if i ever wanted to use that technology.
  #### Authentication:
  To authenticate user in the application i make use of Auth0. The user makes a call to auth0 and obtain a JWT token which can be used to access content safely on the backend.
  #### Database:
  For storing my data i use a SQL database the reason why i chose a SQL database instead of a noSQL database due to SQL databases having relations and multirow transactions.
  #### User Experience:
  For the user experience i have chosen to use as little clutter pages and keep relevant information on the home page and have clear descriptive labels for elements.

  

### 2. You use software tooling and methodology that continuously monitors and improve the software quality during software development.
#### Testing:
To test my application i will be using integration and unit tests to test the application. I will use the integration tests to test user stories and unit tests to test seperate parts of the code

#### Github Actions:
For these test to be useful i have added github actions which will test all of the test before being able to push to a branch. This insures bad code not reaching the builds
  ```
    steps:
      - uses: actions/checkout@v2
      - name: Setup .NET
        uses: actions/setup-dotnet@v1
        with:
          dotnet-version: 5.0.x
      - name: Restore dependencies
        run: dotnet restore
      - name: Build
        run: dotnet build --no-restore
      - name: Test
        run: dotnet test --no-build --verbosity normal
```

### 3. You design and implement a (semi)automated software release process that matches the needs of the project context.
#### Docker:
To Deploy my application I use docker due to the following reasons.
* Docker creates an image due to this the application is deployable on all systems that support docker and variables that may impact compatiblity with a system are nullified.
* Docker provides an easy way for scaling applications.

To deploy a docker container it runs through the creator mentioned steps (example below)
1. It imports the neccesarry dependencies to build and
```
FROM mcr.microsoft.com/dotnet/aspnet:3.1-focal AS base
WORKDIR /app
EXPOSE 7000

ENV ASPNETCORE_URLS=http://+:7000

# Creates a non-root user with an explicit UID and adds permission to access the /app folder
# For more info, please refer to https://aka.ms/vscode-docker-dotnet-configure-containers
RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /app
USER appuser

FROM mcr.microsoft.com/dotnet/sdk:3.1-focal AS build
WORKDIR /src
COPY ["Gateway.csproj", "./"]
RUN dotnet restore "Gateway.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "Gateway.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Gateway.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Gateway.dll"]
```
2. 

#### Github Actions:
  ```
    steps:
      - uses: actions/checkout@v2
      - name: Setup .NET
        uses: actions/setup-dotnet@v1
        with:
          dotnet-version: 5.0.x
      - name: Restore dependencies
        run: dotnet restore
      - name: Build
        run: dotnet build --no-restore
      - name: Test
        run: dotnet test --no-build --verbosity normal
```
### 4. You act in a professional manner during software development and learning.