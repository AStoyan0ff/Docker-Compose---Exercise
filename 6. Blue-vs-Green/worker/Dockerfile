FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS builder

WORKDIR /src

COPY src/Worker/Worker.csproj src/Worker/

RUN dotnet restore "src/Worker/Worker.csproj"

COPY . .

RUN dotnet publish "src/Worker/Worker.csproj" -c Release -o /out --no-restore

FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS final

WORKDIR /app

COPY --from=builder /out /app

ENTRYPOINT [ "dotnet", "Worker.dll" ]
