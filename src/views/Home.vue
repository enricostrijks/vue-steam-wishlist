<template>
  <div class="home">
    <img alt="Steam logo" class="steamlogo" src="../assets/logo.png" />
    <SteamWishlist v-bind:wishlist="wishlist" />
  </div>
</template>

<script>
import SteamWishlist from "../components/SteamWishlist";
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    SteamWishlist,
  },
  data() {
    return {
      wishlist: [
        {
          id: 1,
          title: "Contraband Simulator",
          purchased: false,
        },
        {
          id: 2,
          title: "Car Trader Simulator",
          purchased: true,
        },
        {
          id: 3,
          title: "Grand Theft Auto V",
          purchased: false,
        },
      ],
    };
  },
};
</script>

<style scoped>
.steamlogo {
  max-width: 200px;
}
</style>
