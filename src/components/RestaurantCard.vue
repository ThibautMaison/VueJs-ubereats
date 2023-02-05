<template>
  <div class="restaurant-card">
    <div :style="changeBackground" class="restaurant--image">

    </div>
    <div class="restaurant--imformations">
        <div class="top">
            <p class="name">
                <span>{{ infoRestaurants.name }}</span>
            </p>
            <p class="note">
                <span>{{ infoRestaurants.note }}</span>
            </p>
        </div>
        <p class="time">
          {{ infoRestaurants.drive_time }}
        </p>
    </div>
    <p>test</p>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  name: "RestaurantCard",
  props: {
    infoRestaurants: Object,
  },
  setup(props) {
    const changeBackground = computed(() => {
      return {
      backgroundImage: `url(${props.infoRestaurants.image})`,
      };
    });
    return {
      changeBackground,
    };
  },
}
</script>

<style lang="scss">
.restaurant-card {
  width: 32%;
  height: 30vh;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;

  p{
    margin: 0px;
  }
  .restaurant--image {
    background-image: url("https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==");
        height: 70%;
        background-size: cover;
        background-position: center;
        
  }
  .restaurant--imformations {
    height: 30%;
    padding: 10px ;
    .top {
      display: flex;
      justify-content: space-between;
      margin: 5px 0px;
      .name {
        font-size: 1.2rem;
        font-weight: 700;
        color: #000;
      }
      .note {
        background-color: #eeeeee;
        height: 30px;
        width: 30px;
        font-size: 0.8rem;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: 700;
        color: #000;
        border-radius: 50%;
      }
    }
    .time {
      font-size: 1rem;
      font-weight: 400;
      color: #000;
    }
  }
}



</style>