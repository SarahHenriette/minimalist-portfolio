<template>
    <div class="projet">
        <header >
            <img :src= data.imageDetailHeader alt="header du projet">
        </header>
        <main>
            <section class="infos-projet">
                <div class="line"></div>
                <h2>{{ data.title }}</h2>
                <p class="description-infos-projet">{{ data.description }}</p>
                <p class="important-info">Interaction Design/Front End Development</p>
                <p class="info-techno important-info">{{ data.techno }}</p>
                <a href="#" class="btn-secondary">visit website</a>
                <div class="line"></div>
            </section>
            <section class="infos-projet-tablet">
                <div class="line"></div>
                <div class="info-title">
                    <h2>{{ data.title }}</h2>
                    <p class="important-info">Interaction Design/Front End Development</p>
                    <p class="info-techno important-info">{{ data.techno }}</p>
                    <a href="#" class="btn-secondary">visit website</a>
                </div>
                <div class="info-text">
                    <p class="description-infos-projet">{{ data.description }}</p>
                </div>
                <div class="line"></div>
            </section>
            <section class="presentation-projet">
                <article class="projet-background">
                    <h3>Project Background</h3>
                    <p>This project was a front-end  challenge from Frontend Mentor. It’s a platform that enables you to practice building websites to a design and project brief. Each challenge includes mobile and desktop designs to show how the website should look at different screen sizes. Creating these projects has helped me refine my workflow and solve real-world coding problems. I’ve learned something new with each project, helping me to improve and adapt my style.</p>
                </article>
                <div class="static-previews">
                    <h3>Static Previews</h3>
                    <div class="img-static-previews-top">
                        <img :src= data.imageDetailTop alt="">
                    </div>
                    <div class="img-static-previews-bottom">
                        <img :src= data.imageDetailBottom alt="">
                    </div>
                </div>
            </section>
        </main>
        <nav class="pagination" >
            <li class="previous" @click="previousProject">
                <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="10" height="16"><path fill="none" stroke="#33323D" d="M9 0L1 8l8 8"/></svg></a>
                <div class="text">
                    <h3>{{ namePreviousProject }}</h3>
                    <p>Previous Project</p>
                </div>
            </li>
            <li class="next" @click="nextProject">
                <div class="text">
                    <h3 >{{ nameNextProject }}</h3>
                    <p>Next Project</p>
                </div>
                <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="10" height="16"><path fill="none" stroke="#33323D" d="M1 0l8 8-8 8"/></svg></a>
            </li>
        </nav>
        <Footer/>
    </div>
</template>
    

<script>
import Footer from '../components/Footer'
import portfolioJson from '../../src/assets/portfolio.json'

export default {
    static: {
        visibleItemsPerPageCount: 1
    },
    components: {
        Footer
    },
    data (){
        return {
            data: [],
            nbrItem: 1,
            first: this.$route.query.id - 1,
            portfolio : portfolioJson,
            nameNextProject: "",
            namePreviousProject: ""

        }
    },
    async mounted () {
        this.displayItem()
    }, 
    methods: {
        displayItem() {
            for (let index = this.first; index < (this.first + this.nbrItem); index++) {
                if(index == 3) {
                    this.nameNextProject =this.portfolio.images[0].title
                }else {
                    this.nameNextProject = this.portfolio.images[index+1].title
                }            
                if(index == 0) {
                    this.namePreviousProject = this.portfolio.images[this.portfolio.images.length-1].title
                }else {
                    this.namePreviousProject = this.portfolio.images[index-1].title
                }
                 
             return this.data = this.portfolio.images[index];
            }
        },
        previousProject() {
            this.first -= this.nbrItem
            if(this.first== -1) {
                this.first = 3
            }
            this.displayItem()
        },
        nextProject() {
      
            this.first += this.nbrItem
            if(this.first== this.portfolio.images.length) {
                this.first = 0
            }
            this.displayItem()
        }
    }
}
</script>

<style lang="scss" scoped>
@import './public/sass/colors.scss';

