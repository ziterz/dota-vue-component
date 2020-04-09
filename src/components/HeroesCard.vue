<template>
  <div class="col-3 mb-3">
    <div class="card">
      <img :src="hero.imageURL" class="card-img-top">
      <div class="card-body">
        <h5 class="card-title">{{ hero.name }}</h5>
        <p class="card-text" v-if="type[0]"><img :src="type[0].iconURL" width="24px" height="24px"> {{ type[0].name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroesCard",
  props: ['hero', 'type']

}
</script>

<style>

</style>