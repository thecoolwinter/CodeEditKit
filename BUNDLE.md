# Extension Bundles

CodeEditKit can load extensions that are formatted in the `ceext` bundle structure. This structure contains a `manifest.json` that defines the extension's assets, targets, and capabilities, as well as various other folders that contain assets for the functionality of the extension.

Below we've described how to create an extension bundle, and how the information you provide is used by CodeEdit to load and parse your extension at runtime. This document is very general in the sense that each extension capability may require different `manifest.json` fields, target capabilities, assets, etc. Please use this document to get a basic understanding of how the `ceext` bundle looks, and use the capability-specific guide for more detailed information.

### Directory Structure

Each extension must be bundled in a folder ending with a `.ceext`. 

The structure of the extension bundle is defined below:

```bash
/extension.ceext
	/manifest.json
	/assets
		/ ... (static assets)
	/targets
		/{arch}
			/ ... targets
		/x86_64
			/ .. targets for x86_64
```

### Manifest File

The `manifest.json`'s fields are defined by the `ExtensionManifest` struct. The fields in the `manifest.json` file will change depending on what the extension can do (eg: a syntax extension or a UI extension). For all extensions, the following fields exist:

```json
{
 	"name": String,
 	"displayName": String,
 	"homepage": URL?,
 	"repository": URL?,
 	"issues": URL?,
}
```

>   Each extension capability has different required fields for the manifest.json file. Check the documentation for each extension type for more information on required fields.