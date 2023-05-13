<template>
  <h1> {{ title }}</h1>
  <p> Welcome ...</p>
  <teleport to="#modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Givaway!</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>  

  <button @click.alt="toggleModal"> open modal (alt)</button> 
 <!-- <input type="text" ref="name">
 <button @click="handleclick">click me</button> -->

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the Newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </teleport>


  <button @click.alt="toggleModalTwo">open modal</button> 
</template>


<script>
import Modal from './components/Modal.vue'

export default { //root component to be exported
  name: 'App',
  components: {Modal},

  data(){
    return {
      title: 'My first vue app',
      header: 'Sign Up',
      text:'this is a text',
      showModal: false,
      showModalTwo: false

    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
     toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
  /*methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    }
  }*/
}
</script>

<style>
#app, #modals { 
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
