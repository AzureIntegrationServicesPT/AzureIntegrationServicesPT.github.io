# Create Hash

This Filter creates a Hash Object

## Usage

The input is a null keyword or a child property.

Input:
```json
{
	"Test": null
}
```

Liquid:
{% raw %}
```
{
	{%assign test= null | create_hash %}
	{%assign test = test | add_property: "final_output", "hello world!" %}
	"Final":{{testArray | json}}
}
```
{% endraw %}
Output:
```json
{
	"Final": {
		"final_output":"hello world!"
	}
}
```