# Deloitte Liquid Azure Documentation

Deloitte's Liquid Azure Implementation is based on [DotLiquid](https://github.com/dotliquid/dotliquid). It receives an HTTP call, in which the body is the input.
It also needs 3 headers:
- Filename: Which Liquid File to retrieve from Azure Storage
- Content-Type: Which type of content is the input ( Accepted Values: application/json, application/xml, text/csv)
- Accept: Which type of content is the output ( Accepted Values: application/json, application/xml, text/plain)

The following transformation types are supported:
- JSON to JSON
- JSON to XML
- JSON to plain text / CSV
- XML to JSON
- XML to XML
- XML to plain text / CSV
- CSV to JSON
- CSV to XML

## Getting Started

### Prerequisites
- Visual Studio For Testing
- Microsoft Azure Storage Explorer
- Microsoft Azure Storage Emulator
- Azure subscription

### Usage
Post a JSON/XML/CSV payload to the URL where your function app is hosted, e.g.: http://localhost:7071/api/LiquidTransformer for Visual Studio C# Testing

```http
POST /api/LiquidTransformer HTTP/1.1
Host: localhost:7071
Content-Type: application/json
Accept: application/xml
Filename: liquidsample
{
	"name": "olaf"
}
```

Note how the name of the Liquid transform as stored in the storage account is the Filename header. This allows for a function binding to the blob.

The Liquid transformation should be stored in the Azure storage account associated with the Azure function (used for AzureWebJobsStorage) in a blob container named liquid-transforms.

For Local debugging porpuses. Use Storage Emulator and then using the Azure Storage Explorer, store your Liquid files in the Emulated storage.

Please read the [Storage Explorer documentation](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-manage-with-storage-explorer?tabs=windows) about using it.

In local.settings.json, to use Local Emulated Storage, use "UseDevelopmentStorage=true" for the variable AzureWebJobsStorage.

If you want to use your Azure Storage account, copy and paste the Connection String.

It should look like this: DefaultEndpointsProtocol=https;AccountName=(My Storage account Name);AccountKey=(SAS key);EndpointSuffix=core.windows.net 

### Deployment

The Code can be deployed to Azure as an Azure Function. For that read more about [Publishing](https://docs.microsoft.com/en-us/dotnet/core/tutorials/publishing-with-visual-studio?pivots=dotnet-6-0), [Continuous Development using Azure](https://docs.microsoft.com/en-us/azure/azure-functions/functions-continuous-deployment) or using [Terraform to deploy Azure Functions](https://adrianhall.github.io/typescript/2019/10/23/terraform-functions/).

## Liquid Objects

You can find the original implementation of Liquid in Ruby documentation [here](https://shopify.github.io/liquid/basics/introduction/). DotLiquid is based on this implementation and that documentation can help getting you started. However there are some key differences, which is noted in the [DotLiquid Documentation](https://github.com/dotliquid/dotliquid).

In DotLiquid there are the following objects:

- Hash - Equivilant to a JSON Object and [Dictionary<string,object>](https://www.tutorialsteacher.com/csharp/csharp-dictionary) in C#
- String
- Boolean
- List\<dynamic> - Equivilant to an JSON Array
- Integer
- Double
- Null

Understanding these objects, specially Hash and List , is important to knowing how the custom filters operate.

## Liquid Custom Filters

Filters are C# Functions registered and called from the Liquid Template. The Default Filters are described in the original documentation of DotLiquid.
The following filters goals are to advance the capabilities of Liquid to make it a powerful tool to Payload Transformation:

- [json](./json.html)
- [json_cur_object](./json_cur_object.html)
- [custom_date_time_format](./custom_date_time_format.html)
- [compare_letters](./compare_letters.html)
- [look_up](./look_up.html)
- [liquid_contains](./liquid_contains.html)
- [data_type](./data_type.html)
- [int](./int.html)
- [clear_nulls](./clear_nulls.html)
- [create_hash](./create_hash.html)
- [create_list](./create_list.html)
- [add_to_list](./add_to_list.html)
- [remove_from_list](./remove_from_list.html)
- [log](./log.html)
- [remove_property](./remove_property.html)
- [add_property](./add_property.html)
- [set_property](./set_property.html)


## CSV to JSON Liquid

For CSV conversion to a simple JSON use [this liquid](./CSVtoJSON.liquid)