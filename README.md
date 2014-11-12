Freeboard Table Widget Plugin
===============

This is a widget plugin for http://freeboard.io that shows JSON data in a table.

![preview](https://github.com/daleroy1/freeboard-table/blob/master/widget.table.preview.png)

##### Requirements

This plugin uses a dynamic height which requires a change to be made to the WidgetModel. Modify the processCalculatedSetting() function and add after the following line: 
##### processCalculatedSetting()
```
self.widgetInstance.onCalculatedValueChanged(settingName, returnValue);
//force height refresh
self._heightUpdate.valueHasMutated();
```

#####Datasource Example

The JSON requires a 'header' array which contains ALL the table column heading names.  It also requires a 'data' array that contains an entry for each row, with the header name linked to the value.

#####Example JSON
```
{
	"header": [
		"Drink",
		"Taste",
		"Rating"
	],
	"data": [
		{
			"Drink" : "Beer",
			"Taste" : "Awesome"
		},
		{
			"Drink" : "Vodka",
			"Taste" : "Bland",
			"Rating" : "8"
		}			
	]
}
```

######Widget Settings

![settings](https://github.com/daleroy1/freeboard-table/blob/master/widget.table.settings.png)

#####Show Headers (default true):
If set to false, the THEAD of the table will be hidden and column headings won't be displayed.

#####Replace blank values (default blank):
By default, for any data objects that don't have all the headers listed it will display no value in the table cell. 
Set this to a value to show instead of the blank value.  For example setting it to - will show a - in place of any blank values.

#####Value (requires a JSON array):
This should point to the JSON object, for example: datasources["DrinkData"]
