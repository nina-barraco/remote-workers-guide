<template>
  <section class="container" v-if="profile">
    {{profile.name}}
  </section>
</template>

<script>
import profiles from "~/assets/profiles.json";

export default {
  layout: 'profiles',
  data: {
    id: 0,
    profile: {}
  },
  created() {
    
    console.log(profiles)
    let currentProfile = profiles.find(profile => profile.id === this.$route.params.id);
    console.log(currentProfile)
    if(!currentProfile) {
      //this profile doesn't exist
    } else {
      this.profile = currentProfile;
    }
    this.id = this.$route.params.id;
  }
}
</script>

<style>

</style>
