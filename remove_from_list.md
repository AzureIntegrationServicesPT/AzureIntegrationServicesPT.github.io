# Remove from List

This Filter removes an Object from an Array

## Usage

The input can be a Hash,Array,String,Integer,Boolean and the output will be an updated Array

Input:
```json
{
	"TestArray":["Child1","Child2","Child3","Child4","Child5"]
}
```

Liquid:
{% raw %}
```
{
	{%assign FArray= content.TestArray | remove_from_list: "Child2" %}
	"Final":{{FArray | json}}
}
```
{% endraw %}

Output:
```json
{
		"Final":["Child1","Child3","Child4","Child5"]
}
```