.projet {
    padding-top: 43px;

    header {
        width: 1110px;
        height: 500px;
        margin: auto;
        margin-bottom: 115px;

        img {
            width: 100%
        }
    }

    main {
        width: 1110px;
        height: 1192px;
        display: flex;
        justify-content: space-between;
        margin: auto;
        margin-bottom: 64px;

        .infos-projet {
            width: 350px;
            height: 498px;

            h2 {
                margin-top: 48px;
                margin-bottom: 29px;
            }

            p {
                margin: 0;
            }

            .description-infos-projet {
                width: 350px;
                height: 150px;
                margin-top: 0;
                margin-bottom: 23px;
                font-size: 15px;
            }

            .info-techno {
                margin-top: 16px;
                margin-bottom: 32px;
            }

            .important-info {
                font-size: 15px;
                color: $greenSlightly;
                font-weight: 700 !important;
            }

            a {
                width: 178px !important;
                margin-bottom: 48px;
            }
        }

        .infos-projet-tablet {
            display: none;
        }

        .presentation-projet {
            width: 635px;
            height: 1192px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;

            .projet-background {
                width: 635px;
                height: 250px;
                display: flex;
                flex-direction: column;
                justify-content: space-between;

                h3,
                p {
                    margin: 0;
                }

                p {
                    width: 635px;
                    height: 180px;
                    font-size: 15px;
                }
            }

            .static-previews {
                width: 635px;
                height: 902px;
                display: flex;
                flex-direction: column;
                justify-content: space-between;

                h3 {
                    margin: 0;
                }

                .img-static-previews-top,
                .img-static-previews-bottom {
                    width: 635px;
                    height: 400px;

                    img {
                        width: 100%;
                    }
                }
            }
        }
    }

    .pagination {
        width: 1110px;
        height: 132px;
        display: flex;
        margin: auto;
        border-top: 1px solid #DCDCDE;
        border-bottom: 1px solid #DCDCDE;
        margin-bottom: 115px;

        .previous,
        .next {
            width: 50%;
            display: flex;
            align-items: center;
            cursor: pointer;

            div h3,
            div p {
                margin: 0;
            }

            div p {
                font-size: 16px;
                opacity: 0.5;
            }
        }

        .previous {
            justify-content: flex-start;
            border-right: 1px solid #DCDCDE;

            a svg {
                margin-right: 32px;
            }
        }

        .next {
            justify-content: flex-end;

            a svg {
                margin-left: 32px;
            }

            .text {
                text-align: end;
            }
        }
    }
}

@media screen and (max-width: 1200px) {
    .projet {
        header {
            width: 689px;
            height: 310px;
            margin-bottom: 40px;
        }

        main {
            flex-direction: column;
            width: 689px;
            height: 1529px;

            .infos-projet {
                display: none;
            }

            .infos-projet-tablet {
                width: 689px;
                height: 248px;
                display: flex;
                justify-content: space-between;
                align-items: center;
                margin: auto;
                border-top: 1px solid #DCDCDE;
                border-bottom: 1px solid #DCDCDE;
                margin-bottom: 40px;

                .info-title {
                    width: 338px;
                    height: 182px;

                    h2 {
                        margin-bottom: 16px;
                        margin-top: 0;
                    }

                    p {
                        margin: 0;
                    }

                    .info-techno {
                        margin-bottom: 16px;
                    }

                    .important-info {
                        font-size: 13px;
                        color: $greenSlightly;
                        font-weight: 700 !important;
                    }
                }

                .info-text {
                    width: 339px;
                    height: 182px;

                    p {
                        margin: 0;
                    }
                }
            }

            .presentation-projet {
                width: 689px;
                height: 1241px;

                .projet-background {
                    width: 688px;
                    height: 220px;

                    p {
                        width: 688px;
                        height: 150px;
                    }
                }

                .static-previews {
                    width: 689px;
                    height: 981px;
                    margin-top: 40px;

                    .img-static-previews-top,
                    .img-static-previews-bottom {
                        width: 689px;
                        height: 434px;
                    }
                }
            }
        }

        .pagination {
            width: 691px;
            height: 132px;
        }
    }
}

@media screen and (max-width: 600px) {
    .projet {
        padding-top: 0;

        header {
            width: 311px;
            height: 140px;
        }

        main {
            width: 313px;
            height: 1451px;

            .infos-projet {
                display: block;
                width: 311px;
                height: 452px;
                margin: 0 auto 48px auto;

                h2 {
                    margin-top: 24px;
                }

                .description-infos-projet {
                    width: 311px;
                    height: 180px;
                }

                .info-techno {
                    margin-top: 0;
                    margin-bottom: 24px;
                }

                a {
                    margin-bottom: 24px;
                }
            }

            .infos-projet-tablet {
                display: none;
            }

            .presentation-projet {
                width: 313px;
                height: 948px;

                .projet-background {
                    width: 311px;
                    height: 400px;

                    p {
                        width: 311px;
                        height: 330px;
                    }

                    h3 {
                        margin-bottom: 28px;
                    }
                }

                .static-previews {
                    width: 313px;

                    .img-static-previews-top,
                    .img-static-previews-bottom {
                        width: 313px;
                        height: 197px;
                    }
                }
            }
        }

        .pagination {
            width: 326px;
            height: 148px;

            .previous {
                align-items: flex-start;
                flex-direction: column;
                justify-content: center;

                a {
                    margin-bottom: 16px;
                }
            }

            .next {
                align-items: flex-end;
                flex-direction: column-reverse;
                justify-content: center;

                a {
                    margin-bottom: 16px;
                }
            }
        }
    }
}
</style>