<template>
  <div>
    <h1>Steam Wishlist</h1>
    <div v-for="(wishlistitem, index) in wishlist" v-bind:key="wishlistitem">
      <!-- <SteamWishlistItem v-bind:wishlistitem="wishlistitem" /> -->
      <div
        class="wishlist-item"
        v-bind:class="{ 'is-purchased': wishlistitem.purchased }"
      >
        <p>
          <input type="checkbox" @click="markPurchased(wishlistitem)" />
          {{ wishlistitem.title }}
          <button @click="$emit('delitem'), index" class="del">
            x
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SteamWishlist",
  props: ["wishlist"],
  methods: {
    markPurchased(wishlistitem) {
      wishlistitem.purchased = !wishlistitem.purchased;
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
