<template>
  <div>
    <div class="jumbotron"></div>

    <div class="container">

      <div class="stars"></div>

      <p class="business-description"></p>

      <hr>

      <div class="ratings">
        <h3>wifi</h3>
        <h3>seating</h3>
        <h3>food and beverage</h3>
      </div>

      <hr>

      <div class="reviews"></div>
      <h1 class="body-header">
        reviews
      </h1>

      <hr>

      <div class="row d-flex justify-content-center submit-review">
        <div class="col-8">
          <h1 class="body-header">submit a review</h1>
          <form class="location-form">
            <div class="form-group">
              <input type="name" class="form-control" id="name" placeholder="First name and last initial">
            </div>
            <div class="form-group">
              <textarea class="business-review form-control" id="business-review" placeholder="Write review here" rows="3"></textarea>
            </div>
            <button type="submit" class="btn btn-secondary">Submit</button>
          </form>
        </div>
      </div>

    </div>

    <nuxt/>
  </div>
</template>

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

.jumbotron {
  
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

/* * *,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
} */

</style>
