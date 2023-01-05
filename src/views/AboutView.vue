<template>
  <div class="about">
    <h1>This is an about page guys</h1>
    <button @click="toggleModal">Show Modal</button>
     <button @click="toggleModal2">Show Modal 2</button>
  </div>
  <div v-if="showModal">
    <Modal :heading="title"  @onCloseModal="toggleModal">
        <p>{{description}}</p>
       <template #actionButton>
            <button @click="toggleModal" style="color:'blue">Close</button>
            <button @click="toggleModal" style="color:'red'">Save</button>
       </template>
    </Modal>
  </div>
  <div v-if="showModal2">
    <Modal heading="goodluck"  @onCloseModal="toggleModal2">
        <p>{{description}}</p>
       <template #actionButton>
            <button @click="toggleModal2" style="color:'blue">Close 2</button>
            <button @click="toggleModal2" style="color:'red'">Save 2</button>
       </template>
    </Modal>
  </div>
</template>

<script>
import Modal from "@/components/Modal.vue";

export default {
  name: "AboutView",
  components: {
    Modal,
  },
  data() {
    return {
      showModal: false,
      showModal2: false,
      title : "testing1",
      description : "testing2 testing2 testing2 testing2"
    };
  },
  methods: {
    toggleModal(){
        this.showModal = !this.showModal
    },
    toggleModal2(){
        this.showModal2 = !this.showModal2
    }
  }
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
