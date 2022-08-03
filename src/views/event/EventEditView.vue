<template>
  <p>Edit the event here</p>
  <button @click="edit">Edit here</button>
</template>

<script>
export default {
  props: ['id', 'resa', 'event'],
  inject: ['GStore'], //<---- Inject the Global Store
  methods: {
    edit() {
      //Assuming successful API call to register them

      //Set a flash message to appear on the next page loaded which says
      //'You are successfully registered for ' + this.event.title
      this.GStore.flashMessage = 'The data has been update '
      setTimeout(() => {
        //After 3 secound remove it
        this.GStore.flashMessage = ''
      }, 3000)
      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id }
      })
    }
  }
}
</script>
