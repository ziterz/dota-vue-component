<template>
  <div class="row">
    <div class="col-6 offset-3 mt-3">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Choose your heroes</h5>
          <form @submit.prevent="addHeroes">
            <div class="form-group row">
              <label for="name" class="col-sm-4 col-form-label">Heroes Name</label>
              <div class="col-sm-8">
                <input type="text" class="form-control" id="name" v-model="form.name" required>
              </div>
            </div>
            <div class="form-group row">
              <label for="type" class="col-sm-4 col-form-label">Type</label>
              <div class="col">
                <select id="type" class="form-control" v-model="form.type" required>
                  <option value="" disabled>Please select one</option>
                  <option :value="type.name" v-for="type in types" :key="type.id">{{ type.name }}</option>
                </select>
              </div>
            </div>
            <div class="form-group row">
              <label for="image" class="col-sm-4 col-form-label">Image</label>
              <div class="col-sm-8">
                <input type="text" class="form-control" id="image" v-model="form.image" required>
              </div>
            </div>
            <div class="form-group row">
              <div class="col">
                <input type="submit" class="btn btn-danger" value="Pick Heroes">
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "HeroesForm",
  data () {
    return {
      form: {
        name: '',
        type: '',
        image: ''
      }
    }
  },
  props :['types'],
  methods: {
    addHeroes () {
      axios({
        method: "POST",
        url: "http://localhost:3000/heroes",
        data : {
          name: this.form.name,
          type: this.form.type,
          imageURL: this.form.image
        }
      })
        .then(({data}) => {
          this.clearForm();
          this.$emit('refetchHeroes');
        })
        .catch(err => {
          console.log(err);
        })
    },
    clearForm () {
      this.form.name = '';
      this.form.type = '';
      this.form.image = '';
    }
  }

}
</script>

<style>

</style>