<template>
  <div class="home-page">
    <div class="header">
        <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="">
        <input type="text" placeholder="De quoi avez vous envie ? ">
    </div>
    <div class="banniere">

    </div>
    <RestaurantRow v-for="(data, i) in data_restaurant" :key="i" :three_restaurant="data" />
  </div>
</template>

<script>
// IMPORT
import BDD from "../BDD.js";
import { onMounted, ref } from "vue";

// COMPONENTS
import RestaurantRow from "../components/RestaurantRow.vue";
export default {
  name: "HomePage",
  components: {
    RestaurantRow,
  },
  setup() {
    class Restaurant {
      constructor(name, note, drive_time, image) {
        this.name = name;
        this.note = note;
        this.drive_time = drive_time;
        this.image = image;
      }
    }
    let data_restaurant = ref([]);
    const makeDataRestaurant = () => {
      let three_restaurant = [];
      for (const restaurant of BDD) {
        const newRestaurant = new Restaurant(
          restaurant.name,
          restaurant.note,
          restaurant.drive_time,
          restaurant.image
        );
        if (three_restaurant.length == 2) {
          three_restaurant.push(newRestaurant);
          data_restaurant.value.push(three_restaurant);
          three_restaurant = [];
        } else {
          three_restaurant.push(newRestaurant);
        }
      }
    };
    onMounted(makeDataRestaurant);
    //return
    return {
      data_restaurant,
    };
  },
};
</script>

<style lang="scss">
.home-page {
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 120px;
    width: 100%;
    img {
      width: 200px;
    }
    input {
      width: 30%;
      height: 40px;
      border: none;
      border-radius: 10px;
      padding: 0px 20px;
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      background-color: #f2f2f2;
      outline: none;
    }
  }
    .banniere {
        height: 200px;
        width: 100%;
        background-image: url(https://www.wearehullcity.co.uk/siteassets/general-hull-city-images/uber-eats.jpg/Large);
        background-size: cover;
        background-position: center;
    }
}

</style>