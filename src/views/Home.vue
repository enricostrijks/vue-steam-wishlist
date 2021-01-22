<template>
  <div class="home">
    <img alt="Steam logo" class="steamlogo" src="../assets/logo.png" />
    <Header />
    <form @submit.prevent="addNewWishlistItem">
      <label for="newWishlistItem">Voer naam nieuw wishlist item in</label
      ><br /><br />
      <input v-model="newWishlistItem" name="newWishlistItem" />
      <br /><br />
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

form {
  display: block;
}

label {
  top: 20rem;
}

input[name="newWishlistItem"] {
  background-color: #3cbc8d;
  outline-color: #3cbc8d;
  color: white;
  outline: none;
  border: 3px solid rgb(0, 157, 255);
  width: 20%;
}

button {
  background-color: #4caf50; /* Green */
  border: none;
  color: white;
  padding: 10px 27px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 12px;
  margin: 4px 2px;
  cursor: pointer;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
}

button:hover {
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.24),
    0 17px 50px 0 rgba(0, 0, 0, 0.19);
}
</style>
