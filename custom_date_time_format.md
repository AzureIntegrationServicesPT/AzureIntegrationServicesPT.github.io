# Custom Date Time Format

This Filter outputs a DateTime in the desired shape defined by the input.

For more information about DateTime in C#, see [here](https://www.c-sharpcorner.com/blogs/date-and-time-format-in-c-sharp-programming1)

## Usage

The input is:

- Date
- Date Format
- Time
- Time Format
- DateTime Format

Input:
```json
{
	"Date":"11/01/2012",
	"Time":"00:04:00"
}
```

Liquid:
{% raw %}
```
{
	{%assign test= content.Date | custom_date_time_format: "dd.MM.yyyy", content.Time, "HH:mm:ss", "yyyy-MM-ddTHH:mm:ssZ" %}
	"DateTime":{{test | json}}
}
```
{% endraw %}

Output:
```json
{
		"DateTime":"2012-01-	11T00:04:00Z"
}
```