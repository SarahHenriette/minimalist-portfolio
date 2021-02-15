<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/portfolio">Portfolio</router-link> |
      <router-link to="/contactUs">Contact us</router-link>
    </div> -->
    <Nav/>
    <router-view/>  
  </div>
</template>

<script>
import Nav from '../src/components/Nav'
export default {
  components: {
    Nav
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Ibarra+Real+Nova:wght@400;700&family=Public+Sans&display=swap');
@import './public/sass/colors.scss';
body {
  margin: 0;
}
#app {
  h1 {
    font-family: $ibarra;
    font-size: 50px;
    line-height: 50px;
    font-weight: 700;
  }

  h2 {
    font-family: $ibarra;
    font-size: 40px;
    line-height: 42px;
    font-weight: 700;
  }

  h3 {
    font-family: $ibarra;
    font-size: 32px;
    line-height: 36px;
    font-weight: 400;
  }

  p {
    font-family: $publicSans;
    font-weight: 400;
    line-height: 30px;
  }

  a {
    text-decoration: none;
    font-family: $publicSans;
    font-size: 12px;
    line-height: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: $grayishDarkBlue;
    // margin-left: 43px;
    &:hover {
      color: $greenSlightly;
    }
  }
  li {
    list-style-type: none;
  }
  ul {
    padding-left: 0;
  }


}


</style>
