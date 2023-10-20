<template>
  <div class="modal1" v-if="show_modal">
    <Modal status="" @close="toggleModal">
      <h1>{{ modal_header }}</h1>
      <p>{{ modal_p_text }}</p>
      <template v-slot:links>
        <a href="#">sign up</a>
        <a href="#">sign in</a>
      </template>
    </Modal>
  </div>

  <div class="modal2" v-if="show_info_modal">
    <Modal @close="toggleInfoModal">
      <h1>{{ info_modal_heading }}</h1>
      <p>{{ info_modal_text }}</p>
      <template v-slot:links>
        <a href="#">view more</a>
        <a href="#">next task</a>
      </template>
    </Modal>
  </div>

  <h1>{{ title }}</h1>

  <br>

  <input type="text" ref="input_name">
  <button @click="clickHandler">click me</button>
  
  <p>click to see modal</p>
  <button @click="toggleModal">show modal</button>
  
  <p>click to see info modal</p>
  <button @click="toggleInfoModal">show info modal</button>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: "This is the first title of my Vue app",
      modal_header: "modal heading from props",
      modal_p_text: "this is small paragraph text from props",
      show_modal: false,

      info_modal_heading : "this is secondary heading",
      info_modal_text: "some random text",
      show_info_modal: false,
    }
  },
  methods: {
    clickHandler() {
      console.log(this.$refs.input_name)
      this.$refs.input_name.classList.add("FISH")
      this.$refs.input_name.focus()
    },

    toggleModal() {
      this.show_modal = !this.show_modal
    },

    toggleInfoModal() {
      this.show_info_modal = !this.show_info_modal
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid cadetblue;
  display: inline-block;
  padding-bottom: 10px;
}

input {
  margin-top: 50px;
}

</style>
