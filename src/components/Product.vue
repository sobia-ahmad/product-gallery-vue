<template>
  <div class="product">
    <div :class=" 'product-inner ' + product.color">
      <div class="product-info-wrapper">
        <h2 class="bg-info">{{ product.bgtext }}</h2>
      </div>
      <div class="product-photo-wrapper">
        <img :src="product.src" class="photo" />
      </div>
      <div class="product-description">
        <h2>{{ product.title }}</h2>
        <p>"1966 Brothers Paul Van Doren and Jim Van Doren along with partners Gordon Lee and Serge Delia open The Van Doren Rubber Company, Anaheim, Calif., for business on March 16. Vans #44 deck shoes, now known as the Authentic, are born."</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "product",
  props: ["product"],
};
</script>

<style>
.product {
  width: 100%;
  flex: 1 1 33.333%;
  padding: 25px;
}

.product-inner {
  position: relative;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.73);
  padding: 25px;
}

.product-inner.blue {
  background-image: linear-gradient(to bottom left, #24b1d4, #1aa5cf);
}

.product-inner.purple {
  background-image: linear-gradient(to bottom right, #c97eec, #93419b 70%);
}

.product-inner.green {
  background-image: linear-gradient(to bottom right, #c01e1e, #eb488c 70%);
}

.product-info-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  overflow: hidden;
}

.product-info-wrapper h2 {
  color: #313131;
  font-size: 155px;
  font-weight: 900;
  opacity: 0.2;
  transform-origin: center;
}

.product-photo-wrapper {
  z-index: 1;
  position: relative;
  transform-origin: center;
}

.product-photo-wrapper .photo {
  filter: drop-shadow(0px 0px 0px 12px rgba(0, 0, 0, 0.73));
  width: 100%;
}

.product-description {
  margin: 0px -25px -25px;
  padding: 25px;
  background-color: rgb(248, 244, 244);
}

.product-description h2 {
  color: rgb(121, 116, 116);
  text-align: center;
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 15px;
}

.product-description p {
  color: rgb(114, 101, 101);
  line-height: 1.5;
  font-size: 15px;
  font-weight: 300;
}
</style>