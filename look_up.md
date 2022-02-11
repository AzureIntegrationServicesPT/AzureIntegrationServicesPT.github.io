# Look Up

This Filter Looks up a Key inside a Hash Object.

## Usage

The input is the Hash Object and the key, the output will be the result from that search. Null or the result of the property that has that key

Why the need for this filter? Sometimes a variable has the key needed to access the Field that we want. Example, A simple Reference Data.

Input:
```json
{
	"ReferenceData":{
		"Data":{
			"Value1":"Hello",
			"Value2":"GoodBye",
			"Value3":"See you soon"
		},
	},
	"Input":{
		"Data":"Value2"
	}

}
```

Liquid:
{% raw %}
```
{
	"Final":{{content.ReferenceData.Data | look_up: content.Input.Data | json }}
}
```

Output:
```json
{
		"Final":"GoodBye"
}
```