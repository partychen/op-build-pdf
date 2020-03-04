# Swagger spec cheat sheet

The following sections describe which fields or content are currently supported by [docs.microsoft.com](http://docs.microsoft.com), the toolchain, and the [Swagger/OpenAPI specification](http://swagger.io/specification/). Additionally, other notes and helpful hints related to Swagger spec authoring can be found here.

## Documentation field support by object type

Not all Swagger documentation fields (summary, description, title) are supported by all Swagger object types. This is an [OpenAPI](http://swagger.io/specification/) specification restriction, not a docs.ms.com or toolchain restriction. The following table specifies which fields can be used for which object types in a Swagger *.json.

| Object type | summary | description | title |
|-------------:|:-----------:|:-----------:|:-----------:|
| [operation](http://swagger.io/specification/#operationObject) | X | X |  |
| [parameter](http://swagger.io/specification/#parameterObject) |  | X |  |
| [schema object](http://swagger.io/specification/#schemaObject) |  | X | X |

* `summary` and `title` fields are appropriate for short-form documentation of 120 characters or less.
* `description` is for long-form content, and can contain examples of use ("examples" in this context should not to be confused with the [examples](#examples-field-and-example-object) field).

## GitHub-flavored Markdown (GFM)

The OpenAPI (Swagger) specification supports [GitHub-flavored Markdown](https://guides.github.com/features/mastering-markdown/#GitHub-flavored-markdown) (GFM) in the `description` field of the following object types:

* [Info](http://swagger.io/specification/#infoObject)
* [Operation](http://swagger.io/specification/#operationObject)
* [External Documentation](http://swagger.io/specification/#externalDocumentationObject)
* [Parameter](http://swagger.io/specification/#parameterObject)
* [Response](http://swagger.io/specification/#responseObject)
* [Tag](http://swagger.io/specification/#tagObject)
* [Schema](http://swagger.io/specification/#schemaObject)

You are highly encouraged to use GFM in `description` fields for enhanced presentation of the documentation in your Swagger files. Your Markdown-formatted documentation will be rendered on docs.microsoft.com, and AutoRest will by default sanitize Markdown into plain text for code generators.

## HTML

Do **not** put HTML tags in any of the documentation fields.

## JSON request/response examples

You can provide both request and response examples using the `x-ms-examples` extension, and response (only) examples with the built-in `examples` field. An example of the required properties and parameters for every operation is **required** for a Swagger spec to pass the onboarding checklist.

### x-ms-examples

The [x-ms-examples](https://github.com/Azure/azure-rest-api-specs/blob/master/documentation/x-ms-examples.md) extension should be used for both request and response examples.

**x-ms-examples usage**

* Source:
  * [redis.json](https://github.com/Azure/azure-rest-api-specs/blob/master/arm-redis/2016-04-01/swagger/redis.json) line 67 (Redis_Create operation)
  * [RedisCacheCreate.json](https://github.com/Azure/azure-rest-api-specs/blob/master/arm-redis/2016-04-01/examples/RedisCacheCreate.json)
* Rendered: [Redis Cache **Create** operation](https://docs.microsoft.com/rest/api/redis/redis#Redis_Create) on docs.microsoft.com

### examples field and example object

You also can populate the `examples` field of your response objects with [Example Objects](http://swagger.io/specification/#exampleObject) to present response JSON. Format it as valid JSON (i.e. *don't* stuff it all into a string with `\n`s) and it'll be rendered as the raw JSON response object on docs. For an example, see the Monitor REST API reference

* Source: [insightsManagementClient_AlertRules.json](https://github.com/Azure/azure-rest-api-specs/blob/master/arm-insights/2016-03-01/swagger/insightsManagementClient_AlertRules.json#L184) line 184
* Rendered: [Monitor > AlertRules_Get](https://docs.microsoft.com/rest/api/monitor/alertrules#AlertRules_Get) (see Returns section)

## Overwrites

Not all fields support overwrites. For example, only the `summary` and `description` fields of a Swagger spec can be overwritten in REST API documentation. See the DocFx documentation for lists of which fields can be overwritten:

* [REST API](https://dotnet.github.io/docfx/tutorial/intro_overwrite_files.html#rest-api-model)
* [Managed reference](https://dotnet.github.io/docfx/tutorial/intro_overwrite_files.html#managed-reference-model)

## Swagger validation

The ADX repo has some good info on validating Swagger specs, as well as some information on their min-spec requirements for onboarding. See [Azure Swagger Validation Tools](https://github.com/Azure/adx-documentation-pr/blob/master/tools/tools.md).