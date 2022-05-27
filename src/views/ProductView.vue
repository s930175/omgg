<template>
  <a @click="productFilter = 'all'" href="javascript:;">所有商品</a> |
  <a @click="productFilter = 'buy'" href="javascript:;">購物車</a>
  <Carouse></Carouse>
  <Describe
    @choosen="putIntoCart"
    v-for="item in showProducts"
    :key="item.id"
    :="item"
  >
  </Describe>
  <router-link to="/cart" class="pay" @click="haha">結帳</router-link>
  <!-- <PayView :count="item.count" v-for="item in showProducts" :key="item.id" :="item"></PayView> -->
  <!-- <router-link to="/cart"><a @click="productFilter='buy'" href="javascript:;">結帳</a></router-link> -->
</template>

<script>
import Describe from "../components/DescribeView.vue";
import Carouse from "../components/CarouselView.vue";
import PayView from "../components/PayView.vue";
export default {
  components: {
    Describe,
    Carouse,
    PayView,
  },
  data() {
    return {
      // choosenProduct: localStorage.setItem("choosenProduct") || [],
      // choosenProduct:[],
      productFilter: "all",
      cartList: [],
      imgs: [
        {
          id: 1,
          name: "拉芙塔莉雅",
          src: "../img/01盾勇.jpg",
          desc: "001",
          price: 1800,
        },
        {
          id: 2,
          name: "太空機器人",
          src: "../img/02太空機器人.jpg",
          desc: "002",
          price: 1500,
        },
        {
          id: 3,
          name: "日向雛田",
          src: "../img/03雛田.jpg",
          desc: "003",
          price: 1490,
        },
        {
          id: 4,
          name: "阿爾托莉亞",
          src: "../img/04lancer.jpg",
          desc: "004",
          price: 2000,
        },
        {
          id: 5,
          name: "喜多川佑介",
          src: "../img/05喜多川.jpg",
          desc: "005",
          price: 1750,
        },
        {
          id: 6,
          name: "伏黑惠",
          src: "../img/06伏黑.jpg",
          desc: "006",
          price: 1660,
        },
        {
          id: 7,
          name: "艾連葉卡",
          src: "../img/07艾連.jpg",
          desc: "007",
          price: 2100,
        },
        {
          id: 8,
          name: "波吉",
          src: "../img/08波吉.jpg",
          desc: "008",
          price: 1800,
        },
        {
          id: 9,
          name: "空條承太郎",
          src: "../img/10承太郎.jpg",
          desc: "009",
          price: 1850,
        },
      ],
    };
  },
  computed: {
    showProducts() {
      switch (this.productFilter) {
        case "all":
          return this.imgs;
          break;
        case "buy":
          this.cartList = JSON.stringify(this.imgs);
          localStorage.setItem("ProductCount", this.cartList);
          return this.imgs.filter((item) => item.count > 0);
      }
      //console.log(item);
      //search
      // if (this.search && this.search.length > 0) {
      //   var current = [];
      //   console.log(current)
      //   current = current.filter(function (item) {
      //     var find =this.search.toLowerCase();
      //     var name = item.name.toLowerCase();
      //     return name.indexOf(find) > -1;
      //   });
      // }
    },
    // sum() {
    //   let sum = 0;
    //   this.imgs.forEach(function (item) {
    //     sum += item.price * item.count;
    //   });
    // },
  },
  methods: {
    putIntoCart(info) {
      this.imgs.map(function (item) {
        if (item.id == info.id) {
          item.count = info.count;
        }
      });
      // console.log(this.imgs);
    },
    haha() {
      this.cartList = JSON.stringify(this.imgs);
      localStorage.setItem("ProductCount", this.cartList);
    },
  },
  watch: {},
  mouted() {
    //用來塞入BS的JS
    (function () {});
  },
};
</script>

<style scoped>
img {
  width: 100%;
  border: transparent;
}
a {
  text-decoration: none;
  color: black;
  font-family: Arial, Helvetica, sans-serif;
}
.pay {
  padding: 10px;
  border: 1px solid #aaa;
  border-radius: 5px;
}
</style>

