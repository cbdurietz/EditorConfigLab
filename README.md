# EditorConfigLab
Simple project to test the .editorconfig capabilities.

## Usage
It seems as if some attributes in the .editorconfig does not work as intended but is reset when opening the Visual Studio Viewer.

The following attributes is affected:

- Place open brace on new line for types
- Place open brace on new line for methods and local functions
- Place open brace on new line for properties, indexers, and events
- Place open brace on new line for property, indexer, and event accessors
- Place open brace on new line for anonymous methods
- Place open brace on new line for control blocks
- Place open brace on new line for anonymous types
- Place open brace on new line for object, collection, array, and with initializers
- Place open brace on new line for lambda expression

## Testing

1. Clone and open this project.
2. Open the .editorconfig separately in a stand alone editor, preferably VS Code (since it updates the files dynamically).
3. In the file, find `csharp_new_line_before_open_brace` and not its value. It's probably `all` or `none`. Id `none`, set it to `all`.
4. In Visual Studio, open the .editorconfig file in the viewer.
5. Find the list of attributes mentioned above under the Whitespeace tab. It is under the **New line preferences** section. If you have set `csharp_new_line_before_open_brace` to `all`, they should all be ticked.
6. Untick one of them. Save the file.
7. In the text editor, notice how the `csharp_new_line_before_open_brace` have changed from `all`to `none`.
8. In Visual Studio, close, then reopen the .editorconfig. All the attributes have been unticked.

## Note

The `csharp_new_line_before_open_brace` should be able to handle the following values:
- `all`
- `none`

Or, in a comma-separated list:

- `accessors`
- `anonymous_methods`
- `anonymous_types`
- `control_blocks`
- `events`
- `indexers`
- `lambdas`
- `local_functions`
- `methods`
- `object_collection_array_initializers`
- `properties`
- `types`

The latter don't seem to be supported by Visual Studio. At least not for me. If I create a comma-separated list as per the definition, Visual Studio can read it. But if I remove one of the tick boxes, it doesn't simply remove the specific item from the list, but set the whole attribute to `none`.

For more info on how it is supposed to work: [C# formatting options](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options#csharp_new_line_before_open_brace)
