<template>
  <div class="restaurant-row">
    <h2 class="title">
        <span>Nos restaurants</span>
    </h2>
    <div class="wrapper-card">
        <RestaurantCard v-for="(card,index) in three_restaurant" :info-restaurants="card" :key="index"/>
    </div>
    
  </div>
</template>

<script>
import RestaurantCard from './RestaurantCard.vue';

export default {
    name: "RestaurantRow",
    components: {
        RestaurantCard,
    },
    props: {
    three_restaurant: Array
    },

}
</script>

<style lang="scss">
.restaurant-row {
    .wrapper-card {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 20px;}

    .title {
        font-size: 3rem;
        font-weight: 700;
        color: #000;
        margin: 10px;
    }
}

</style>