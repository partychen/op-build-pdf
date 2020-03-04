# How to onboard Azure CLI Project

## How to add a new module for azure cli

To add a new module for azure cli, there are three requirements:

1. Add source code for module.
2. Add _help.py for module.
3. Add mapping for document and source code.

### Add source code for module

The modules are listed in [command_modules](https://github.com/Azure/azure-cli/tree/master/src/command_modules) folder. Add your new module into this folder like other modules. 

### Add _help.py for module

A `_help.py` must be included in your new module. You could refer to the [_help.py](https://github.com/Azure/azure-cli/blob/master/src/command_modules/azure-cli-iot/azure/cli/command_modules/iot/_help.py) of azure iot as reference.

### Add mapping for document and source code

After `_help.py` is added, go to [doc_source_map.json](https://github.com/Azure/azure-cli/blob/master/doc/sphinx/azhelpgen/doc_source_map.json) to add the mapping for document and source code. Refer to azure iot as example:
```json
"iot": "src/command_modules/azure-cli-iot/azure/cli/command_modules/iot/_help.py"
```

## Where to add metadata for azure cli

The config for the metadata is in [docfx.json](https://github.com/Azure/azure-docs-cli-python/blob/master/azure-cli-docs/docfx.json)