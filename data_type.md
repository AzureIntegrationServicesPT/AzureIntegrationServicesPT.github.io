# Data Type

This Filter returns the Data Type of the Variable Input as a string

## Usage

The input is a variable of any type.

Input:
```json
{
	"Test": {
		"test2":"test"
	}
}
```

Liquid:
```liquid
{
	{%assign testvar = content.Test | data_type %}
	{%assign testvar2 = content.Test.test2 | data_type %}

	"Final1":{{testvar | json}},
	"Final2":{{testva2 | json}}

}
```

Output:
```json
{
		"Final1":"Hash",
		"Final2":"String"
}
```