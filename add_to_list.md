# Add to List

This Filter adds an Object to an Array

## Usage

The input can be a Hash,Array,String,Integer,Boolean and the output will be an updated Array

Input:
```json
{
	"TestArray":[{
		"Child1":"Hello1",
		"Child2":"World!1"
	}
	],
	"Test":{
		"Child1":"Hello2",
		"Child2":"World!2"
	}
}
```

Liquid:
{% raw %}
```
{
	{%assign FArray= content.TestArray | add_to_list: content.Test %}
	"Final":{{FArray | json}}
}
```
{% endraw %}
Output:
```json
{
		"Final":[{
		"Child1":"Hello1",
		"Child2":"World!1"
		},
		{
		"Child1":"Hello2",
		"Child2":"World!2"
		}]
}
```