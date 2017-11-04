# Global
Satellite
Hello world
Animation
Custom map tiles
TileJSON
Overlays
Two layers
Markers
Polygon
Globe
2D next to 3D
Opposite Side of the World
Advanced API demo
Download & offline demo

Project page & API reference

 WebGLEarth logo Animation
Leaflet compatible API (replace "L." with "WE.")View example on a separate page
Rotate your globe with a simple animation.

Copy Source code
<!DOCTYPE HTML>
<html>
  <head>
    <script src="http://www.webglearth.com/v2/api.js"></script>
    <script>
      var earth;
      function initialize() {
        earth = new WE.map('earth_div');
        earth.setView([46.8011, 8.2266], 3);
        WE.tileLayer('http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{
          attribution: '© OpenStreetMap contributors'
        }).addTo(earth);

        // Start a simple rotation animation
        var before = null;
        requestAnimationFrame(function animate(now) {
            var c = earth.getPosition();
            var elapsed = before? now - before: 0;
            before = now;
            earth.setCenter([c[0], c[1] + 0.1*(elapsed/30)]);
            requestAnimationFrame(animate);
        });
      }
    </script>
    <style>
      html, body{padding: 0; margin: 0;}
      #earth_div{ top: 0; right: 0; bottom: 0; left: 0; position: absolute !important;}
    </style>   
    <title>WebGL Earth API v2: Animation</title>
  </head>
  <body onload="initialize()">
    <div id="earth_div"></div>
  </body>
</html>
