---
author: Andrea Thum
date: 2015-09-20 12:02:53+00:00
draft: false
title: our events
description: "Find public workshops, community meetups, and hands-on events at Eigenbaukombinat, a makerspace in Halle (Saale), Germany."
type: page
url: /en/our-events/
---

Eigenbaukombinat hosts public workshops, community meetups, and hands-on events in Halle (Saale). Check the calendar for current dates and registration details.

<div id="termine">Loading events...
  <noscript><div id="spacestatus" style="font-size:100%;">
    <span style="color:#f2f2f2; background-color:#f0ad4e; padding:3px 5px 3px 5px; border-radius:4px;display:inline-block;">Your browser does not support JavaScript!</span>
    </div>
  </noscript>
</div>  

Our events are also available as an [iCalendar feed](https://kalender.eigenbaukombinat.de/public/public.ics).
  


<script>
  async function loadDatatermine() {
  try {
    const dataresponse = await fetch('https://eigenbaukombinat.de/api/kalender/');
    if (!dataresponse.ok) {
      throw new Error('Netzwerkantwort war nicht ok');
    }
    const data = await dataresponse.json();
    updateContent(data);
  } catch (error) {
     console.error('Fehler beim Laden der JSON-Daten: ', error);
     }
  }

  function updateContent(data) {
    const contentDiv = document.getElementById('termine');
    var json = '';
    for(var i = 0; i < 25; i++){
  //url verlinken, wenn vorhanden
    if (data[i].url) {
    summary = '<a href="'+data[i].url+'">'+data[i].summary+'</a>';
  } else {
    summary = data[i].summary;
  }
  //enddate nur anzeigen, wenn != startdate
  if (data[i].startdate != data[i].enddate) {
    enddate = ' '+data[i].enddate;
  } else {
    enddate = '';
  }
json = json + '' + data[i].startdate + ' ' + data[i].starttime + ' - ' +  data[i].enddate + ' ' + data[i].endtime + ' ' +  summary + '</br>'

  };
    contentDiv.innerHTML = `${json}`;   
  }
  
  loadDatatermine();
  setInterval(loadDatatermine, 15000);

</script>
