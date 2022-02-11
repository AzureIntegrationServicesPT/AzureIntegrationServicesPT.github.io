# Int

This Filter transforms from a String to a Integer

## Usage

The input is a String to be transformed into an Integer. This filter is specially useful when a string needs to be transformed to an integer to use the Math Filters. The behaviour of the math functions is erratic with strings e.g: Plus filter with strings is concatenation, see the example below for more information.

Input:
```json
{
	"Test": "20"
}
```

Liquid:
```liquid
{

	"Final1":{{content.Test | int | plus: 1 | json}},
	"Final2":{{content.Test | plus: 1 | json}},

}
```

Output:
```json
{
		"Final1": 21,
		"Final2": "201",
}
```