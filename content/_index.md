#  
<space></space>


<script type="text/javascript">
jQuery('<div id="spacestatus" style="font-size:100%;"></div><div style="font-size: 100%; margin-top: 0.5ex; margin-bottom: 2.5ex;" id="spacestatus_sm"></div>').insertBefore(jQuery('space').first())
jQuery.get('https://eigenbaukombinat.de/status/status.json?' + jQuery.now(), function(resp) {

if (resp['state']['open']) {
   jQuery('#spacestatus').html('<span style="color:white; background-color:#5cb85c; padding:3px 5px 3px 5px; border-radius:4px; display:inline-block;">Das Eigenbaukombinat ist <span id="howlong"></span> offen,   <a href="/anpassung-der-verhaltensregeln/">Anmelde-, Verhaltens- und Hygieneregeln beachten</a>!</span>');

jQuery.get('https://eigenbaukombinat.de/status/openuntil.json?' + jQuery.now(), function(resp) {
  if (resp['closetime'] != null) {
      jQuery('#howlong').html(' bis mindestens '+ 
resp['closetime'] +' Uhr ');
  }
 });
 } else {
    jQuery('#spacestatus').html('<span style="color:white; background-color:#f0ad4e; padding:3px 5px 3px 5px; border-radius:4px;display:inline-block;">Das Eigenbaukombinat ist gerade geschlossen.</span>');
};
});
</script>
