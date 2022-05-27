<template>
  <div class="main-header">
    <div class="container">
      <li class="nav-item dropdown">
        <router-link
          class="nav-link dropdown-toggle"
          to="/login"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="currentColor"
            class="bi bi-person"
            viewBox="0 0 16 16"
          >
            <path
              d="M8 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm2-3a2 2 0 1 1-4 0 2 2 0 0 1 4 0zm4 8c0 1-1 1-1 1H3s-1 0-1-1 1-4 6-4 6 3 6 4zm-1-.004c-.001-.246-.154-.986-.832-1.664C11.516 10.68 10.289 10 8 10c-2.29 0-3.516.68-4.168 1.332-.678.678-.83 1.418-.832 1.664h10z"
            />
          </svg>
        </router-link>
      </li>
      <nav class="main-nav">
        <router-link to="/">首頁</router-link>
        <router-link to="/post" class="login d-show">公告</router-link>
        <router-link to="/product">產品</router-link>
        <router-link to="/cart">訂單</router-link>
        <router-link to="/pre" class="login d-show">預購</router-link>
        <router-link to="/add" class="login d-show">加入會員</router-link>
      </nav>
      <form class="header-search" action="">
        <input
          type="search"
          name=""
          id=""
          placeholder="輸入關鍵字"
          class="header-search-input"
        />
        <button>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            fill="currentColor"
            class="bi bi-search"
            viewBox="0 0 16 16"
          >
            <path
              d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"
            />
          </svg>
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filter: "all",
    };
  },
  mouted() {
    //用來塞入BS的JS
    ;(function () {
      
    });
  },
};
</script>
<style scoped lang="less">

li {
  list-style: none;
}

.bi-person {
  color: rgb(0, 0, 0);
}

.nav-link::after {
  color: rgb(196, 52, 52);
}

.bi-search:hover {
  color:#aaa;
}

.header-search-input {
  width: 70%;
  // @media screen and (max-width:768px){
  //   display: none;
  // }
}

.carousel-item img {
  width: 100%;
  height: 350px;
  overflow: hidden;
}

.main-header {
  background: linear-gradient(#fff,rgba(200,200,200,.5), #fff);
  padding: 10px;
}

.main-header .container {
  display: flex;
  align-items: center;
  max-width: 80%;
  margin-right: 30px;
}

.main-header .logo {
  width: 100px;
}

.main-header .logo img {
  width: 100%;
  vertical-align: middle;
}

.main-header .main-nav {
  margin: auto;
  display: flex;
}

.main-header .main-nav a {
  text-decoration: none;
  color: rgb(0, 0, 0);
  padding: 5px 1em;
  position: relative;
  transform: translateY(0px);
  transition: 0.3s;
}

.main-header .main-nav a:hover {
  transform: translateY(-5px);
}

.main-header .main-nav a:after {
  content: "";
  position: absolute;
  left: 50%;
  right: 50%;
  height: 0;
  bottom: -5px;
  border-bottom: 1px solid #aaa;
  transition: 0.4s;
}

.main-header .main-nav a:hover:after {
  left: 0;
  right: 0;
}

.main-header .header-search {
  display: flex;
}

.main-header .header-search button,
.main-header .header-search input {
  border: 1px solid #aaa;
  background-color: #fff;
  padding: 5px 10px;
}
.main-header .header-search button:focus,
.main-header .header-search input:focus {
  outline: none;
}

.main-header .header-search button {
  border-radius: 0 200px 200px 0;
  border-left: none;
}

.main-header .header-search input {
  border-radius: 200px 0 0 200px;
  border-right: none;
}
.main-nav {

  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    text-shadow: #aaa;

    &.router-link-exact-active {
      color: #aaa;
    }
  }
}
</style>