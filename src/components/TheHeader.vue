<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand logo" href="#">TurnCart</a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="#"
            >Home <span class="sr-only">(current)</span></a
          >
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Dropdown
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Something else here</a>
          </div>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#">Disabled</a>
        </li>
      </ul>
      <form class="form-inline my-2 my-lg-0">
        <input
          class="form-control mr-sm-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
          Search
        </button>
      </form>
      <!-- cart -->
      <div class="ml-1">
        <button class="btn btn-danger" @click="handleOpenModalCartList()">
          <i class="fa-solid fa-cart-shopping"></i>
          <span class="badge badge-light ml-1">{{ cartList.length }}</span>
        </button>
      </div>
    </div>
  </nav>
  <!-- lưu ý truyền prop function thì không nên cho (); -->
  <teleport to="#app">
    <app-modal
      :isOpen="isOpenModalCartList"
      :handleCloseModal="handleCloseModalCartList"
    >
      <section>
        <cart-list
          :cartList="cartList"
          @hanlde-delete-cart="hanldeDelete"
          @handle-up-or-dow-amount-cart="handleUpOrDowAmount"
        ></cart-list>
      </section>
    </app-modal>
  </teleport>
</template>
<script>
import AppModal from "./AppModal.vue";
import CartList from "./CartList.vue";
export default {
  components: { AppModal, CartList },
  props: {
    cartList: {
      type: Array,
    },
  },
  data() {
    return {
      isOpenModalCartList: false, // đóng modal
    };
  },
  methods: {
    handleOpenModalCartList() {
      this.isOpenModalCartList = true; // mở modal
    },
    handleCloseModalCartList() {
      this.isOpenModalCartList = false; // đóng modal
    },
    hanldeDelete(productId) {
      // xóa 1 sản phẩm trong giỏ hàng

      this.$emit("hanlde-delete-cart", productId);
    },
    handleUpOrDowAmount(params) {
      this.$emit("handle-up-or-dow-amount-cart", params);
    },
  },
};
</script>
<style scoped>
.logo {
  font-size: 30px;
  /**chuyển màu */
  background: -webkit-linear-gradient(#41b883, #35495e, yellow);
  -webkit-background-clip: text; /**dùng cho text */
  -webkit-text-fill-color: transparent;
}
</style>