<template>
  <div class="d-inline-block">
    <div class="card me-3 mb-3">
      <img :src="src" alt="" />
      <div>
        <p>
          黏土人 <strong>{{ name }}</strong>
        </p>
        <p>價錢: {{ price }}</p>
        <p>商品描述: {{ desc }}</p>
        <button class="btn-count" @click="reductCount">-</button>
        <span>{{ count }}</span>
        <button class="btn-count" @click="addCount">+</button>
        <button class="btn-add" @click="addCart">加到購物車</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      count: 0,
      cartList:[],
    };
  },
  methods: {
    reductCount() {
      if (this.count > 1) {
        this.count--;
        this.$emit("choosen", { id: this.id, count: this.count, name:this.name,price:this.price });
        this.$emit("cart", { id: this.id, count: this.count, name:this.name,price:this.price, select:this.select });
      }
    },
    addCount() {
      if (this.count < 9) {
        this.count++;
        this.$emit("choosen", { id: this.id, count: this.count,name:this.name,price:this.price });
        this.$emit("cart", { id: this.id, count: this.count, name:this.name,price:this.price, select:this.select });
      }
    },
    addCart() {
      alert(`成功加入購物車，數量:${this.count}`);
      // this.cartList=this.cartList.push(this.cartList)
      // this.cartList =JSON.stringify([{ id: this.id, count: this.count,name:this.name,price:this.price }])
      // localStorage.setItem("ProductCount", this.cartList);
      // this.count = localStorage.getItem('ProductCount')
    },
  },
  computed: {
    //TODO:儲存到localStorage裡
    ProductCount() {
      return localStorage.getItem("ProductCount");
    },
  },
  props: ["id", "price", "src", "name", "desc"],
};
</script>

<style scoped>
img {
  width: 300px;
  border: 1px solid #aaaaaa;
  border-radius: 30px;
}
.card {
  vertical-align: middle;
  padding: 10px 5px;
}
.btn-count{
  font-size: 16px;
  border: none;
  border-radius: 50%;
  margin: 10px;
  background-color: #eee;
}
.btn-add{
  margin: 5px;
  padding: 5px;
  border: 1px solid #aaa;
  border-radius: 10px;
}
</style>