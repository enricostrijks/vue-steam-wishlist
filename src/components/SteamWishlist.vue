<template>
  <div>
    <h1>Steam Wishlist</h1>
    <div v-for="wishlists in wishlist" v-bind:key="wishlists">
      <SteamWishlistItem v-bind:wishlists="wishlists" />
    </div>
  </div>
</template>

<script>
import SteamWishlistItem from "./SteamWishlistItem.vue";

export default {
  name: "SteamWishlist",
  components: {
    SteamWishlistItem,
  },
  props: ["wishlist"],
};
</script>

<style scoped></style>
