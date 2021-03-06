# Map-O-Matic: easy geo data visualization
![mapomatic](http://spencertipping.com/bassomatic.jpg)

mapomatic generates `data:` URLs that become [Leaflet](http://leafletjs.com)
maps designed to display specific datasets. This means you don't need any web
hosting or temporary files to get high-quality Javascript maps.

## Usage
```sh
$ nfu perl:1..10 -m 'row rand(), rand(), "point %0"' | ./mapomatic
data:text/html;base64,ZGF0YTp0ZXh0L2h0bWwsPGh0bWw+PGhlYWQ+PGxpbmsgcmVsPSJzdHlsZXNoZWV0ImhyZWY9Imh0dHA6Ly9jZG5qcy5jbG91ZGZsYXJlLmNvbS9hamF4L2xpYnMvbGVhZmxldC8wLjcuMy9sZWFmbGV0LmNzcyIvPjxzY3JpcHQgc3JjPSJodHRwOi8vY2RuanMuY2xvdWRmbGFyZS5jb20vYWpheC9saWJzL2xlYWZsZXQvMC43LjMvbGVhZmxldC5qcyI+PC9zY3JpcHQ+PHNjcmlwdCBzcmM9Imh0dHA6Ly9jb2RlLmpxdWVyeS5jb20vanF1ZXJ5LTEuMTEuMy5taW4uanMiPjwvc2NyaXB0PjxzdHlsZT5ib2R5IHttYXJnaW46IDB9PC9zdHlsZT48L2hlYWQ+PGJvZHkgaWQ9J21hcCc+PHNjcmlwdCB0eXBlPSdnZW9kYXRhJz4wLjUzODU0NjQxMzQ4OTcxNiAwLjk4ODEzMDE5NzQ4NTEwNn4wLjA3MzE3MTYwMTIwMzQwOTIgMC43OTcwMDMzNzYxNTQ4MTJ+MC4yNjgyMDE0NDU4MjMzMjYgMC44MzU2NTAyNzgwMDc5NDd+MC4xODQ3MTMzODI0MTA2NDYgMC42Njg1MDk2OTcxMTY5Mzl+MC4zODYzNzk3MDI3MDY0ODEgMC4yMjI5NDk2NzA5MTk0MzR+MC41NjAyODgwMDM4OTQ4NTEgMC4wNTYzNzg2Nzc3MTA2MzN+MC40NDExMjAyNDczODY1OTYgMC42OTYyOTU0NDk4MjQ2ODl+MC4xNzM4MjA0OTIxODYyMiAwLjI4MTE4MzE5MTg5NTM1OX4wLjcxNjg0MjExMDQ3MzI0MSAwLjI0MjI3MDY3OTA5NTgxfjAuMzA3MTk1NTczNjQzNTkzIDAuMTUwODk5NTkzNTU5MTk1fjAuNzA5NDY1NzMzMDk4MDE4IDAuNDcwNDgxNDU2MzA1MTk0PC9zY3JpcHQ+PHNjcmlwdD4kKGZ1bmN0aW9uICgpIHt2YXIgcmYgPSBmdW5jdGlvbiAoKSB7aWYgKCQoJyNtYXAnKS5oZWlnaHQoKSAhPT0gJCh3aW5kb3cpLmhlaWdodCgpKSQoJyNtYXAnKS5oZWlnaHQoJCh3aW5kb3cpLmhlaWdodCgpKTt9OyQod2luZG93KS5yZXNpemUocmYpO3NldFRpbWVvdXQocmYsIDEwMCk7dmFyIG0gPSBMLm1hcCgnbWFwJyk7TC50aWxlTGF5ZXIoJ2h0dHA6Ly97c30udGlsZS5vc20ub3JnL3t6fS97eH0ve3l9LnBuZycse2F0dHJpYnV0aW9uOiAnJmNvcHk7IDxhIGhyZWY9Imh0dHA6Ly9vc20ub3JnL2NvcHlyaWdodCI+T3BlblN0cmVldE1hcDwvYT4gY29udHJpYnV0b3JzJ30pLmFkZFRvKG0pO3ZhciBzeSA9IDAsIHN4ID0gMDt2YXIgbHMgPSAkKCdzY3JpcHRbdHlwZT0iZ2VvZGF0YSJdJykudGV4dCgpLnJlcGxhY2UoL15ccyp8XHMqJC9nLCAnJykuc3BsaXQoL34vKTtmb3IgKHZhciBpID0gMCwgbCA9IGxzLmxlbmd0aDsgaSA8IGw7ICsraSkge3ZhciBwcyA9IGxzW2ldLnNwbGl0KC9ccysvKTt2YXIgbGwgPSBbK3BzWzBdLCArcHNbMV1dO0wubWFya2VyKGxsKS5hZGRUbyhtKS5iaW5kUG9wdXAocHMuc2xpY2UoMikuam9pbignICcpKTtzeSArPSBsbFswXTtzeCArPSBsbFsxXTt9bS5zZXRWaWV3KFtzeSAvIGxzLmxlbmd0aCwgc3ggLyBscy5sZW5ndGhdLCA0KTt9KTs8L3NjcmlwdD48L2JvZHk+PC9odG1sPg==
```

You can use it like this:

```sh
$ generate-some-data | ./mapomatic | xargs -0 xdg-open  # Linux
$ generate-some-data | ./mapomatic | xargs -0 open      # OSX
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
