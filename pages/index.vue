<template>
  <section class="container">
    <header>
      <h2>remote worker's</h2>
      <h1>guide to detroit</h1>
    </header>

    <div class="row d-flex justify-content-center">
      <div class="searchBar">
        <input class="form-control form-control-lg" type="text" placeholder="Search for a location">
      </div>
    </div>

    <div id="map"></div>

    <hr>

    <div class="row d-flex justify-content-center">
      <p class="col-9 landing-description">
        Here to help remote workers locate great spaces to work around the city of Detroit.
      </p>
    </div>

    <hr>

    <div class="row d-flex justify-content-center submit-location">
      <h1 class="body-header">submit a location</h1>
      <form class="col-8 location-form">
      <div class="form-group">
        <input type="name" class="form-control form-control-lg" id="establishment-name" placeholder="Name of establishment">
      </div>
      <button type="submit" class="btn btn-secondary">Submit</button>
    </form>
    </div>
  

  </section>
</template>

<script>

export default {
  head () {
    return {
      script: [
        { src: 'https://unpkg.com/leaflet@1.3.4/dist/leaflet.js' }
      ],
      link: [
        { rel: 'stylesheet', href: 'https://unpkg.com/leaflet@1.3.4/dist/leaflet.css' }
      ]
    }
  },
  
  mounted() {
    var that = this;
    let x = setInterval(() => {
      if(!L)
        return;
      that.initMap()
      window.clearInterval(x);
    }, 1000)
  },
  methods: {
    initMap() {
      var mymap = L.map('map').setView([42.3314, -83.0458], 13);
      L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoibmluYS1iYXJyYWNvIiwiYSI6ImNqb3owNXQ4bDA0NTQzcHA5ajRheWc5OGcifQ.Y1hDymb8BI2Jf9cc8zrx7A', {
          attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
          maxZoom: 18,
          id: 'mapbox.streets',
          accessToken: 'your.mapbox.access.token'
      }).addTo(mymap);
    }
  }
}
</script>

<style>

header {
  padding: 8%;
}

h2 {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  font-size: 2rem;
  color: #707070;
  text-align: center;
}

h1 {
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  font-size: 3rem;
  color: rgb(255, 122, 122);
  text-align: center;
}

.searchBar {
  width: 60%;
  font-family: 'DIN 2014', sans-serif;
}

#map {
  height: 35rem;
  width: 100%;
  border: 1px solid darkslategrey;
  margin-top: 5%;
  margin-bottom: 6%;

}

hr {
  margin-top: 8%;
  margin-bottom: 8%;
}

.landing-description {
  font-family: 'DIN 2014', sans-serif;
  color: #ACACAC;
  font-size: 2.7rem;
  text-align: center;
}

.body-header {
  color: #707070;
  padding-bottom: 8%;
}

.submit-location {
  width: 100%;
  margin-bottom: 20%;
}

</style>
