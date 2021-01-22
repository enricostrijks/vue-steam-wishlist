<template>
  <div class="home">
    <img alt="Steam logo" class="steamlogo" src="../assets/logo.png" />
    <Header />
    <form @submit.prevent="addNewWishlistItem">
      <label>Voer naam nieuw wishlist item in</label>
      <input v-model="newWishlistItem" name="newWishlistItem" />
      <button>Voeg nieuw wishlist item toe</button>
    </form>
    <SteamWishlist
      v-bind:wishlist="wishlist"
      v-on:delitem="removeWishlistItem"
    />
  </div>
</template>

<script>
import Header from "../components/layout/Header";
import SteamWishlist from "../components/SteamWishlist";
import { ref } from "vue";
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    Header,
    SteamWishlist,
  },
  // data() {
  //   return {
  //     wishlist: [
  //       {
  //         id: 1,
  //         title: "Contraband Simulator",
  //         purchased: false,
  //       },
  //       {
  //         id: 2,
  //         title: "Car Trader Simulator",
  //         purchased: true,
  //       },
  //       {
  //         id: 3,
  //         title: "Grand Theft Auto V",
  //         purchased: false,
  //       },
  //     ],
  //   };
  // },
  setup() {
    const newWishlistItem = ref("");
    const wishlist = ref([
      {
        title: "Contraband Simulator",
        purchased: false,
      },
      {
        title: "Car Trader Simulator",
        purchased: true,
      },
      {
        title: "Grand Theft Auto V",
        purchased: false,
      },
    ]);

    function addNewWishlistItem() {
      wishlist.value.push({
        id: Date.now(),
        purchased: false,
        title: newWishlistItem.value,
      });
      newWishlistItem.value = "";
    }

    function removeWishlistItem(index) {
      wishlist.value.splice(index, 1);
    }

    return {
      wishlist,
      newWishlistItem,
      addNewWishlistItem,
      removeWishlistItem,
    };
  },
};
</script>

<style scoped>
.steamlogo {
  max-width: 200px;
}
</style>
