FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine AS build
EXPOSE 80
EXPOSE 443
WORKDIR /usr/src/app
RUN apk --no-cache add curl

COPY . .
RUN dotnet restore
RUN dotnet publish -o /usr/src/app/publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine as runtime
WORKDIR /app
COPY --from=build /usr/src/app/publish /app
ENTRYPOINT ["dotnet", "HomeworkAPI.dll"]