# Compare Letters

This Filter compares 2 strings, ignoring punctuation and casesize, e.g: 
João and JOAO will output as true.

## Usage

The input is:

- String1
- String2

The output will be a Boolean, true if it's a match, false if it's not.

Input:
```json
{
	"CaseNoP":"JOAO",
	"noCaseP":"João"
}
```

Liquid:
```liquid
{
	{%assign test = content.CaseNoP | compare_letters: content.noCaseP %}
	"Final":{{test | json}}
}
```

Output:
```json
{
		"Final": true
}
```