<template>
  <section class="product-list">
    <h2 class="text-center text-danger font-weight-bold">
      Các sản phẩm nổi bật
    </h2>
    <div class="pro-list row">
      <div
        class="col-lg-3"
        v-for="productItem in productList"
        :key="productItem.id"
      >
        <product-item :productItem="productItem" @hanlde-buy="hanldeBuy" />
      </div>
    </div>
  </section>
</template>
<script>
import ProductItem from "./ProductItem.vue";
import sp1 from "../assets/Images/12-ly-do.png";
import sp2 from "../assets/Images/12-truong.png";
import sp3 from "../assets/Images/am-thuc-the-gioi.png";
import sp4 from "../assets/Images/chi-pheo.png";
import sp5 from "../assets/Images/chuot-ty-bieng-an.png";
import sp6 from "../assets/Images/conan.png";
export default {
  components: {
    ProductItem,
  },
  methods: {
    hanldeBuy(productItem) {
      this.$emit("hanlde-buy", productItem);
    },
  },
  data() {
    return {
      productList: [
        {
          id: 1,
          name: "Truyen tranh 12 lý do",
          imge: sp1,
          description: "truyên hay lắm ahihi",
          price: 500,
          sale: 10,
          quantity: 55,
        },
        {
          id: 2,
          name: "Truyen tranh 12 trường",
          imge: sp2,
          description: "truyên hay lắm ahihi",
          price: 600,
          sale: 10,
          quantity: 55,
        },
        {
          id: 3,
          name: "Truyen tranh ẩm thực thế giới",
          imge: sp3,
          description: "truyên hay lắm ahihi",
          price: 7800,
          sale: 10,
          quantity: 55,
        },
        {
          id: 4,
          name: "Truyen tranh chí phèo",
          imge: sp4,
          description: "truyên hay lắm ahihi",
          price: 8500,
          sale: 10,
          quantity: 55,
        },
        {
          id: 5,
          name: "Truyen tranh chuột tý biếng",
          imge: sp5,
          description: "truyên hay lắm ahihi",
          price: 9500,
          sale: 10,
          quantity: 55,
        },
        {
          id: 6,
          name: "Truyen tranh conna",
          imge: sp6,
          description: "truyên hay lắm ahihi",
          price: 7500,
          sale: 10,
          quantity: 55,
        },
      ],
    };
  },
};
</script>