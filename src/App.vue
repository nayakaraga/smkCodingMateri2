<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">

  <div class="container-fluid">
    <div class="row">
      <div v-for="(item, index) in items" :key="index" class="col-lg-3 col-sm-6 col-sm-12 px-3">
        <div class="product-card">
          <div class="product-image">
            <img :src="item.image" alt="product-image">
          </div>
          <div class="product-details">
            <div class="product-catagory">{{ item.catagory }}</div>

            <h4><a href="#">{{ item.product }}</a></h4>

            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos sunt quidem iusto laborum delectus
              architecto, cum maiores unde consequuntur sed beatae expedita molestias quod corporis earum ipsa, fugit
              placeat
              maxime.</p>

            <div class="product-bottom-details">
              <div class="product-price">
                <small>Rp. {{ item.price }}</small>{{ item.discountPrice }}
              </div>
            </div>

            <div class="row">
              <button class="btn btn-danger btn-rounded" @click="item.qty--">Remove Qty</button>
              <p>{{ item.qty }}</p>
              <button class="btn btn-warning btn-rounded" @click="item.qty++">Add Qty</button>
            </div>

          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>

import products from "./static/product";

export default {
  name: 'App',
  data() {
    return {
      items: products.arrayProducts,
      count: 0
    }
  },
  methods: {
    increment() {
      this.count += 1
    },
    decrement() {
      this.count -= 1
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto+Condensed');

* {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Roboto', sans-serif;
}

.product-card {
  width: 380px;
  position: relative;
  box-shadow: 0 2px 7px#dfdfdf;
  margin: 30px auto;
  background: #fafafa;
  align-content: flex-end;
}

.product-image {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 300px;
  padding: 50px;
  background: #f0f0f0;
}

.product-image img {
  max-width: 100%;
  max-height: 100%;
}

.product-details {
  padding: 30px;
}

.product-catagory {
  display: block;
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  color: #ccc;
  margin-bottom: 18px;
}

.product-details h4 a {
  font-weight: 500;
  display: block;
  margin-bottom: 18px;
  text-transform: uppercase;
  color: #363636;
  text-decoration: none;
  transition: 0.3s;
}

.product-details h4 a:hover {
  color: #fbb72c;
}

.product-details p {
  font-size: 15px;
  line-height: 22px;
  margin-bottom: 1px;
  color: #999;
}

.product-bottom-details {
  overflow: hidden;
  border-top: 1px solid #eee;
  /* padding-top: 50%; */
}

.product-bottom-details div {
  float: left;
  width: 100%;
}

.product-price {
  font-size: 18px;
  color: #fbb72c;
  font-weight: 600;
  padding: 5px;
}

.product-price small {
  font-size: 80%;
  font-weight: 400;
  text-decoration: line-through;
  display: inline-block;
  margin-right: 5px;
}
</style>
