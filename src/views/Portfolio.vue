<template>
  <main class="portfolio">
      <section  v-for="item in portfolio.images" :key="item.id" class="item-portfolio">
        <div class="image-item-portfolio">
          <img :src= item.url   alt="preview du projet"/>
        </div>
        <div class="text-item-portfolio">
          <div class="line"></div>
          <h2>{{ item.title }}</h2>
          <p>{{ item.description }}</p>
          <router-link class="btn-secondary" :to="{ name: 'portfolio', params: { title: item.title }, query:{id: item.id}} ">View project</router-link>
          <div class="line"></div>
        </div>
      </section>
      <Footer/>
  </main>
</template>


<script>
import Footer from '../components/Footer'
import portfolioJson from '../../src/assets/portfolio.json'
export default {
  components: {
    Footer,
  },
  data () {
    return {
      portfolio : portfolioJson,
    }
  },
}
</script>

<style lang="scss" scoped>
.portfolio {
  padding-top: 47px;
  .item-portfolio {
    width: 1015px;
    height: 500px;
    display: flex;
    padding-bottom: 80px;
    margin: auto;

    .image-item-portfolio {
      width: 540px;
      height: 500px;

      img {
        width: 100%;
      }
    }

    .text-item-portfolio {
      width: 350px;
      height: 500px;

      h2 {
        margin-top: 103px;
        margin-bottom: 28px;
      }

      p {
        font-size: 16px;
      }

      a {
        margin-top: 24px;
        margin-bottom: 103px;
      }
    }
  }

  .item-portfolio:nth-of-type(2n+1) {
    margin-left: 165px;

    .text-item-portfolio {
      margin-left: 125px;
    }
  }

  .item-portfolio:nth-of-type(2n) {
    flex-direction: row-reverse;
    margin-right: 165px;

    .text-item-portfolio {
      margin-right: 125px;
    }
  }
}

@media screen and (max-width: 1200px) {
  .portfolio {
    .item-portfolio {
      width: 689px;
      height: 418px;
      padding-bottom: 72px;
    margin: auto!important;
      .image-item-portfolio {
        height: 418px;
        display: flex;
        justify-content: center;
        align-items: center;
      }

      .text-item-portfolio {
        h2 {
          margin-top: 32px;
        }

        p {
          width: 281px;
          height: 180px;
          font-size: 15px;
        }

        a {
          margin-bottom: 50px;
        }
      }
    }

    .item-portfolio:nth-of-type(2n+1) {
      margin-left: 0;

      .text-item-portfolio {
        margin-left: 69px;
      }
    }

    .item-portfolio:nth-of-type(2n) {
      margin-right: 0px;

      .text-item-portfolio {
        margin-right: 69px;
      }
    }
  }
}

@media screen and (max-width: 600px) {
  .portfolio {
    padding-top: 0;

    .item-portfolio {
      flex-direction: column;
      width: 311px;
      height: 662px;

      .image-item-portfolio {
        width: auto;
        height: 288px;
        margin-bottom: 32px;
      }

      .text-item-portfolio {
        width: auto;
        height: 368px;

        h2 {
          margin-top: 25px;
        }

        p {
          width: auto;
          height: 180px;
          font-size: 15px;
          margin-top: 25px;
        }

        a {
          margin-top: 25px;
          margin-bottom: 24px;
        }
      }
    }

    .item-portfolio:nth-of-type(2n+1) {
      margin-left: 32px;

      .text-item-portfolio {
        margin-left: 0;
      }
    }

    .item-portfolio:nth-of-type(2n) {
      flex-direction: column;
      margin-right: 40px;

      .text-item-portfolio {
        margin-right: 0;
      }
    }
  }
}
</style>