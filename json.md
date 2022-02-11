# Json

This Filter transforms the Input Object to a JSON object using JsonConvert C# Library with the SerializeObject Method.

## Usage

The input can be a Hash,Array,String,Integer,Boolean and the output will be a JSON string

Input:
```json
{
	"Test":{
		"Child1":"Hello",
		"Child2":"World!"
	},
	"Parent": 3
}
```

Liquid:
```liquid
{
	"Final":{{content.Test | json}},
	"ChildProperty": {{content.Test.Child2 | json }},
	"ParentFinal": {{content.Parent | json }}
}
```

Output:
```json
{
		"Final":{
			"Child1":"Hello",
			"Child2":"World!"
		},
		"ChildProperty": "World!",
		"ParentFinal": 3
}
```