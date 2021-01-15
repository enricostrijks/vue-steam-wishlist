<template>
  <div
    class="wishlist-item"
    v-bind:class="{ 'is-purchased': wishlists.purchased }"
  >
    <p>
      <input type="checkbox" v-on:change="markPurchased" />
      {{ wishlists.title }}
    </p>
  </div>
</template>

<script>
export default {
  name: "SteamWishlistItem",
  props: ["wishlists"],
  methods: {
    markPurchased() {
      this.wishlists.purchased = !this.wishlists.purchased;
    },
  },
};
</script>

<style scoped>
.wishlist-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-purchased {
  text-decoration: line-through;
}
.del {
  background: red;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
