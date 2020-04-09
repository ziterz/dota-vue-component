<template>
  <div class="container">
    <heroes-form
      :types="types"
      @refetchHeroes="refetchHeroes">
    </heroes-form>
    <heroes-list
      :heroes="heroes"
      :types="types">
    </heroes-list>
  </div>
</template>

<script>
import HeroesForm from '../components/HeroesForm'
import HeroesList from '../components/HeroesList'

export default {
  name: "Home",
  components : {
    HeroesForm,
    HeroesList
  },
  props : ['heroes', 'types'],
  methods: {
    refetchHeroes () {
      this.$emit('refetchHeroes');
    }
  }
}
</script>

<style>

</style>