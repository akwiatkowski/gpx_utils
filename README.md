gpx_utils
=======

Import track file
-----------------

    g = GpxUtils::TrackImporter.new
    g.add_file('track_file.gpx')
    g.coords
     => [{:lat=>52.4606258981, :lon=>16.9213317242, :time=>2012-03-24 18:48:22 +0100, :alt=>83.77}, ...]


Import waypoints file
---------------------

    g = GpxUtils::WaypointsImporter.new
    g.add_file('waypoints.gpx')
    g.pois
     => [{:lat=>49.461531, :lon=>21.160355, :time=>2012-04-30 09:10:48 +0200, :alt=>492.629486, :name=>"PKS", :sym=>"Trail Head"}, ...]


Export waypoints to GPX file
----------------------------

    g = GpxUtils::WaypointsExporter.new
    lat = 52.384444
    lon = 16.193056
    name = "point"
    cmt = "comment" # optional
    time = "created_at" # optional
    ele = 200 # 200m above sea level, optional
    sym = "Trail Head" # Garmin icon string, optional
    g.add(lat, lon, name, cmt, time, ele, sym)
    #g.add(lat, lon, name) # w/o optional parameters
    xml = g.to_xml
    xmp # GPX file content


Create waypoint files
---------------------

You can prepare your own list of waypoints and then store into Garmin eTrex device using a GPX file. At this moment there is
only possible to convert data from YAML file to GPX. It is also possible to integrate with other (web)apps.

How to use it
-------------

1. Check samples/sample_yaml_pois.yml as a template.

2. Modify it, add yours POIs.

3. Run command

  generate_garmin_waypoints -y input_file.yml > output.gpx

4. You can check inter-POI distances using

  generate_garmin_waypoints -y input_file.yml -C

   Distance conflict does not mean something is wrong. POIs can be close to each other so it
   is a good idea to have your brain turned on ;)

5. You can change inter-POI distances using 'latlon something' distance for distance checking
   explained line before.

  generate_garmin_waypoints -y samples/sample_yaml_pois.yml -C -t 1

6. You can specify output file if you don't like using >> 'file.gpx'.

  generate_garmin_waypoints -y samples/sample_yaml_pois.yml -o file.gpx


Contributing to gpx_utils
-------------------------------

[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=bobik314&url=https://github.com/akwiatkowski/gpx_utils&title=gpx_utils&language=en_GB&tags=github&category=software)

* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.


Copyright
---------

Copyright (c) 2012-2014 Aleksander Kwiatkowski. See LICENSE.txt for
further details.

