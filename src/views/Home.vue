<template>
  <div class="home" id="home">
    <header>
      <section class="text-header">
        <h1>Hey, I’m Alex Spencer and I love building beautiful websites</h1>
        <a href="#aboutMe" class="btn-primary"><span class="arrow-down"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="14"><g fill="none" fill-rule="evenodd" stroke=""><path d="M0 9l8 4 8-4"/><path opacity=".5" d="M0 5l8 4 8-4"/><path opacity=".25" d="M0 1l8 4 8-4"/></g></svg></span><span class="text">About me</span></a>
      </section>
    </header>
    <main id="aboutMe">
     <figure class="image-aboutMe">
     </figure>
     <section class="text-aboutMe">
       <div class="line"></div>
       <h2>About Me</h2>
       <p>
         I’m a junior front-end developer looking for a new role in an exciting company. I focus on writing accessible HTML, using modern CSS practices and writing clean JavaScript. When writing JavaScript code, I mostly use React, but I can adapt to whatever tools are required. I’m based in London, UK, but I’m happy working remotely and have experience in remote teams. When I’m not coding, you’ll find me outdoors. I love being out in nature whether that’s going for a walk, run or cycling. I’d love you to check out my work.
       </p>
       <router-link to="/portfolio" class="btn-secondary">Go to portfolio</router-link>
       <div class="line"></div>
     </section>
    </main>
    <Footer/>
  </div>
</template>

<script>
import Footer from '../components/Footer'

export default {
  name: 'Home',
  components: {
    Footer
  }
}
</script>

<style lang="scss" scoped>
@import './public/sass/colors.scss';
.home {
  header {
    width: 1110px;
    height: 600px;
    margin: auto;
    position: relative;
    background-image: url("../../public/images/homepage/desktop/image-homepage-hero.jpg");
    margin-bottom: 150px;
    .text-header {
      width: 445px;
      height: 357px;
      background-color: $white;
      position: absolute;
      bottom: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      h1 {
        width: 400px;
        height: 200px;
        margin-bottom: 53px;
      }
    }
  }
  #aboutMe {
    width: 1110px;
    height: 600px;
    display: flex;
    margin: auto;
    margin-bottom: 150px;
    .image-aboutMe {
      background-image: url("../../public/images/homepage/desktop/image-homepage-profile.jpg");
      margin: 0;
      width: 540px;
      height: 600px;
      img {
        width: 100%;
      }
    }
    .text-aboutMe {
      width: 350px;
      height: 600px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      margin-left: 125px;
      h2 {
        margin-bottom: 28px;
        margin-top: 50px;
      }
      p {
        font-size: 16px;
        opacity: 0.8;
        margin-top: 0;
        margin-bottom: 0;
        width: 350px;
        height: 360px;
      }
      a {
        margin-top: 24px;
        width: 202px;
        margin-bottom: 46px;
        
      }
    }
  }
}

@media screen and (max-width: 1200px) {
  .home {
    header {
      width: 688px;
      background-image: url("../../public/images/homepage/mobile/image-homepage-hero@2x.jpg");
      background-size: cover;
      margin-bottom: 96px;
      .text-header {
        width: 514px;
        height: 278px;
        h1 {
          height: 126px;
          width: 458px;
          font-size: 40px!important;
          line-height: 42px!important;
        }
      }
    }
    #aboutMe {
      width: 689px;
      margin:auto;
      margin-bottom: 96px;
      .image-aboutMe {
        background-image: url("../../public/images/homepage/desktop/image-homepage-profile.jpg");
        background-size:cover;
        background-position: -212px;
        width: 281px;
      }
      .text-aboutMe {
        width: 339px;
        margin-left: 69px;
        p {
          width: auto;
        }
      }
    }
  }
}

@media screen and (max-width: 600px) {
  .home {
    header {
      width: 311px;
      height: 543px;
      background-image: url("../../public/images/homepage/mobile/image-homepage-hero.jpg");
      background-size: contain;
      background-repeat: no-repeat;
      margin-bottom: 96px;
      .text-header {
        width: auto;
        h1 {
          width: 314px;
          height: 168px;
          margin-top: 0;
          margin-bottom: 32px;
        }
      }
    }
    #aboutMe {
      width: 311px;
      height: 995px;
      flex-direction: column;
      margin-bottom: 115px;
      .image-aboutMe {
        background-image: url("../../public/images/homepage/desktop/image-homepage-profile.jpg");
        background-size: contain;
        background-repeat: no-repeat;
        width: auto;
        background-position: 0;
        margin-bottom: 17px;
      }
      .text-aboutMe {
        margin-left: 0;
        width: 311px;
        height: 617px;
        h2 {
          margin-top: 32px;
        }
        p {
          width: 311px;
          height: 390px;
        }
        a {
          margin-bottom: 51px;
        }
      }
    }
  }
}
</style>
