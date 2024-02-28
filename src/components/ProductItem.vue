<template>
  <div class="card text-left mb-5 mt-3">
    <img class="card-img-top" :src="productItem.imge" alt="" />
    <div class="card-body">
      <h4 class="card-title">{{ productItem.name }}</h4>
      <p class="card-text font-weight-bold text-danger">
        {{ productItem.price }}
      </p>
    </div>
    <div class="ml-5">
      <button class="btn btn-danger ml-2" @click="hanldeBuy(productItem)">
        Mua
      </button>
      <button class="btn btn-info ml-2" @click="handleOpenModal">
        Chi tiet
      </button>
    </div>
  </div>
  <Teleport to="#app">
    <app-modal :isOpen="isOpen" :handleCloseModal="handleCloseModal">
      <product-detail-vue :productItem="productItem" />
    </app-modal>
  </Teleport>
</template>
<script>
import AppModal from "./AppModal.vue";
import ProductDetailVue from "./ProductDetail.vue";

export default {
  components: { AppModal, ProductDetailVue },
  data() {
    return {
      isOpen: false,
    };
  },
  props: {
    productItem: {
      type: Object,
    },
  },
  methods: {
    hanldeBuy(productItem) {
      // sử lý clich mua
      this.$emit("hanlde-buy", productItem);
    },
    handleOpenModal() {
      // sử lý mở đóng modal
      this.isOpen = true;
    },
    handleCloseModal() {
      this.isOpen = false;
    },
  },
};
</script>