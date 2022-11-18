<script>
export default {
  name: "CardComp",
  props: {
    actors: Array,
  },
};
</script>

<template>
  <div class="card-cont">
    <div class="ib-card">
      <div class="img-cont">
        <img :src="actors.img" alt="" />
      </div>
      <div class="text-cont">
        <h4>{{ actors.name }}</h4>
        <p>{{ actors.category }}</p>
        <p>{{ actors.status }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../styles/Variables" as *;
@use "../styles/Mixin" as *;
.card-cont {
  width: calc(100% / 5);
  padding: 15px;
  min-width: 200px;
  margin: auto;
  height: 520px;
  .ib-card {
    background-color: $primary-color;
    padding: 10px;
    border-radius: 20px;

    .img-cont {
      height: 280px;
      margin-bottom: 25px;
      img {
        width: 100%;
        object-fit: cover;
        border-radius: 20px;
      }
    }
  }
}
.text-cont {
  text-align: center;
  height: 150px;
  h4 {
    color: #fff;
  }
  p {
    color: #4c5c63;
  }
}
</style>
