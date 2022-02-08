# Deloitte Liquid  Documentation

Deloitte's Liquid Implementation is based on [DotLiquid](https://github.com/dotliquid/dotliquid). It receives an HTTP call, in which the body is the input.
It also needs 3 headers:
- Filename: Which Liquid File to retrieve from Azure Storage
- Content-Type: Which type of content is the input ( Accepted Values: application/json, application/xml, text/csv)
- Accept: Which type of content is the output ( Accepted Values: application/json, application/xml, text/plain)

## Liquid Custom Filters

Filters are C# Functions registered and called from the Liquid Template. The Default Filters are described in the original documentation of DotLiquid.
The following filters goals are to advance the capabilities of Liquid to make it a powerful tool to Payload Transformation:

-json
-json_cur_object
-custom_date_time_format
-compare_letters
-look_up
-liquid_contains
-data_type
-int
-is_loop
-clear_nulls
-create_hash
-create_list
-add_to_list
-remove_from_list
-log
-remove_property
-add_property
-set_property
