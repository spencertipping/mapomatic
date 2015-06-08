# mapomatic: easy geo data visualization
mapomatic generates `data:` URLs that become [Leaflet](http://leafletjs.com)
maps designed to display specific datasets. This means you don't need any web
hosting or temporary files to get high-quality Javascript maps.

```sh
$ nfu perl:1..10 -m 'row rand(), rand(), "point %0"' | ./mapomatic
data:text/html,<html><head><link rel="stylesheet"href="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css"/><script src="http://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script><script src="http://code.jquery.com/jquery-1.11.3.min.js"></script><style>body {margin: 0}</style></head><body id='map'><script type='geodata'>0.460017017860995 0.549862431452738~0.648777563163218 0.66594596239424~0.684847881214484 0.584244168581776~0.857034012346357 0.914392138872323~0.125741293877955 0.531883511518345~0.971623788371101 0.248852936308573~0.483993689093939 0.938046175835339~0.39736295475495 0.321282072778665~0.368637668639 0.919264795607006~0.511303397890924 0.255259158396264~0.896075164733606 0.167823309592265</script><script>$(function () {var rf = function () {if ($('#map').height() !== $(window).height())$('#map').height($(window).height());};$(window).resize(rf);setTimeout(rf, 100);var m = L.map('map');L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png',{attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'}).addTo(m);var sy = 0, sx = 0;var ls = $('script[type="geodata"]').text().replace(/^\s*|\s*$/g, '').split(/~/);for (var i = 0, l = ls.length; i < l; ++i) {var ps = ls[i].split(/\s+/, 3);var ll = [+ps[0], +ps[1]];L.marker(ll).addTo(m).bindPopup(ps[2]);sy += ll[0];sx += ll[1];}m.setView([sy / ls.length, sx / ls.length], 4);});</script></body></html>
```

MIT license as usual.
