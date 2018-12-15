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
import profiles from "~/static/profiles.json";

export default {
  head () {
    return {
      script: [
        { src: 'https://unpkg.com/leaflet@1.3.4/dist/leaflet.js' }
      ],
      link: [
        { rel: 'stylesheet', href: 'https://unpkg.com/leaflet@1.3.4/dist/leaflet.css' }
      ],
      search: '',
      // postList : [
      //   profile.name
      // ],
      profile: null,
      reviews: [],
      form: {
        name: '',
        message: ''
      },
      show: true
    }
  },
  mounted() {
    
    console.log(this.$route.params.name)
    let currentProfile = profiles.find(profile => profile.slug === this.$route.params.name);
    console.log(currentProfile)
    if(currentProfile) {
      this.profile = currentProfile;
    } else {
      alert("This page does not exist.");
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
      var bottomLine = L.marker([42.3514, -83.0692]).addTo(mymap);
      bottomLine.bindPopup("<img src='~/static/The_Bottom_Line.0.0.jpeg'><a href='profile/the-bottom-line'>The Bottom Line</a><br>Neighborhood coffeehouse with open-mike nights serving espresso drinks, tea & pastries in cozy digs.");
      var redHook = L.marker([42.3552, -82.9971]).addTo(mymap);
      redHook.bindPopup("<a href='profile/the-red-hook'>The Red Hook</a><br>Hot java drinks & desserts in airy, bright surrounds featuring wooden banquettes & white walls.");
      var cafe1923 = L.marker([42.3919, -83.0601]).addTo(mymap);
      cafe1923.bindPopup("<a href='profile/cafe-1923'>Cafe 1923</a><br>Hip, bustling spot for coffee, desserts & sandwiches featuring bookcases & vintage oak shelving.");
      var astroCoffee = L.marker([42.3316, -83.0757]).addTo(mymap);
      astroCoffee.bindPopup("<a href='profile/astro-coffee'>Astro Coffee</a><br>Small, cozy cafe serving a variety of coffee & tea plus locally sourced baked goods & sandwiches.");
      var greatLakes = L.marker([42.3503, -83.0602]).addTo(mymap);
      greatLakes.bindPopup("<a href='profile/great-lakes-coffee'>Great Lakes Coffee Roasting Company</a><br>Cafe furnished with reclaimed wood & exposed ducts serving micro-roasted coffees, beer & snacks.");
      var socraTea = L.marker([42.3545, -83.0613]).addTo(mymap);
      socraTea.bindPopup("<a href='profile/socra-tea'>Socra Tea</a><br>Trendy & cozy hidden in the back walking area off the busy streets. Specialty teas & deserts, including gluten free!");
      var dessertOasis = L.marker([42.3330, -83.0490]).addTo(mymap);
      dessertOasis.bindPopup("<a href='profile/dessert-oasis'>Dessert Oasis Coffee Roasters</a><br>Comfortable coffee shop downtown with a small selection of food.");
      var avalon = L.marker([42.3329, -83.0480]).addTo(mymap);
      avalon.bindPopup("<a href='profile/avalon'>Avalon Café and Bakery</a><br>Casual counter serve for salads, sandwiches & organic, housemade pastries & fresh breads.");
      var DIA = L.marker([42.3591, -83.0645]).addTo(mymap);
      DIA.bindPopup("<a href='profile/DIA'>DIA Kresge Court</a><br>Atrium cafe at the Detroit Institute of Arts offering sandwiches, salads, pastries & coffee.");
      var bikesCoffee = L.marker([42.3529, -83.0798]).addTo(mymap);
      bikesCoffee.bindPopup("<a href='profile/bikes-and-coffee'>The Bottom Line</a><br>Small neighborhood coffee shop also offering bike repair services.");
    }
  },

  // for (let i = 0; i =< profiles.length; i++) {
  //     display profile.marker;
  // }

computed: {
    filteredList() {
      return this.postList.filter(post => {
        return profile.name.toLowerCase().includes(this.search.toLowerCase())
      })
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
  border: 1px solid rgb(255, 122, 122);
  margin-top: 5%;
  margin-bottom: 5%;
}

.landing-description {
  font-family: 'DIN 2014', sans-serif;
  font-weight: 300;
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
