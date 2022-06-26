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
              <button @click="item.status ? addCart(item) : removeCart(item)"
                :class="{ 'btn btn-warning btn-rounded': item.status, 'btn btn-outline-warning btn-rounded' : !item.status}">
                {{ item.status ? 'Add to Cart' : 'Remove from Cart'}}
              </button>
            </div>

          </div>
        </div>
      </div>
    </div>

    <div class="container py-5">
      <div class="row text-center text-black mb-5">
        <div class="col-lg-7 mx-auto">
          <h1 class="display-4">Cart List</h1>
        </div>
      </div>
      <div class="row">
        <div v-for="cart in cartList" :key="cart" class="col-lg-8 mx-auto py-2">
          <ul class="list-group shadow">
            <li class="list-group-item">
              <div class="media align-items-lg-center d-flex align-items-center justify-content-between p-3">

                <div class="media-body">
                  <h5 class="mt-0 font-weight-bold mb-2">{{ cart.product }}</h5>
                  <p class="font-italic mb-0 small">Kategori {{ cart.catagory }}</p>
                  <div class="d-flex align-items-center justify-content-between mt-1">
                    <h6 class="font-weight-bold my-2">Rp. {{cart.price}}</h6>
                  </div>
                </div>

                <img :src="cart.image" alt="" width="200" class="ml-lg-5 order-1 order-lg-2">

              </div>
            </li>
          </ul>
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
      count: 0,
      cartList: []
    }
  },
  methods: {
    increment() {
      this.count += 1
    },
    decrement() {
      this.count -= 1
    },
    addCart(cart) {
      cart.status = !cart.status
      this.cartList.push(cart)
    },
    removeCart(cart) {
      cart.status = true

      for (let index = 0; index < this.cartList.length; index++) {
        if (this.cartList[index].status) {
          this.cartList.splice(index, 1);
        }
      }



      // this.cartList.pop(cart)
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
