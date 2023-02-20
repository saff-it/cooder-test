<template>
  <div class="col-12 col-md-6 ms_product-card" @click="active = false" @mouseleave="active = true">

    <div class="ms_product-img" v-show="active === true" >
      <img :src="productDetail.image" :alt="productDetail.title">
    </div>

    <div class="ms_product-info" v-show="active === false">
      <h4>{{productDetail.title}}</h4>
      <p>{{productDetail.description}}</p>
      <span class="ms_rating-tag">Rating: {{productDetail.rating.rate}}/5</span>
      <span class="ms_price-tag">Price: € {{productDetail.price}}</span>
    </div>


  </div>
</template>

<script>
export default {

  data: function () {
    return {
      active: true,

    }
  },

  props: {
    productDetail: Object,
  }

}
</script>

<style lang="scss">

.ms_product-card div.ms_product-img{
  height: 500px;
  transition: all 1.5s;
  

  img {
    height: 100%;
    width: 100%;
    object-fit: contain;
    
  }

  &:hover{
    transform: scale(1.1);
  }
}

.ms_product-info{
  border-style: dashed;
  border-color: black;
  border-radius: 20px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  h4{
    font-size: 2rem;
    width: 75%;
    margin: 25px 25px;
    text-align: center;
  }

  p{
    font-size: 0.8rem;
    width: 70%;
    margin: 25px 25px;
    text-align: justify;
    color: #6f6f6f;
  }

  span.ms_price-tag{
    margin: 25px 25px;
    display: block;
    background-color: black;
    color: white;
    border-radius: 20px;
    padding: 4px 10px;
    font-size: 0.9rem;
    width: 20%;
    text-align: center;
  }

  span.ms_rating-tag{
    margin: 0 25px;
  }
}
</style>