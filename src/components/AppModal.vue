<template>
  <div v-if="isOpen" class="modal" @click="handleClose()">
    <div class="modal__container" @click.stop>
      <div class="modal__header">
        <h1 class="modal__title">Cart</h1>
        <div class="modal__close" @click="handleClose()">
          <i class="fa-solid fa-xmark"></i>
        </div>
      </div>
      <div class="modal__body">
        <slot></slot>
        <!-- khi bấm button nào ở đây nó sẽ trôi lên tk cha( modal__body sau đó lên modal__container là cha của modal__body) -->
      </div>
      <div class="modal__footer"></div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    isOpen: {
      type: Boolean,
    },
    handleCloseModal: {
      type: Function,
    },
  },
  methods: {
    handleClose() {
      this.handleCloseModal();
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  display: flex;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.4);
}
.modal__container {
  width: 950px;
  margin: auto;
  margin-top: 70px;
  background: white;
  border: 1px solid #888;
  padding: 10px 20px;
}
.modal__header {
  display: flex;
  justify-content: space-between;
}
.modal__close {
  width: 50px;
  height: 50px;
  line-height: 50px;
  border-radius: 50%;
  text-align: center;
  font-size: 30px;
}
.modal__close:hover {
  background-color: rgba(0, 0, 0, 0.2);
}
</style>