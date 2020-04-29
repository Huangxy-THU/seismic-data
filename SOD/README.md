
The fold contains all the SOD recipes I used to download seismic data from some Data Centers, e.g., [IRIS-DMC](https://ds.iris.edu/ds/nodes/dmc/). Please refer to [FDSN web service](https://www.fdsn.org/webservices/) to see the supporting Data Centers and their hosts.


## Recipes

- recipe-csvEvent-fixedNet.xml : the catalog is already downloaded using other mehtod, and the stations are set explicitly.

- recipe-IRISPH5.xml : Query seismic waveforms from [IRIS-DMC's PH5 FDSN web service](http://service.iris.edu/ph5ws/).

- recipe-GEOFON.xml  : Query seismic waveforms from [GEOFON FDSN web service](http://geofon.gfz-potsdam.de/fdsnws/).



## Some notes

- The default of [fdsnEvent](http://www.seis.sc.edu/sod/ingredients/fdsnEvent.html) is to query [USGS FDSN Event web service](https://earthquake.usgs.gov/fdsnws/event/1/), i.e., [ANSS Comprehensive Earthquake Catalog (ComCat)](https://earthquake.usgs.gov/earthquakes/search/). You can also query other Data Center's Event web service (e.g., [IRIS-DMC Event web service](http://service.iris.edu/fdsnws/event/1)).

- The default of [fdsnStation](http://www.seis.sc.edu/sod/ingredients/fdsnStation.html) is to query [IRIS-DMC FDSN Station web service](http://service.iris.edu/fdsnws/station/1/). By default this does not get restricted channels unless there is a corresponding [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html) that has a `user` and `password` specified.

- The default of [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html) is to query [IRIS-DMC FDSN dataselect web service](http://service.iris.edu/fdsnws/dataselect/1/).

- To query restricted data, set `user` and `password` in [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html).


