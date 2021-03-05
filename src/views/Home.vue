<template>
  <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col cols="3" v-for="ghost in items.characters" :key="ghost" >
          <b-card
            :title="ghost.name"
            :img-src="ghost.image_url"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem"
            class="mb-2"
          >
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import axios from "axios";

export default {
  props:{
    title: String,
    image: String
  },
  data() {
    return {
      items: "",
    };
  },
  mounted() {
    axios({
      method: "GET",
      url: "https://jikan1.p.rapidapi.com/manga/2/characters",
      headers: {
        "x-rapidapi-key": "3be2405cd7mshd7ba84867da62f6p1a5629jsn324c16641a35",
        "x-rapidapi-host": "jikan1.p.rapidapi.com",
      },
    }).then((res) => {
      this.items = res.data;
    });
  },
};
</script>

<style>
.bg-info {
  background-color: #a813ff !important;
}
.navbar1 {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  height: 80px;
}
.btn-group-sm > .btn,
.btn-sm {
  padding: 0.25rem 0.5rem;
  font-size: 1.275rem;
  line-height: 1.5;
  border-radius: 0.2rem;
}
.btn-secondary {
  color: rgb(0, 0, 0);
  background-color: #007fee;
  border-color: #00c3ff;
}
.form-inline .form-control {
  display: inline-block;
  width: 260px;
  height: 38px;
  vertical-align: middle;
}
.font1 {
  color: rgb(91, 236, 255);
}
</style>