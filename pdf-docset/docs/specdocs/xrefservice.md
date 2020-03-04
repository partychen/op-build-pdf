# I want to reference APIs for docs site.
In this article, we show you how to reference APIs published by docs.

## Step 1. Create docset for reference document.
Provision a repo with a reference docset, no modification here.

## Step 2. Build reference docset.
There are sevial modification in this step:
1. Supporting multi-version in DocFX build.
   DocFX already exports `xrefmap.yml` file, but it not support multi-version.
   
   > [!todo]
   > define multi-version format for `xrefmap.yml`.
2. Updating `Href` in Open Publishing.
   DocFX only generates the relative paths in href, Open Publishing should update them to absolute paths.
3. Rename xref map file to docset name by Open Publishing.

## Step 3. Publish reference docset.
There are following requirements:
1. Create a new xref depot in DHS for publish xrefmap file (e.g.: docs.microsoft.com/xref/).
2. Open Publish will push xref file to xref depot.

   > [!note]
   > Localized xref map file is not in scope.
   > And for now, localized repo should not push notification to xref service.
   
   > [!todo]
   > design the path to xref map file.
3. Push a message to xref servie.

## Step 4. Parsing and index API in XRef service.
The size of `xrefmap.yml` file might be large for some big reference repo (e.g. dotnet).
It is not easy to use for `docfx` and other service (e.g.: api browser).
So we require an xref service to do some actions (e.g.: analysis and query).

Xref service should do following:
1. Downloading xref map file from DHS xref depot.
2. Parsing content.
   * If it is update, generate a incremental update for xref map, and publish to azure blob.
   
     > [!note]
     > Api Browser can reuse this item.
3. Storing items into a sql/key-value/full-text database.
4. Hosting a query server, it can query APIs by following condition:
   1. Single/multi uid.
   2. Single/multi comment id.
   3. Single text in name or full name. (intellisence for vs-code plug-in)

> [!note]
> Xref service is an async. service, it may delay servial hours.

> [!todo]
> define query servie.

## Step 5. Modify `docfx.json` for other reference/conceptual docset.
Add query service url in `docfx.json`.

> [!note]
> Example for query server in `docfx.json`
> ```json
> {
>   "build": {
>     ...
>     "xref": "query:docs.mirosoft.com/xref/"
>   }
> }
> ```

> [!todo]
> Update design for query server with version.

And then rebuild and republish the documents.
