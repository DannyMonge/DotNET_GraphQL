# WIP NetCoreMediatrSample

Sample using GraphQL implemented in .NET Core by using MediatR and identityserver4, background workers, real-time metrics, monitoring, logging and more

Some of the dependencies are:

- App.Metrics: Real time metrics and monitoring set up with InfluxDb and Grafana.
- AutoFixture: Auto generate test objects.
- FluentAssertions: Better and easier assertions in tests.
- GraphQL: GraphQL for .NET.
- Hangfire: Background worker.
- Identityserver4: OpenID Connect and OAuth 2.0 framework.
- Microsoft.EntityFrameworkCore: Object-relational mapping.
- Microsoft.Extensions.Logging: Logging API that allow other providers.
- Moq: Mocking framework used for testing.
- Sentry.io: Logging provider
- StructureMap: IoC Container.
- Xunit: Testing framework.

Running on .NET Core 2.2

## Structure

- API: Core hosting functionality including root GraphQL query and mutation.
- Features: Business logic that includes GraphQL feature queries and mutations.
- DataModel: Models for the database/store.
- UnitTest: Unit tests for the application.
- IDP: Identity Provider using Identityserver4.

## Setting up application

The application require 2 databases - one for the application it self and one for Hangfire.

1.  Create a new appsettings to your _ASPNETCORE_ENVIRONMENT_ (eg appsettings.Development.json) and add the 2 new connection strings for application and Hangfire.
2.  Run database changes to the application database by running the command `dotnet ef database update -s ../API` inside DataModel folder (see commands in _DataModel/DatabaseContext.cs_).
3.  Add connection string to the Identity server (IDP/appsettings.json or change environment and add a new appsettings). The database used for the application can also be used to the Identity server. Once the Identity server project is ran it will run the migrations for it.

## Setting up real time metrics

Real time metrics require Grafana and InfluxDb.

1.  Add InfluxDb options to appsettings.
2.  Download Grafana dashboard 

## Logging

Logging is set up with Microsoft.Extensions.Logging which means you can add logging providers by your self to it.

Sentry.io logging provider has been added to the project. This can be used or removed.

## Build and run with Docker

```
$ docker build -t aspnetapp .
$ docker run -d -p 8080:80 --name myapp aspnetapp
```
