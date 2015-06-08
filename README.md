# Map-O-Matic: easy geo data visualization
![mapomatic](http://spencertipping.com/bassomatic.jpg)

mapomatic generates `data:` URLs that become [Leaflet](http://leafletjs.com)
maps designed to display specific datasets. This means you don't need any web
hosting or temporary files to get high-quality Javascript maps.

[Here's a sample map.](data:text/html,<html><head><link rel="stylesheet"href="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css"/><script src="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script><script src="http://code.jquery.com/jquery-1.11.3.min.js"></script><style>body {margin: 0}</style></head><body id='map'><script type='geodata'>0.03794717959045 0.294340659023391~0.141252322160778 0.337141188184383~0.532424359710678 0.174989649312906~0.894442954703063 0.0753170373328302~0.660416424498553 0.939706658770547~0.0644406422668844 0.109259113426994~0.118253071356765 0.15097694642624~0.819710435186149 0.981004447530829~0.639516767784531 0.997362260123765~0.462696370732782 0.771720845558782~0.510691538287478 0.143688347704071</script><script>$(function () {var rf = function () {if ($('#map').height() !== $(window).height())$('#map').height($(window).height());};$(window).resize(rf);setTimeout(rf, 100);var m = L.map('map');L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png',{attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'}).addTo(m);var sy = 0, sx = 0;var ls = $('script[type="geodata"]').text().replace(/^\s*|\s*$/g, '').split(/~/);for (var i = 0, l = ls.length; i < l; ++i) {var ps = ls[i].split(/\s+/);var ll = [+ps[0], +ps[1]];L.marker(ll).addTo(m).bindPopup(ps.slice(2).join(' '));sy += ll[0];sx += ll[1];}m.setView([sy / ls.length, sx / ls.length], 4);});</script></body></html>)

## Usage
```sh
$ nfu perl:1..10 -m 'row rand(), rand(), "point %0"' | ./mapomatic
data:text/html,<html><head><link rel="stylesheet"href="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css"/><script src="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script><script src="http://code.jquery.com/jquery-1.11.3.min.js"></script><style>body {margin: 0}</style></head><body id='map'><script type='geodata'>0.03794717959045 0.294340659023391~0.141252322160778 0.337141188184383~0.532424359710678 0.174989649312906~0.894442954703063 0.0753170373328302~0.660416424498553 0.939706658770547~0.0644406422668844 0.109259113426994~0.118253071356765 0.15097694642624~0.819710435186149 0.981004447530829~0.639516767784531 0.997362260123765~0.462696370732782 0.771720845558782~0.510691538287478 0.143688347704071</script><script>$(function () {var rf = function () {if ($('#map').height() !== $(window).height())$('#map').height($(window).height());};$(window).resize(rf);setTimeout(rf, 100);var m = L.map('map');L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png',{attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'}).addTo(m);var sy = 0, sx = 0;var ls = $('script[type="geodata"]').text().replace(/^\s*|\s*$/g, '').split(/~/);for (var i = 0, l = ls.length; i < l; ++i) {var ps = ls[i].split(/\s+/);var ll = [+ps[0], +ps[1]];L.marker(ll).addTo(m).bindPopup(ps.slice(2).join(' '));sy += ll[0];sx += ll[1];}m.setView([sy / ls.length, sx / ls.length], 4);});</script></body></html>
```

You'd probably use it like this:

```sh
$ generate-some-data | ./mapomatic | xargs -0 xdg-open          # Linux
$ generate-some-data | ./mapomatic | xargs -0 open              # OSX
```

## Input data format
The data to `mapomatic` is in this format (whitespace-delimited):

```
lat1    lng1    [note1]
lat2    lng2    [note2]
...
latN    lngN    [noteN]
```

All notes are optional; if specified, they'll be bound as text popups for the
markers.

MIT license as usual.
