---
title: Termine
subtitle: Aktuelle Termine
comments: false
---

<termin></termin>

<script type="text/javascript">
jQuery('<div id="termin" style="font-size:70%;"></div>').insertBefore(jQuery('termin').first())
jQuery.get('https://eigenbaukombinat.de/api/kalender', function(resp) {
var json = '';
for(var i = 0; i < 13; i++){
json = json + '<tr><td>' + resp[i].startdate + '</td><td>' + resp[i].starttime + '</td><td> - </td><td>' +  resp[i].enddate + '</td><td>' + resp[i].endtime + '</td><td>' +  resp[i].summary + '</td></tr>'

  };
  jQuery('#termin').html('<span style="color:white; padding:3px 5px 3px 5px; border-radius:4px; display:inline-block;"><span id="termin"><table cellspacing="0" cellpadding="0" border="0">' + json + '</table></span></span>');
});
</script>

