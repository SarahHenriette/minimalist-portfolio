<template>
    <nav class="pagination" >
        <li class="previous" @click="previousProject">
            <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="10" height="16"><path fill="none" stroke="#33323D" d="M9 0L1 8l8 8"/></svg></a>
            <div class="text">
                <h3>Fylo</h3>
                <p>Previous Project</p>
            </div>
        </li>
        <li class="next" @click="nextProject">
            <div class="text">
                <h3>Bookmark</h3>
                <p>Next Project</p>
            </div>
            <a href="#" ><svg xmlns="http://www.w3.org/2000/svg" width="10" height="16"><path fill="none" stroke="#33323D" d="M1 0l8 8-8 8"/></svg></a>
        </li>
    </nav>
</template>

<script>
import portfolioJson from '../../src/assets/portfolio.json'

export default {
    data () {
        return {
            portfolio : portfolioJson,  
            first: this.$route.query.id - 1,
            nbrItem: 1,
            data: [],        
        }
    },
    
    methods: {
        displayItem() {
            for (let index = this.first; index < (this.first + this.nbrItem); index++) {
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
            console.log('next')
            console.log(this.first)
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

    @media screen and (max-width: 1200px) {
        .pagination {
            width: 691px;
            height: 132px;
        }
    }

    @media screen and (max-width: 600px) {
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
</style>