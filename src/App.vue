<template>
  <header>
    <the-header
      :cartList="cartList"
      @hanlde-delete-cart="hanldeDelete"
      @handle-up-or-dow-amount-cart="handleUpOrDowAmount"
    />
  </header>
  <main class="container">
    <product-list @hanlde-buy="hanldeBuy" />
  </main>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import ProductList from "./components/ProductList.vue";
export default {
  name: "App",
  components: {
    TheHeader,
    ProductList,
  },
  methods: {
    hanldeBuy(productItem) {
      const index = this.cartList.findIndex(
        (cart) => cart.id === productItem.id
      ); // tìm vị trí index của sản phẩm trong giỏ hàng nếu bằng productItem
      if (index !== -1) {
        // sản phẩm đã tồn tại trong giỏ hàng, tăng amount lên 1
        this.cartList[index].amount += 1;
      } else {
        // sản phẩm chưa tồn tại trong giỏ hàng
        this.cartList = [...this.cartList, { ...productItem, amount: 1 }]; // sử dụng spread(giải )
      }
    },
    hanldeDelete(productId) {
      // xóa sản phẩm trong cart
      this.cartList = this.cartList.filter((cart) => cart.id !== productId);
    },
    handleUpOrDowAmount(params) {
      console.log(params);

      this.cartList.forEach((cart) => {
        // cách tối ưu hơn là dùng finIndex để tìm vị trí

        if (cart.id === params.id) {
          if (params.status) {
            if (cart.amount < cart.quantity) {
              cart.amount += 1;
            } else {
              alert("Quá số lượng!!");
            }
          } else {
            if (cart.amount > 1) {
              cart.amount -= 1;
            } else {
              alert("Số lượng >1!!");
            }
          }
        }
      });
    },
  },
  data() {
    return {
      cartList: [],
    };
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
  /* margin-top: 60px; */
}
</style>
