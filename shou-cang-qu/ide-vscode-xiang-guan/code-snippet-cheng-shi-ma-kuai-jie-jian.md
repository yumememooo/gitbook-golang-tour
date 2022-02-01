# \[Code Snippet] 程式碼快捷鍵

#### 程式碼快捷鍵

VSCODE->file->Perfernce->User sippets->go.json

* Snippet Generator extension (recommended)
* [https://snippet-generator.app/](https://snippet-generator.app) 線上編輯版

```
/{
	// Place your snippets for go here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	"Print to console": {
		"prefix": "errf",
		"body": [
			"errors.Wrapf(cause, \"failed to  %s\", name)"
		],
		"description": "errf"
	},
	"Print": {
		"prefix": "errn",
		"body": [
			"errors.New(\"xxx\")"
		],
		"description": "errf"
	},
	"Print": {
		"prefix": "stringC",
		"body": [
			"strings.Contains(s,sub)"
		],
		"description": "strings.Contains"
	},
	"Print": {
		"prefix": "Itoa",
		"body": [
			"strconv.Itoa(int)"
		],
		"description": "int to string"
	},
	"Print": {
		"prefix": "makeMap",
		"body": [
			"map_variable := make(map[key_data_type]value_data_type)"
		],
		"description": "makeMap"
	},
	"Print": {
		"prefix": "makeAry",
		"body": [
			"rad := make([]int, 128)"
		],
		"description": "makeAry"
	}
	
}
```
