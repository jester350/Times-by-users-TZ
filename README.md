# Times-by-users-TZ

This small javascript code and HTML were quickly put together for a calendar Wordpress site I run for drift events. 
For events with livestreams, I normally list the times local to the UK, where I'm based, and wanted to initially have a script to calculate the times for me, which quickly expanded into showing the times based on the users own timezone settings.

The javascript simeply needs to be deployed somewhere on the webserver
The HTML firstly needs be be updated so the javascript src is correct
To amend/add dates for an event
  
  The first line which sets the eventtz is used as an offset to the local event time and UTC. So for example if the event is taking place in New York set that value to +4.
    ie <input id="eventtz" name="eventtz" type="hidden" value="+4" />
  this needs to be set as there is no way for a website to know which timezone your event is in.
  
  You then need to add your event times in the events-data json with the format NAME,Start Date & Time,End Date & Time
    <script id="events-data" type="application/json">
    [
      { "name": "Prospec Qualifying", "stime": "2023-06-22T12:30:00Z", "etime": "2023-06-22T15:30:00Z" },
      { "name": "Pro Qualifying", "stime": "2023-06-22T20:00:00Z", "etime": "2023-06-22T23:00:00Z" },
      { "name": "Prospec Top 32", "stime": "2023-06-23T14:00:00Z", "etime": "2023-06-23T17:00:00Z" },
      { "name": "Prospec Top 16", "stime": "2023-06-23T18:30:00Z", "etime": "2023-06-23T22:00:00Z" },
      { "name": "Pro Top 32", "stime": "2023-06-24T14:00:00Z", "etime": "2023-06-24T17:00:00Z" },
      { "name": "Pro Top 16", "stime": "2023-06-24T18:30:00Z", "etime": "2023-06-24T22:00:00Z" }
    ]
    </script>
The javascript reads the json and calulates the time in the users TZ, assuming their TZ is set correctly, and displays the data in a table. The dates are also formatted based on the users device settings.
