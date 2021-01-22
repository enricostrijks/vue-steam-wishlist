<template>
  <div
    class="wishlist-item"
    v-bind:class="{ 'is-purchased': wishlists.purchased }"
  >
    <p>
      <input type="checkbox" @click="markPurchased(wishlists)" />
      {{ wishlists.title }}
    </p>
    <button @click="removeWishlistItem(wishlists)" class="del">x</button>
  </div>
</template>

<script>
export default {
  name: "SteamWishlistItem",
  props: ["wishlists"],
  methods: {
    markPurchased(wishlists) {
      wishlists.purchased = !wishlists.purchased;
    },
  },
  setup() {
    function removeWishlistItem(wishlists) {
      wishlists.value.splice(wishlists, 1);
    }

    return {
      removeWishlistItem,
    };
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
