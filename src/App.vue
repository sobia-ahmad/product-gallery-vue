<template>
  <main id="app" @mousemove="mousemove">
    <section class="products">
      <Product v-for="product in products" :key="product.color" :product="product" />
    </section>
  </main>
</template>

<script>
import Product from "./components/Product";

export default {
  name: "app",
  components: {
    Product,
  },
  data() {
    return {
      products: [
        {
          title: "VANS - Burgundy",
          color: "blue",
          bgtext: "OFF VANS",
          src: require("./assets/vans-trainers-1.png"),
        },
        {
          title: "VANS - Funky Colours",
          color: "purple",
          bgtext: "THE VANS",
          src: require("./assets/vans-trainers-2.png"),
        },
        {
          title: "VANS - Black",
          color: "green",
          bgtext: "WALL VANS",
          src: require("./assets/vans-trainers-3.png"),
        },
      ],
    };
  },
  methods: {
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll(".products .product");

      for (let i = 0; i < products.length; i++) {
        let product = products[i];

        let product_photo = product.querySelector(".product-photo-wrapper");

        let photo_x = mouseX - this.coords(product_photo).x;
        let photo_y = mouseY - this.coords(product_photo).y;
        product_photo.style.transform = `translateY(-${
          photo_y / 20
        }px) translateX(-${photo_x / 20}px) translateZ(100px)`;

        let bginfo = product.querySelector(".bg-info");
        let bg_x = mouseX - this.coords(bginfo).x;
        let bg_y = mouseY - this.coords(bginfo).y;

        bginfo.style.transform = `translateX(${bg_x})px translateY(${bg_y})px`;
      }
    },
    coords(el) {
      let coords = el.getBoundingClientRect();

      return {
        x: coords.left / 2,
        y: coords.top / 2,
      };
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: "Open Sans Condensed", sans-serif;
}

main {
  background-color: rgb(243, 243, 243);
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  width: 100vw;
}

.products {
  max-width: 1280px;
  padding: 25px;
  margin: 0 auto;
  display: flex;
}
</style>