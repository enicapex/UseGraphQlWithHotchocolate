# Graphql with Hotchocolate
## installation
### install dotnet
[dotnet sdk](https://dotnet.microsoft.com/en-us/download)
* download and install it
### install hotchocolate templastes in dotnet cli
```cmd
    dotnet new install HotChocolate.Templates
```
### use te template .net for hotchocolate
```cmd
dotnet new graphql --name GettingStarted
```
### download Northwind database
[download](https://github.com/microsoft/sql-server-samples/blob/master/samples/databases/northwind-pubs/instnwnd.sql)

### use docker or nay other database
Install docker or sql server (any database)
```cmd
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=yourStrong(!)Password" -e "MSSQL_PID=Evaluation" -p 1433:1433  --name sqlpreview --hostname sqlpreview -d mcr.microsoft.com/mssql/server:2022-preview-ubuntu-22.04
```

### intall sqlcmd
```cmd
winget install --id Microsoft.sqlcmd –e
```

### install entityframe tools
```cmd
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```
### import northwind database
```cmd
sqlcmd -S localhost -U sa -P "yourStrong(!)Password" -Q "CREATE DATABASE Northwind;"
sqlcmd -S localhost -U sa -P "yourStrong(!)Password" -d  Northwind  -i "instnwnd (Azure SQL Database) (1).sql“
```
### convert schema strucuture to model EF
```cmd
dotnet ef dbcontext scaffold "Server=localhost;User ID=sa;Password=yourStrong(!)Password;Database=northwind;Trusted_Connection=False;Encrypt=False;" Microsoft.EntityFrameworkCore.SqlServer -o Models -f
```
### GraphQl documentation
[aqui](https://graphql.org/learn/)

### install automapper
```cmd
dotnet add package AutoMapper
dotnet add package AutoMapper.Extensions.Microsoft.DependencyInjection
```

extra services
```cs
services
    .AddQueryType<Query>();
    .AddMutationType<Mutation>()
    .AddSubscriptionType<Subscription>()
    .AddType<HelloWorldType>()
    .AddType<HelloWorldInputType>()
    .AddFiltering()
    .AddSorting()
    .AddInMemorySubscriptions()
```