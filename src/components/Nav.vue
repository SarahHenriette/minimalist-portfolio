<template>
    <nav id="nav">
        <router-link to="/"><svg xmlns="http://www.w3.org/2000/svg" class="logo" width="61" height="32"><path fill="#33323D" fill-rule="evenodd" d="M60.082 5.878L44.408 32 28.735 5.878h31.347zM15.673 0l15.674 26.122H0L15.673 0z"/></svg></router-link>
        <ul id="nav-desktop">
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/portfolio">Portfolio</router-link></li>
            <li><router-link to="/contactUs">Contact us</router-link></li>
        </ul>
        <div id="nav-mobile">
            <svg v-if="displayIconBurger" xmlns="http://www.w3.org/2000/svg" @click="displayMenuBurger"  id="menu-burger" width="24" height="13"><g fill="#33323D" fill-rule="evenodd"><path d="M0 0h24v1H0zM0 6h24v1H0zM0 12h24v1H0z"/></g></svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" @click="hideMenuBurger" id="close" width="18" height="19"><path fill="#33323D" fill-rule="evenodd" d="M17.132.661l.707.707L9.707 9.5l8.132 8.132-.707.707L9 10.207.868 18.34l-.707-.707L8.293 9.5.161 1.368.868.661 9 8.793 17.132.661z"/></svg>
            <ul :class="menuBurger" class="menu-nav-mobile">
                <li @click="hideMenuBurger"><router-link to="/">Home</router-link></li>
                <li @click="hideMenuBurger"><router-link to="/portfolio">Portfolio</router-link></li>
                <li @click="hideMenuBurger"><router-link to="/contactUs">Contact us</router-link></li>
            </ul>
        </div>
    </nav>
</template>

<script>
export default {
    data () {
        return {
            displayIconBurger: true,
            menuBurger: ''
        }
    },
    methods: {
        displayMenuBurger () {
            this.menuBurger = "active"
            this.displayIconBurger = false
        },
        hideMenuBurger () {
            this.menuBurger = ""
            this.displayIconBurger = true
        }
    }
}
</script>

<style lang="scss" scoped>
@import './public/sass/colors.scss';

#nav {
    height: 32px;
    width: 1111px;
    top: 64px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 64px auto 54px auto;
    position: relative;
    top: 0;
    .logo {
        cursor: pointer;
    }
    #nav-desktop {
        display: flex;
        li a {
            margin-left: 43px;
            color: $grayishDarkBlue;
            transition: color ease .5s;
        }
    }
    #nav-mobile {
        display: none;
        position: absolute;
        right: 0;
        .menu-nav-mobile {
            display: none;
            position: absolute;
            top: 47px;
            right: 0;
            width: 223px;
            height: 186px;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            li {
                margin: 12px 0;
            }
            li a {
                color: $white;
                margin-left: 0;
            }
        }
        .active {
            display: flex;
            background-color: $grayishDarkBlue;
            animation: backgroundMenuMobile .5s linear;
            z-index: 20;
        }
        @keyframes backgroundMenuMobile {
            0% {background-color: transparent}
            100% {background-color: $grayishDarkBlue}
        }
    }
}

@media screen and (max-width: 1200px) {
    #nav {
        width: 689px;
        margin: 64px auto 47px auto;
    }
}

@media screen and (max-width: 600px) {
    #nav {
        width: 311px;
        margin: 32px auto 40px auto;
        #nav-desktop {
            display: none;
        }
        #nav-mobile {
            display: flex;
        }
    }
}
</style>