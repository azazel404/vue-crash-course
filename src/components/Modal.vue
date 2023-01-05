<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <h1>{{ heading }}</h1>
      <!-- passing concept children -->
      <slot></slot>
      <!-- concept children spesific -->
       <div class="actions">
            <slot name="actionButton"></slot>
       </div>
    </div>
  </div>
</template>

<script>
export default {
  //properties
  props: ['heading', 'text', 'theme'],
  //callback func the closeModal method when the backdrop is clicked
  methods: {
    closeModal() {
     //declare name callback func
      this.$emit('onCloseModal')
    }
  }
}
</script>

<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 200px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }
  .modal h1 {
    color: black;
    border: none;
    padding: 0;
  }
  .modal p {
    font-style: normal;
    color:black
  }
  /* sale styles */
  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
</style>