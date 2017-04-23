<template>
  <div class="row" id="translateForm">
  <div class="col-md-6 col-md-offset-3"></div>
    <form id="transform" class="well form-inline" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word...">
      <select class="form-control" v-model="language">
        <option value="ru">Russian</option>
        <option value="es">Spanish</option>
        <option value="de">German</option>
        <option value="fr">French</option>
        <option value="pl">Polish</option>
        <option value="pt">Portuguese</option>
        <option value="uk">Ukranian</option>
        <option value="hy">Armenian</option>
        <option value="mi">Maori</option>


      </select>
      <input class="btn btn-primary" type="submit" value="translate">
    </form>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate:'',
      language: ''
    }
  },
  created() {
  this.language = 'pl';
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
}
</script>

<style>
#transform {
  border-radius: 10px;
  border: 1px #ccc solid;
}
</style>
