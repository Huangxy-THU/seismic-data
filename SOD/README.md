
The fold contains all the SOD recipes I used to download seismic data from some Data Centers, e.g., [IRIS-DMC](https://ds.iris.edu/ds/nodes/dmc/).

You may check all the [FDSN web service supporting Data Centers](https://www.fdsn.org/webservices/). Sometimes you can use the web services directly via [wget](https://www.gnu.org/software/wget/) or [curl](https://curl.haxx.se/). Some of them may also have their own web services, which could be useful.


## eventArm

Those recipes only contain the eventArm, which can be used to download the catalog.

- [recipe-origin-mag-dep-boxarea.xml](eventArm/recipe-origin-mag-dep-boxarea.xml) : Query catalog from [USGS FDSN Event web service](https://earthquake.usgs.gov/fdsnws/event/1/), within a box area.

- [recipe-origin-mag-dep-boxarea-more.xml](eventArm/recipe-origin-mag-dep-boxarea-more.xml) : Query catalog with more conditions.

- [recipe-origin-mag-dep-pointdist.xml](eventArm/recipe-origin-mag-dep-pointdist.xml) : Query catalog within given distance range of the given lat & lon.

- [recipe-origin-mag-dep-boxarea-NC.xml](eventArm/recipe-origin-mag-dep-boxarea-NC.xml) : Query catalog from [Northern California Earthquake Data Center FDSN web service](http://service.ncedc.org/).


## networkArm

Those recipes only contain the networkArm, which can be used to search stations.

- [recipe-fixed-net-sta.xml](networkArm/recipe-fixed-net-sta.xml) : Query seismic stations from [IRIS-DMC FDSN web service](http://service.iris.edu/fdsnws/), with specic networks and stations.

- [recipe-boxarea.xml](networkArm/recipe-boxarea.xml) : Query seismic stations within a box area.

- [recipe-pointdist.xml](networkArm/recipe-pointdist.xml) : Query seismic stations within given distance range of the given lat & lon.

- [recipe-boxarea-NC.xml](networkArm/recipe-boxarea-NC.xml) : Query seismic stations from [Northern California Earthquake Data Center FDSN web service](http://service.ncedc.org/).


## waveformArm

Those recipes contain the three Arms, which are used to download seismic waveforms.

- [recipe-csvEvent-fixedNet.xml](waveformArm/recipe-csvEvent-fixedNet.xml) : Query seismic waveforms from [IRIS-DMC FDSN web service](http://service.iris.edu/fdsnws/). The catalog is already downloaded using other mehtod, and the stations are set explicitly.

- [recipe-csvEvent-fixedNet-phase.xml](waveformArm/recipe-csvEvent-fixedNet-phase.xml) : same as [recipe-csvEvent-fixedNet.xml](waveformArm/) except that a reference phase is used to limit the time window.

- [recipe-continous.xml](waveformArm/recipe-continous.xml) : Query continous seismic waveforms from [IRIS-DMC FDSN web service](http://service.iris.edu/fdsnws/). I set the output format to be miniseed.

- [recipe-IRISPH5.xml](waveformArm/recipe-IRISPH5.xml) : Query seismic waveforms from [IRIS-DMC's PH5 FDSN web service](http://service.iris.edu/ph5ws/).

- [recipe-SC.xml](waveformArm/recipe-SC.xml)      : Query seismic waveforms from [Southern California Earthquake Data Center FDSN web service](https://service.scedc.caltech.edu/)
- [recipe-NC.xml](waveformArm/recipe-NC.xml)      : Query seismic waveforms from [Northern California Earthquake Data Center FDSN web service](http://service.ncedc.org/)

- [recipe-GEOFON.xml](waveformArm/recipe-GEOFON.xml)  : Query seismic waveforms from [GEOFON FDSN web service](http://geofon.gfz-potsdam.de/fdsnws/).

- [recipe-ORFEUS.xml](waveformArm/recipe-ORFEUS.xml)  : Query seismic waveforms from [ORFEUS FDSN web service](http://www.orfeus-eu.org/fdsnws/)



## Some notes

- The default of [fdsnEvent](http://www.seis.sc.edu/sod/ingredients/fdsnEvent.html) is to query [USGS FDSN Event web service](https://earthquake.usgs.gov/fdsnws/event/1/), i.e., [ANSS Comprehensive Earthquake Catalog (ComCat)](https://earthquake.usgs.gov/earthquakes/search/). You can also query other Data Center's Event web service (e.g., [IRIS-DMC Event web service](http://service.iris.edu/fdsnws/event/1)).

- The default of [fdsnStation](http://www.seis.sc.edu/sod/ingredients/fdsnStation.html) is to query [IRIS-DMC FDSN Station web service](http://service.iris.edu/fdsnws/station/1/). By default this does not get restricted channels unless there is a corresponding [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html) that has a `user` and `password` specified.

- The default of [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html) is to query [IRIS-DMC FDSN dataselect web service](http://service.iris.edu/fdsnws/dataselect/1/).

- To query at non-default Data Center, please refer to [FDSN web service](https://www.fdsn.org/webservices/) to see the supporting Data Centers and their hosts. Here are the host names for some Data Centers.

    - [Southern California Earthquake Data Cente](https://service.scedc.caltech.edu/): `service.scedc.caltech.edu`
    - [Northern California Earthquake Data Center](http://service.ncedc.org/) : `service.ncedc.org`
    - [GEOFON](http://geofon.gfz-potsdam.de/fdsnws/): `geofon.gfz-potsdam.de`
    - [ORFEUS](http://www.orfeus-eu.org/fdsnws/) : `www.orfeus-eu.org`

- To query restricted data, set `user` and `password` in [fdsnDataSelect](http://www.seis.sc.edu/sod/ingredients/fdsnDataSelect.html).

- If you use SOD to do the `transferResponse` process, it is necessary to further multiply the waveform by `1.0e9` to convert from meters to nanometers. Please refer to SAC's `transfer` manual to check the reason: open SAC; then type `help transfer`; see `POLEZERO OPTION`. You may also refer to some Chinese tutorials about this issue: [Chinese SAC manual](https://seisman.github.io/SAC_Docs_zh/commands/transfer/) and [Difference when doing transfer using RESP and PZ](https://blog.seisman.info/resp-sacpz-difference/). In addition, choose right arguments for `transferResponse`. For example, f4 should be smaller than Nyquist frequency (if sampling rate is 0.01 s, then Nyquist frequency is 50 Hz).


