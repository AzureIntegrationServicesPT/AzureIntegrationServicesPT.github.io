# Json Cur Object

This Filter transforms the Input Object to a JSON object using JsonConvert C# Library with the SerializeObject Method and removes the brackets. It's conviniant when you want to output an entire object and add more Data to the output or want to write the output in CSV

When Input is String, it means the Output will be String without "".

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
{% raw %}
```
{
	{{content.Test | json_cur_object}},
	"ChildProperty": "{{content.Test.Child2 | json_cur_object }}",
}
```
{% endraw %}

Output:
```json
{
		"Child1":"Hello",
		"Child2":"World!",
		"ChildProperty": "World!",
}
```