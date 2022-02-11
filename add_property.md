# Add Property

This Filter Adds a property and its value, or name-value pair, to a Hash object, and returns the updated object.

The Hash Object can be a Hash Object which is a member of an Array. That indexed member will be updated and the Array returned. The Index must be an input in that case.

## Usage

The input is:

- Object: Hash/Array
- Property: String
- Value : Any
- **Optional** Index: integer

Output:
- Updated Object: Hash/Array

Input JSON:
```json
{
	"Test":
	{
		"Child1":"Hello",
		"Child2":"World!"
	},
	"Parent": 3,
	"TestArray":[
		{
			"Child1":"Hello1",
			"Child2":"World1!"
		},
		{
			"Child1":"Hello2",
			"Child2":"World2!"
		}
	]
}
```

Liquid:
```
{
	{% assign Test = content.Test | add_property: "ADDED_PROPERTY",content,Parent %}
	{% assign FArray = content.TestArray | add_property: "ADDED_PROPERTY", content.Parent , 0 %}
	"Final":{{Test | json}},
	"FinalArray":{{FArray | json}}
}
```

Output JSON:
```json
{
		"Final":
		{
			"Child1":"Hello",
			"Child2":"World!",
			"ADDED_PROPERTY": 3
		},
		"FinalArray":[
			{
				"Child1":"Hello1",
				"Child2":"World1!",
				"ADDED_PROPERTY": 3
			},
			{
				"Child1":"Hello2",
				"Child2":"World2!"
			}
		]
}
```