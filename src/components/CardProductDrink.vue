<template>
  <div class="card shadow card-product">
    <img :src="'assets/images/' + productminuman.gambar " class="card-img-top" alt="..." />
    <div class="card-body">
      <h5 class="card-title">{{ productminuman.nama }}</h5>
      <h5 class="card-text">
        Harga : Rp. {{productminuman.harga}}
      </h5>
      <router-link class="btn btn-success" :to="'/drinks/'+productminuman.id"><b-icon-cart></b-icon-cart> Pesan </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProductDrink",
  props: ["productminuman"],
};
</script>

<style>
</style>