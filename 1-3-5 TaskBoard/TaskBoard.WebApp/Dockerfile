FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

WORKDIR /src

COPY . . 

RUN dotnet restore "TaskBoard.WebApp/TaskBoard.WebApp.csproj"

RUN dotnet publish "TaskBoard.WebApp/TaskBoard.WebApp.csproj" -c Release -o /app/publish --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS final

WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 80

ENTRYPOINT [ "dotnet", "TaskBoard.WebApp.dll" ]

