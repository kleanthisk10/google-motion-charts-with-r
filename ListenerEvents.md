In this section we present ideas which go beyond the usual coding in
R and are somewhat experimental.

# Registering to catch events #

Google visualisations can fire and [receive events.](http://code.google.com/apis/chart/interactive/docs/reference.html#addlistener)
It exposes the following two Java Script methods:
  * `google.visualization.events.trigger()` fires an event,
  * `google.visualization.events.addListener()` listens for events.

Here is an example of registering to receive the selection event from
the Google documentation:
```
var table = new google.visualization.Table(document.getElementById('table_div'));
table.draw(data, options);
google.visualization.events.addListener(table, 'select', selectHandler);

function selectHandler() {
  alert('A table row was selected');
}
```
We will only deal with this special case of a 'select' event of the
'addListner' method. This event is available for most visualisations
and acts on user interactions, e.g. user selection clicks.

The 'addListner' method expects Java Script code, which can be embedded
into a gvis-object via `options` as (undocumented) parameter
`gvis.listener.jscode`.

Here is an example to look up the selected item in Wikipedia:
```
jscode <- "window.open('http://en.wikipedia.org/wiki/' 
                  + data.getValue(chart.getSelection()[0].row,0)); "

J1 <- gvisGeoMap(Exports, locationvar='Country', numvar='Profit',
                 options=list(dataMode="regions", gvis.listener.jscode=jscode))
plot(J1)
```
&lt;wiki:gadget url="https://docs.google.com/uc?id=0By35Mtg9R9\_RYjY0NTgwYzAtNjliMy00N2M3LWIyZjAtNGYxODg2ZWVkODA4&export=download&hl=en\_GB"  width="800" height="400" border="0"/&gt;