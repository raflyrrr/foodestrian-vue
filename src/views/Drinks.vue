<template>
  <div>
    <Navbar />
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h2>Daftar<strong> Minuman</strong></h2>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input
            v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari Minuman Kesukaan Anda .."
              aria-label="Cari"
              aria-describedby="basic-addon1"
              @keyup="searchFood"
            />
            <span class="input-group-text" id="basic-addon1"
              ><b-icon-search></b-icon-search
            ></span>
          </div>
        </div>
      </div>

      <div class="row mb-4">
        <div
          class="col-md-4 mt-4"
          v-for="minuman in minumans"
          :key="minuman.id"
        >
          <h2><CardProductDrink :productminuman="minuman" /></h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import CardProductDrink from "@/components/CardProductDrink.vue";
import axios from "axios";
export default {
  name: "Drinks",
  components: {
    Navbar,
    CardProductDrink,
  },
  data() {
    return {
      minumans: [],
      search: '',
    };
  },
  methods: {
    setMinuman(data) {
      this.minumans = data;
    },
    searchFood(){
       axios
      .get("http://localhost:3000/minuman?q="+this.search)
      .then((response) => this.setMinuman(response.data))
      .catch((error) => console.log(error));

    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/minumans")
      .then((response) => this.setMinuman(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style></style>
