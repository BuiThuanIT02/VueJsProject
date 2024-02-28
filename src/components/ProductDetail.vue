<template>
  <div class="row">
    <div class="col-sm-3 border p-0">
      <img :src="productItem.imge" class="img-fluid" alt="" />
    </div>
    <div class="col-sm-9 border">
      <div class="row">
        <p>{{ productItem.name }}</p>
      </div>
      <div class="row">
        <p>{{ productItem.quantity }}</p>
      </div>
      <div class="row">
        <p>{{ productItem.description }}</p>
      </div>
      <div class="row">
        <p>{{ productItem.price }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    productItem: {
      type: Object,
    },
  },
};
</script>