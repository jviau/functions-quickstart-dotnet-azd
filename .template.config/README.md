# Microsoft.TemplateEngine Support Example

This repo can be used with `dotnet new` by adding this one file `.template.config/template.json` file.

## Usage

1. Clone repo and checkout this branch
2. `dotnet new install <cloned-path>`
3. `dotnet new functions-quickstart-dotnet-azd -o quickstart`

A folder `quickstart` will be created with the contents of this repo.

## Advanced Scenario

This further leverages the template engine for more advanced behavior:

1. Automatic restore, by default the engine will restore the project after generation. Can be skipped via `--no-restore`
   1. `dotnet new functions-quickstart-dotnet-azd -o quickstart --no-restore`
2. VNET condition as a template time decision, not bicep build time. Will include VNET by default, running with `--no-vnet` will switch to public access and drop all vnet files and values from the bicep.
   1. `dotnet new functions-quickstart-dotnet-azd -o quickstart --no-vnet`
   2. `.bicep` files are natively understood by the template engine, so the `"specialCustomOperations"` section is added to `template.json` to tell the engine what comment style the file has, and thus what template processing to use. When integrating to `func` CLI, we can add native support for bicep and any other files we want.
