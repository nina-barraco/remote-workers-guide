<template>
  <section v-if="profile">

  <header>
    <div class=headerImage v-bind:style="{ backgroundImage: profile.image }">
      <b-container>
        <h1>{{ profile.name }}</h1>
      </b-container>
    </div>

  </header>

    <b-container>

      <div class="stars"></div>

      <p class="business-description">{{ profile.description }}</p>

      <hr>

      <div class="ratings">
        <h3>wifi: {{ profile.wifi }}</h3>
        <h3>seating: {{ profile.seating }}</h3>
        <h3>food and beverage: {{ profile.foodBeverage }}</h3>
      </div>

      <hr>

      <!-- manny code on review form -->
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
        <li v-for="value in object">
          {{ name }} says {{ message }}
        </li>
      </ul>

      <hr>

      <b-row align-h="center">
        <b-col xl="8" md="9">
          <b-form @submit.prevent="onSubmit" @reset="onReset" v-if="show">
            <b-form-group id="name">
              <b-form-input id="name1"
                            type="text"
                            v-model="form.name"
                            required
                            placeholder="First name and last initial">
              </b-form-input>
            </b-form-group>
            <b-form-group id="review">
              <b-form-textarea id="message"
                     v-model="form.message"
                     required
                     placeholder="Write review here"
                     :rows="5"
                     :max-rows="10">
              </b-form-textarea> 
            </b-form-group>           
            <b-button type="submit" variant="secondary">Submit</b-button>
          </b-form>
        </b-col>
      </b-row>

   </b-container>
  </section>
</template>


<script>

import profiles from "~/static/profiles.json";

export default {
  data() {
    return {
      profile: null,
      // name: '',
      // message: '',
      reviews: [],
      form: {
        name: '',
        message: ''
      },
      show: true
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
  // methods: {
  //   submitReview () {
  //     evt.preventDefault();
  //     alert(JSON.stringify(this.form));
  //     console.log(this.name);
  //     console.log(this.message);
  //     this.reviews.push({
  //       name: this.name,
  //       message: this.message
  //     });
  //   },
  //   nameChanged() {
  //     console.log(this.name)
  //   }
  // },
//   methods: {
//     onSubmit (evt) {
//       //what does evt.preventDefault() do? Couldn't find anything good on it.
//       evt.preventDefault();
//       alert(JSON.stringify(this.form));
//     },
//     onReset (evt) {
//       evt.preventDefault();
//       /* Reset our form values */
//       this.form.name = '';
//       this.form.message = '';
//       /* Trick to reset/clear native browser form validation state */
//       this.show = false;
//       this.$nextTick(() => { this.show = true });
//     }
//   }
// }
  methods: {
    onSubmit (evt) {
      //what does evt.preventDefault() do? Couldn't find anything good on it.
      //evt.preventDefault();
      alert(JSON.stringify(this.form));
      this.reviews.push({
        name: this.form.name,
        message: this.form.message
      });
    },
    onReset (evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.name = '';
      this.form.message = '';
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => { this.show = true });
    }
  }
}

//another attempt at making the images change
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

//nina code for review form
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

</script>


<style>

body {
  background-color: #F2F2F2;
}

h1 {
  font-family: 'Playfair Display', serif;
  font-weight: bolder;
  font-size: 4rem;
  color: white;
  text-align: center;
}

@media (max-width: 690px) {
  h1 {
    font-size: 3rem;
  } 
}

/* .jumbotron {
  position: relative;
}
.jumbotron .container {
  height: 100%;
}
.jumbotron-inner {
  height: 100%;
  width: 100%;
  background-image: linear-gradient( rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2));
  background-size: cover;
  background-position: center;
  position: absolute;
  top: 0;
  left: 0;
} */

.headerImage {
  height: 50vh;
  width: 100%;
  background-image: linear-gradient(rgba(0, 0, 0, 1), rgba(0, 0, 0, 1));
  background-size: cover;
  background-position: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin-bottom: 5%;
}

.business-description {
  font-family: 'DIN 2014', sans-serif;
  font-size: 6vh;
  color: #ACACAC;
}

@media (max-width: 690px) {
  .business-description {
    font-size: 5vh;
  } 
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