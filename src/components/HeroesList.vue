<template>
  <div class="row mt-3">
    <heroes-card
      v-for="hero in heroes"
      :key="hero.id"
      :hero="hero"
      :type="types.filter(el => el.name === hero.type)">
    </heroes-card>
  </div>
</template>

<script>
import HeroesCard from './HeroesCard'

export default {
  name: "HeroesList",
  components: {
    HeroesCard
  },
  props: ['heroes', 'types']

}
</script>

<style>

</style>