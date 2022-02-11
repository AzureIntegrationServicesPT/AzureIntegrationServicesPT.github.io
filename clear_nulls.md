# Clear Nulls

This Filter removes properties that have empty strings or null values.

## Usage

The input can be a Hash or Array. The Output will be the updated Object

Input:
```json
{
	"TestArray":[{
		"Child1":"test",
		"Child2":null
	}
	],
	"Test":{
		"Child1":"",
		"Child2":"World!2"
	}
}
```

Liquid:
```
{
	{%assign FArray= content | clear_nulls %}
	{{FArray | json}}
}
```

Output:
```json
{
		"TestArray":[{
		"Child1":"test"
		},
		{
		"Child2":"World!2"
		}]
}
```