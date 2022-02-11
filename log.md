# Log

This Filter outputs to the console for Debugging Porpuses.

## Usage

The input for better usage, should be a string

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
```
{
	"Final":{{content.Test | json}},
	{{Content.Test.Child2 | log }}
	{{Content.Test | json | log}}
```

Output:
```json
{
		"Final":{
			"Child1":"Hello",
			"Child2":"World!"
		},
}
```
Console:
```cmd
-[TIMESTAMP] - World!
-[TIMESTAMP] - {
		"Child1":"Hello",
		"Child2":"World!"
	}
```