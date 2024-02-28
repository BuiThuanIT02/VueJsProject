<template>
  <table class="table">
    <thead>
      <tr>
        <th>STT</th>
        <th>Tên</th>
        <th>Giá</th>
        <th>Số lượng trong kho</th>
        <th>Số lượng mua</th>
        <th>Thành tiền</th>
        <th>Hành động</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(cart, index) in cartList" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ cart.name }}</td>
        <td>{{ cart.price }}</td>
        <td>{{ cart.quantity }}</td>
        <td>
          <button
            class="btn btn-success"
            @click="handleUpOrDowAmount(true, cart)"
          >
            <i class="fa-solid fa-plus"></i>
          </button>
          <span class="mx-2">{{ cart.amount }}</span>
          <button
            class="btn btn-success"
            @click="handleUpOrDowAmount(false, cart)"
          >
            <i class="fa-solid fa-minus"></i>
          </button>
        </td>
        <td>{{ cart.amount * cart.price }}</td>
        <td>
          <button class="btn btn-danger" @click="hanldeDelete(cart.id)">
            <i class="fa-solid fa-trash"></i>Xóa
          </button>
        </td>
      </tr>
      <tr>
        <td>Tổng tiền</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td>{{ sumMoney }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  props: {
    cartList: {
      type: Array,
    },
  },
  computed: {
    sumMoney() {
      return this.cartList.reduce((sum, cart) => {
        return (sum += cart.price * cart.amount);
      }, 0);
    },
  },
  methods: {
    hanldeDelete(productId) {
      this.$emit("hanlde-delete-cart", productId);
    },
    handleUpOrDowAmount(status, cart) {
      this.$emit("handle-up-or-dow-amount-cart", { ...cart, status: status });
    },
  },
};
</script>