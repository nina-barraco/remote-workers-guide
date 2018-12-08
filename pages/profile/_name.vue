<template>
  <section v-if="profile">

    <!-- <div class="image">
      <img v-bind:src="profile.image">
    </div> -->

  <b-jumbotron fluid class="jumbotron" v-bind:src="profile.image">
    <img v-bind:src="profile.image" />
    <template slot="header" class="jumbotronHeader">
      {{ profile.image }}
      {{ profile.name }}
    </template>
    <template slot="lead">
      {{ profile.rating }}
    </template>
  </b-jumbotron>

  <!-- <div class="jumbotron" v-bind:src="profile.image">
    <h1 class="display-4 jumbotronHeader"> {{ profile.name }}</h1>
    <p class="lead"> {{ profile.rating }}</p>
  </div> -->

  <!-- <div :style="{'background-image': `url(${require('getImageUrl')})`}" style="width: 100%; height: 100px;">
  </div> -->

    <div class="container" >

      <div class="stars"></div>

      <p class="business-description">{{ profile.description }}</p>

      <hr>

      <div class="ratings">
        <h3>wifi: {{ profile.wifi }}</h3>
        <h3>seating: {{ profile.seating }}</h3>
        <h3>food and beverage: {{ profile.foodBeverage }}</h3>
      </div>

      <hr>

      <!-- <div class="reviews"></div>
      <h1 class="body-header">
        reviews
      </h1>
      <ul>
        <li v-for="(review,ndx) in reviews" :key="ndx">
          {{review.name}} says {{review.message}}
        </li>
      </ul>
      <hr>
      <div class="row d-flex justify-content-center submit-review">
        <div class="col-8">
          <h1 class="body-header">submit a review</h1>
          <form class="location-form">
            <div class="form-group">
              <input type="name" v-model="name" class="form-control" id="name" placeholder="First name and last initial">
            </div>
            <div class="form-group">
              <textarea class="business-review form-control" v-model="message" id="business-review" placeholder="Write review here" rows="3"></textarea>
            </div>
            <button type="submit" @click.prevent="submitReview" class="btn btn-secondary">Submit</button>
          </form>
        </div>
      </div> -->

      <div class="reviews"></div>
      <h1 class="body-header">
        reviews
      </h1>
      <ul>
        <li>
          {{ reviews.name }}
        </li>
      </ul>
      <hr>
      <div class="row d-flex justify-content-center submit-review">
        <div class="col-8">
          <h1 class="body-header">submit a review</h1>
          <form class="location-form">
            <div class="form-group">
              <input type="name" class="form-control" id="name" v-model="name" placeholder="First name and last initial">
            </div>
            <div class="form-group">
              <textarea class="business-review form-control" id="business-review" v-model="message" placeholder="Write review here" rows="3"></textarea>
            </div>
            <button type="submit" @click.prevent="submitReview" class="btn btn-secondary">Submit</button>
          </form>
        </div>
      </div>

    </div>
  </section>
</template>


<script>

import profiles from "~/assets/profiles.json";

export default {
  data() {
    return {
      profile: null,
      name: '',
      message: '',
      reviews: [],
      // uploadImage: {
      //   background: 'red'
      // }
    }
  },
  mounted() {
    
    console.log(this.$route.params.name)
    let currentProfile = profiles.find(profile => profile.slug === this.$route.params.name);
    console.log(currentProfile)
    if(!currentProfile) {
      //this profile doesn't exist
    } else {
      this.profile = currentProfile; 
      //this.profiles = profiles;
    }
  },
  methods: {
    submitReview () {
      console.log(this.name);
      console.log(this.message);
      // this.reviews.push(
      //   name: this.name
      // );
    }
  },
}

//store info in reviews

  // methods: {
  //   uploadImage () {
  //     console.log(this.profile.image)
  //     this.profile.image
  //   }
  // }


  // methods: {
  //   increaseWifi() {
  //     console.log(this.profile.wifi)
  //     this.profile.wifi = this.profile.wifi + 1;
  //   },

//   methods: {
//     submitReview() {
//       console.log(this.name);
//       console.log(this.message);
//       this.reviews.push({
//         name: this.name,
//         message: this.message
//       })
//     },
//     nameChanged() {
//       console.log(this.name)
//     }
//   }
// }

// when you submit a review, it will display in the reviews section with your name.

// when submit button is clicked, display info in reviews. 



// Nina
// import profiles from "~/assets/profiles.json";

// var request = require('request');
//import request from 'request'
// request('~/assets/profiles.json, function(error, response, body)') {
//   if(!error && response.StatusCode == 200) {
//     var parsedData = JSON.parse(body);
//     console.log("It worked!");
//   }
// }

// import axios from "axios";

// export default {
//   asyncData () {
//     return axios.get(`/api/profiles?name=this.$route.params.name`)
//     .then((res) => {
//       return { profiles: res.data.profiles }
//     })
//   }
// }


	// var ajax = new XMLHttpRequest();
	// ajax.onreadystatechange = function() {
	//     if (ajax.readyState == 4)
  //       {
  //           console.log(ajax.status, ajax.responseText)
  //           if(ajax.status==200) {
	// 			var result = JSON.parse(ajax.responseText);
  //           }
	// 	}
	// };
	// ajax.open("GET", "~assets/profiles.json");
	// ajax.send();

</script>


<style>

body {
  background-color: #F2F2F2;
}

h1 {
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  font-size: 3rem;
  color: rgb(255, 122, 122);
  text-align: center;
}

/* .jumbotron {
  background-image: url("~assets/The_Bottom_Line.0.0.jpeg");
} */

.jumbotronHeader {
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  font-size: 3vw;
  text-align: left;
}

.business-description {
  font-family: 'DIN 2014', sans-serif;
  font-size: 6vh;
  color: #ACACAC;
}

hr {
  border: 1px solid rgb(255, 122, 122);
}

h3 {
  font-family: 'DIN 2014', sans-serif;
  text-transform: uppercase;
  letter-spacing: .2rem;
  color: #ACACAC;
}

.body-header {
  color: #707070;
  padding-bottom: 8%;
}

.submit-review {
  width: 100%;
  margin-top: 5%;
  margin-bottom: 10%;
}

#business-review {
  width: 100%;
  height: 10rem;
}

</style>
