
# Setting Options #
Setting the various options of a `googleVis` objects can be a bit
cumbersome at first. The options follow those of the Google
Visualisation API and can be set via a named list using the argument `options`.
In the following example we create a line chart and set various options.
&lt;wiki:gadget url="http://dl.dropbox.com/u/7586336/googleVisExamples/Gadgets/SettingOptions.xml" width="500" height="300" border="0"/&gt;
```
library(googleVis)
df <- data.frame(country=c("US", "GB", "BR"), val1=c(10,13,14), val2=c(23,12,32))
Line <-  gvisLineChart(df, xvar="country", yvar=c("val1","val2"),
                        options=list(
                          title="Hello World",
                          titleTextStyle="{color:'red', 
                                           fontName:'Courier', 
                                           fontSize:16}",                         
                          backgroundColor="#D3D3D3",                          
                          vAxis="{gridlines:{color:'red', count:3}}",
                          hAxis="{title:'Country', titleTextStyle:{color:'blue'}}",
		          series="[{color:'green', targetAxisIndex: 0},	
                                   {color: 'orange',targetAxisIndex:1}]",
                          vAxes="[{title:'val1'}, {title:'val2'}]",
                          legend="bottom",
                          curveType="function",
                          width=500,
                          height=300                         
                          ))
plot(Line)
```
As you can see some from the example above, the simpler options can be set by name=value,
e.g. width=500, while the more complex options with sub-components are
listed in curly brackets { }, and arrays, e.g. to define the two
axes, use square brackets [ ].

# Chart Editor (`googleVis >= 0.2.9`) #
A special option for all charts is `gvis.editor`, which puts a
button onto the page allowing the user to edit, change and customise the chart in
a browser window, see the following example.
The content of the list item `gvis.editor` describes the label
of the browser button.
```
Editor <- gvisLineChart(df, options=list(gvis.editor="Editor"))
plot(Editor)
```
&lt;wiki:gadget url="http://dl.dropbox.com/u/7586336/googleVisExamples/Gadgets/Editor.xml" width="1000" height="600" border="0"/&gt;