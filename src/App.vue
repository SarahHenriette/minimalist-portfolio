<template>
  <div id="app">
    <Nav/>
    <router-view/>  
    
  </div>
</template>

<script>
import Nav from '../src/components/Nav'

export default {
  components: {
    Nav,
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
  //typography
  $ibarra: 'Ibarra Real Nova', serif;
  $publicSans: 'Public Sans', sans-serif;

  h1 {
    font-family: $ibarra;
    font-size: 50px;
    line-height: 50px;
    font-weight: 700;
    color: $grayishDarkBlue;
  }

  h2 {
    font-family: $ibarra;
    font-size: 40px;
    line-height: 42px;
    font-weight: 700;
    color: $grayishDarkBlue;
  }

  h3 {
    font-family: $ibarra;
    font-size: 32px;
    line-height: 36px;
    font-weight: 400;
    color: $grayishDarkBlue;
  }

  label {
    font-family: $publicSans;
    font-size: 13px;
    font-weight: 700;
    line-height: 30px;
  }
  input::placeholder, textarea::placeholder {
      font-family: $publicSans;
      font-size: 13px;
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
    &:hover {
      color: $greenSlightly!important;
    }
  }
  li {
    list-style-type: none;
  }
  ul {
    padding-left: 0;
  }

  .btn-secondary {
    height: 48px;
    width: 162px;
    background-color: $white;
    border: solid 1px $grayishDarkBlue;
    color: $grayishDarkBlue;
    text-transform: uppercase;
    font-size: 12px;
    line-height: 14px;
    letter-spacing: 2px;
    font-weight: 400;
    font-family: $publicSans;
     display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: background-color ease .5s;
    &:hover {
      background-color: $grayishDarkBlue;
      color: $white;
    }
  }

  .btn-primary {
    height: 48px;
    width: 200px;
    background-color: $darkBlue;
    color: $white;
    position: relative;
    border: none;
    padding:0;
    text-transform: uppercase;
    font-size: 12px;
    line-height: 14px;
    letter-spacing: 2px;
    font-weight: 400;
    font-family: $publicSans;
    text-align: center;
    transition: background-color ease .5s;
    cursor: pointer;
    .arrow-down {
      padding: 15px;
      background-color: $grayishDarkBlue;
      position : absolute;
      top: 0;
      left: 0;
      transition: background-color ease .5s;
      svg {
        stroke: #5FB4A2;
      }
    }
    .text {
      position: absolute;
      width: 152px;
      height: 14px;
      right: 0;
      top: 17px;
      color: $white;
    }
    &:hover {
      background-color: $greenSlightly;
      color: $white;
      .arrow-down {
        background-color: $greenDark;
        svg {
          stroke: $white;
        }
      }
    }
  }
  .line {
    height: 1px;
    background-color: $grayishDarkBlue;
    opacity: 0.15;
  }

}


</style>
