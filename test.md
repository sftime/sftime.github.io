---
layout: test
---

<div id="external_visualization"></div>
<div id="loading">loading...</div>

<script type="text/javascript">
  // load data via an ajax request. When the data is in, load the timeline
  $.ajax({
    url: '/static/data/data.json',
    success: function (data) {
      // hide the "loading..." message
      document.getElementById('loading').style.display = 'none';

      // DOM element where the Timeline will be attached
      var container = document.getElementById('external_visualization');

      // Create a DataSet (allows two way data-binding)
      var items = new vis.DataSet(data);

      // Configuration for the Timeline
      var options = {};

      // Create a Timeline
      var timeline = new vis.Timeline(container, items, options);
    },
    error: function (err) {
      console.log('Error', err);
      if (err.status === 0) {
        alert('Failed to load data/basic.json.\nPlease run this example on a server.');
      }
      else {
        alert('Failed to load data/basic.json.');
      }
    }
  });
</script>
