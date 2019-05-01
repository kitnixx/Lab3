<!DOCTYPE html>
<html lang="en">
<head>
    <title>Pure Water Brew</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="please add">
    <!-- CSS Base -->
    <link rel="stylesheet" type='text/css' media='all' href="css/webslides.css">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.4.0/dist/leaflet.css"/>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.css"/>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/c3/0.6.14/c3.min.css" rel="stylesheet">
    <link rel="stylesheet" type="text/css" media="all" href="css/style.css">
    <!-- Javascript Library -->
    <script src="https://unpkg.com/leaflet@1.4.0/dist/leaflet.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>
    <script src="js/webslides.min.js"></script>
    <script src="https://unpkg.com/d3@5/dist/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/c3/0.6.14/c3.min.js"></script>
</head>
<body>
<main role="main">
    <article id="webslides">
      <!-- the landing scene -->
        <section class="bg-white">
            <video class="background-video dark" autoplay muted loop>
                <source src="assets/view.mp4" type="video/mp4">
            </video>
            <div class="wrap aligncenter">
                <h1>
                    <strong>Story Map Title</strong>
                </h1>
            </div>
        </section>

        <section class="bg-apple slide-top">
            <div id="mymap"></div>
        </section>

       <!-- the second map -->
       <section class="bg-apple slide-top">
           <div id="mymap2"></div>
       </section>

    </article>
</main>
<script>

    
    var map = L.map("mymap", {zoomControl: false, scrollWheelZoom: false}).setView([1.290270, 103.851959], 8);

    var map2 = L.map("mymap2", {zoomControl: false, scrollWheelZoom: false}).fitBounds([
        [49.3, -138.5],
        [22.8, -67.4]
    ]);

    L.tileLayer('https://cartodb-basemaps-{s}.global.ssl.fastly.net/light_all/{z}/{x}/{y}@2x.png', {
        maxZoom: 19
    }).addTo(map);

    L.tileLayer('https://cartodb-basemaps-{s}.global.ssl.fastly.net/dark_all/{z}/{x}/{y}@2x.png', {
        maxZoom: 19
    }).addTo(map2);


    ws = new WebSlides();
    ws.el.addEventListener('ws:slide-change', function () {

      crtDiv = $(".current div");
      //Map 1 'flyto' animation location and function
      if (crtDiv.attr("id") === "mymap") {
          map.invalidateSize();
          //starting location latitude and longitude
          map.setView([1.290270, 103.851959], 9);
          //Fly to animation  new latitude and longitude
          map.flyTo([45.514685, -122.987080], 10, {animate: true, duration: 23});
          //outline of Washington county
      }

})

</script>
</body>
</html>
