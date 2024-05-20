# Graph traffic on OpenBSD PF labels with cacti

* Configure and run SNMP on the OpenBSD system, the default configuration is enough, if you are running this on an internal secure network, the included default `snmpd.conf` is everything you need

* Put `pf-labels.xml` somewhere on your file system so that it is accessible by everyone (including `nobody`-like accounts)

* Open the Cacti admin console, go to `Data Collection` / `Data Queries`, click `+` to create a new one

  Fill `Name`, `Description`, `XML Path` is the path to `pf-labels.xml`, set `Data Input Method` to `Get SNMP Data (Indexed)`

* Edit your new data query and `Associated Graph Templates`, select `Interface - Traffic (bytes/sec)`

  Set the first data source `traffic_in` to `pfLabelInBytes`, the second one `traffic_out` to `pfLabelOutBytes`, leave the rest empty

* Go to your host in `Management` / `Devices` and select it
  At the very bottom you will have an `Associated Data Queries` section, select `Add Data Query` with the `PF Labels` data query

  You will have the option to run it in verbose method to check if everything works as expected

  If it does, you should see as many elements as you have PF labels

* Go to `Create` / `New Graphs` and select your host

  The PF labels should be listed in `Data Query`, select the graphs and add them

  You can use `|host_description| - |query_pfLabel| - Traffic` as title to get the label in the title
