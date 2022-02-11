# Create List

This Filter creates an Array (List)

## Usage

The input is a null keyword

If the input is of type Hash. An Array of Hashes is created

Input:
```json
{
	"Test": null
}
```

Liquid:
```
{
	{%assign testArray= null | create_list %}
	{%assign testArray = testArray | add_to_list: content %}
	"Final":{{testArray | json}}
}
```

Output:
```json
{
	"Final":[{
	"Test": null
	}]
}
```