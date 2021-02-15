<template>
  <main class="portfolio">
      <section  v-for="item in portfolio" :key="item.id" class="item-portfolio">
        <div class="image-item-portfolio">
          <img :src= item.url  alt=""/>
        </div>
        <div class="text-item-portfolio">
          <div class="line"></div>
          <h2>{{ item.title }}</h2>
          <p>{{ item.description }}</p>
          <router-link class="btn-secondary" :to="{ name: 'portfolio', params: { title: item.title }, query:{item}} ">View project</router-link>
          <div class="line"></div>
        </div>
      </section>
  </main>
</template>


<script>
export default {
  components: {
  },
  data () {
    return {
      portfolio : [
        {
          "id": 1,
          "title": "Manage",
          "description": "This project required me to build a fully responsive landing page to the designs provided. I used HTML5, along with CSS Grid and JavaScript for the areas that required interactivity, such as the testimonial slider.",
          "techno": "HTML / CSS / JS",
          "url": require('@/assets/images/portfolio/desktop/image-portfolio-manage@2x.jpg') 
          // "image-detail-header": "image-manage-hero@2x",
          // "image-detail-01": "image-manage-preview-1@2x",
          // "image-detail-02": "image-mange-preview-2@2x"
        },
        {
          "id": 2,
          "title": "Bookmark",
          "description": "This project required me to build a fully responsive landing page to the designs provided. I used HTML5, along with CSS Grid and JavaScript for the areas that required interactivity, such as the features section.",
          "techno": "HTML / CSS / JS",
          "url": require('@/assets/images/portfolio/desktop/image-portfolio-bookmark@2x.jpg') 
          // "image-detail-header": "image-manage-hero@2x",
          // "image-detail-01": "image-manage-preview-1@2x",
          // "image-detail-02": "image-mange-preview-2@2x"
        },
        {
          "id": 3,
          "title": "Insure",
          "description": "This was a small project which mostly consisted of HTML and CSS. I built a fully-responsive landing page. The only JavaScript this project required was to enable the toggling of the mobile navigation.",
          "techno": "HTML / CSS / JS",
          "url": require('@/assets/images/portfolio/desktop/image-portfolio-insure@2x.jpg') 
          // "image-detail-header": "image-manage-hero@2x",
          // "image-detail-01": "image-manage-preview-1@2x",
          // "image-detail-02": "image-mange-preview-2@2x"
        },
                {
          "id": 4,
          "title": "Fylo",
          "description": "This project was built in pure HTML and CSS. I had mobile and desktop designs to work to and built it so that it was fully-responsive. I took a mobile-first approach and used modern CSS like Flexbox and Grid for layout purposes.",
          "techno": "HTML / CSS / JS",
          "url": require('@/assets/images/portfolio/desktop/image-portfolio-fylo@2x.jpg') 
          // "image-detail-header": "image-manage-hero@2x",
          // "image-detail-01": "image-manage-preview-1@2x",
          // "image-detail-02": "image-mange-preview-2@2x"
        },
  ]
  
    }
  },
  mounted () {
  }
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
      margin-left: 39px;

      .text-item-portfolio {
        margin-left: 69px;
      }
    }

    .item-portfolio:nth-of-type(2n) {
      margin-right: 40px;

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