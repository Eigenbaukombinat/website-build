---
title: "Eigenbaukombinat Halle: Makerspace and Workshop"
description: "Visit the Eigenbaukombinat makerspace in Halle (Saale) for workshops, community events, shared tools and hands-on projects."
---

Eigenbaukombinat Halle e.V. is a community workshop and makerspace in Halle (Saale), Germany. Members share tools and machines, work on their own projects, and exchange practical skills.

Visitors can meet us at public events. Find information about [opening hours](/en/opening/), [events](/en/our-events/), and [membership](/en/join-us/).
<div id="space">Lade Daten...
  <noscript>
    <div id="spacestatus" style="font-size:100%;">
      <span style="color:#f2f2f2; background-color:#f0ad4e; padding:3px 5px 3px 5px; border-radius:4px;display:inline-block;">Your browser does not support JavaScript!</span>
    </div>
 </noscript> 
</div>

<script>
  async function loadDataStatus() {
  try {
    const dataresponse = await fetch('https://eigenbaukombinat.de/status/status.json');
    if (!dataresponse.ok) {
      throw new Error('Netzwerkantwort war nicht ok');
    }
    const data = await dataresponse.json();
    updateContentStatus(data);
  } catch (error) {
     console.error('Fehler beim Laden der JSON-Daten: ', error);
     }
  }

  function updateContentStatus(data) {
    const contentDiv = document.getElementById('space');
    if (data['state']['open']) {
    var json = '';
    json = `<span style="color:#f2f2f2; background-color:#5cb85c; padding:3px 5px 3px 5px; border-radius:4px; display:inline-block;">Eigenbaukombinat is <span id="howlong"></span> open!</span>`;
  } else {
    json = '<span style="color:#f2f2f2; background-color:#f0ad4e; padding:3px 5px 3px 5px; border-radius:4px;display:inline-block;">Eigenbaukombinat is closed.</span>';
  };
  contentDiv.innerHTML = `${json}`;
  };

  async function loadDataHowlong() {
  try {
    const dataresponse = await fetch('https://eigenbaukombinat.de/status/openuntil.json');
    if (!dataresponse.ok) {
      throw new Error('Netzwerkantwort war nicht ok');
    }
    const data = await dataresponse.json();
    updateContentHowlong(data);
  } catch (error) {
     console.error('Fehler beim Laden der JSON-Daten: ', error);
     }
  }

 function updateContentHowlong(data) {
    const contentDiv = document.getElementById('howlong');
    if (data['closetime'] != null) {
      json = ' until ' +  data.closetime + ' o\'clock ';
  };
  contentDiv.innerHTML = `${json}`; 
  };

  loadDataStatus();
  setInterval(loadDataStatus, 10000);
  loadDataHowlong();
  setInterval(loadDataHowlong, 10000);

</script>

<div id="termine">Lade Daten...
  <noscript><div id="spacestatus" style="font-size:100%;">
    <span style="color:#f2f2f2; background-color:#f0ad4e; padding:3px 5px 3px 5px; border-radius:4px;display:inline-block;">Your browser does not support JavaScript!</span>
    </div>
  </noscript>
</div>

Unsere Termine gibt es auch hier als [iCal](https://kalender.eigenbaukombinat.de/public/public.ics)

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
    for(var i = 0; i < 3; i++){
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
