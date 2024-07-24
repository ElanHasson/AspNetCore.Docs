:::moniker range=">= aspnetcore-9.0"

The [OpenAPI specification](https://spec.openapis.org/oas/latest.html) is a programming language-agnostic standard for documenting HTTP APIs. This standard is supported in ASP.NET apps through a combination of built-in APIs and open-source libraries. There are three key aspects to OpenAPI integration in an application:

* Generating information about the endpoints in the app.
* Gathering the information into a format that matches the OpenAPI schema.
* Exposing the generated OpenAPI schema via a visual UI or a serialized file.

ASP.NET apps provide built-in support for generating information about endpoints in an app via the `Microsoft.AspNetCore.OpenApi` package.

The following code is generated by the ASP.NET Core minimal web API template and uses OpenAPI:

[!code-csharp[](~/fundamentals/minimal-apis/9.0-samples/WebMinOpenApi/Program.cs?name=snippet_default&highlight=5,9-12)]

In the preceding highlighted code:

* `AddOpenApi` registers services required for OpenAPI document generation into the application's DI container.
* `MapOpenApi` adds an endpoint into the application for viewing the OpenAPI document serialized into JSON.

<a name="openapinuget"></a>

## `Microsoft.AspNetCore.OpenApi` NuGet package

The [`Microsoft.AspNetCore.OpenApi`](https://www.nuget.org/packages/Microsoft.AspNetCore.OpenApi/) package provides the following features:

* Support for generating OpenAPI documents at runtime and accessing them via an endpoint on the application
* Support for "transformer" APIs that allow modifying the generated document

`Microsoft.AspNetCore.OpenApi` is added as a PackageReference to a project file:

[!code-xml[](~/fundamentals/minimal-apis/9.0-samples/WebMinOpenApi/projectFile.xml?highlight=15)]

To learn more about the `Microsoft.AspNetCore.OpenApi` package, see <xref:fundamentals/openapi/aspnetcore-openapi>.

## `Microsoft.Extensions.ApiDescription.Server` NuGet package

The [`Microsoft.Extensions.ApiDescription.Server`](https://www.nuget.org/packages/Microsoft.Extensions.ApiDescription.Server/) package provides support for generating OpenAPI documents at build time and serializing them to disk.

`Microsoft.Extensions.ApiDescription.Server` is added as a PackageReference to a project file, and
document generation at build time is enabled by setting the `OpenApiGenerateDocuments` property.
By default, the generated OpenAPI document is saved to the `obj` directory, but you can customize
the output directory by setting the `OpenApiDocumentsDirectory` property.

[!code-xml[](~/fundamentals/minimal-apis/9.0-samples/WebMinOpenApi/projectFile.xml?highlight=9-12,16-19)]

## ASP.NET Core OpenAPI source code on GitHub

* [AddOpenApi](https://github.com/dotnet/aspnetcore/blob/main/src/OpenApi/src/Extensions/OpenApiServiceCollectionExtensions.cs)
* [OpenApiDocumentService](https://github.com/dotnet/aspnetcore/blob/main/src/OpenApi/src/Services/OpenApiDocumentService.cs)
* [OpenApiOptions](https://github.com/dotnet/aspnetcore/blob/main/src/OpenApi/src/Services/OpenApiOptions.cs)

## Additional Resources

* <xref:fundamentals/minimal-apis/security>

:::moniker-end