<template>
  <div>
    <nuxt/>
  </div>
</template>

<style>

body {
  background-color: #F2F2F2;
}

button {
  font-family: 'DIN 2014', sans-serif;
}

form {
  font-family: 'DIN 2014', sans-serif;
}

/* * *,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
} */

</style>

// import profiles from "~/assets/profiles.json";

// export default {
//   layout: 'profiles',
//   data: {
//     id: 0,
//     profile: {}
//   },
//   created() {
    
//     console.log(profiles)
//     let currentProfile = profiles.find(profile => profile.id === this.$route.params.id);
//     console.log(currentProfile)
//     if(!currentProfile) {
//       //this profile doesn't exist
//     } else {
//       this.profile = currentProfile;
//     }
//     this.id = this.$route.params.id;
//   }
// }
