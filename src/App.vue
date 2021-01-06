<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <transition name="fade">
    <div v-if="showModal">
      <Modal theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">Sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Giveaway!</h1>
        <p>Grab you ninja swag!</p>
      </Modal>
    </div>
  </transition>
  <transition name="fade">
    <div v-if="showModal2">
      <Modal theme="" @close="toggleModal2">
        <template v-slot:links>
          <a href="#">Sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>modal2!</h1>
        <p>hello world</p>
      </Modal>
    </div>
  </transition>
  <button @click="toggleModal">open modal</button>
  <button @click="toggleModal2">open modal 2</button>
  <br />
  <input type="text" ref="name" />
  <button @click="handleClick">click me</button>
</template>

<script>
  import Modal from './components/Modal.vue';

  export default {
    name: 'App',
    components: {
      Modal,
    },
    data() {
      return {
        title: 'My First Vue App ;)',
        header: 'Sign up for the Giveaway!',
        text: 'Grab your ninja swag for half price!',
        showModal: false,
        showModal2: false,
      };
    },
    methods: {
      handleClick() {
        console.log(this.$refs.name);
        this.$refs.name.classList.add('active');
        this.$refs.name.focus();
      },
    },
    methods: {
      toggleModal() {
        this.showModal = !this.showModal;
      },
      toggleModal2() {
        this.showModal2 = !this.showModal2;
      },
    },
  };
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
    border-bottom: 1px solid #ddd;
    display: inline-block;
    padding-bottom: 10px;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s;
  }

  /* // If you are using Vue3: the v-enter/v-leave classes are now v-enter-from/v-leave-from */
  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
</style>
