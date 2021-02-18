<template>
    <div class="contact">
        <section class="get-in-touch">
            <h2>Get in Touch</h2>
            <article>
                <p>I’d love to hear about what you’re working on and how I could help. I’m currently looking for a new role and am open to a wide range of opportunities. My preference would be to find a position in a company in London. But I’m also happy to hear about opportunites that don’t fit that description. I’m a hard-working and positive person who will always approach each task with a sense of purpose and attention to detail. Please do feel free to check out my online profiles below and get in touch using the form.</p>
                <div class="icon">
                    <svg xmlns="http://www.w3.org/2000/svg" width="25" height="24"><path fill="#33323D" d="M12.5 0C5.594 0 0 5.51 0 12.305c0 5.437 3.581 10.048 8.547 11.674.625.116.854-.265.854-.592 0-.292-.01-1.066-.016-2.092-3.477.742-4.21-1.65-4.21-1.65-.569-1.42-1.39-1.8-1.39-1.8-1.133-.764.087-.748.087-.748 1.255.086 1.914 1.268 1.914 1.268 1.115 1.881 2.927 1.338 3.641 1.024.113-.797.434-1.338.792-1.646-2.776-.308-5.694-1.366-5.694-6.08 0-1.343.484-2.44 1.286-3.302-.14-.31-.562-1.562.11-3.256 0 0 1.047-.33 3.437 1.261 1-.273 2.063-.409 3.125-.415 1.063.006 2.125.142 3.125.415 2.375-1.591 3.422-1.261 3.422-1.261.672 1.694.25 2.945.125 3.256.797.861 1.281 1.959 1.281 3.302 0 4.727-2.921 5.767-5.703 6.07.438.369.844 1.123.844 2.276 0 1.647-.016 2.97-.016 3.37 0 .322.22.707.86.584 5-1.615 8.579-6.23 8.579-11.658C25 5.509 19.403 0 12.5 0z"/></svg>
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="20"><path fill="#33323D" d="M24 2.557a9.83 9.83 0 01-2.828.775A4.932 4.932 0 0023.337.608a9.864 9.864 0 01-3.127 1.195A4.916 4.916 0 0016.616.248c-3.179 0-5.515 2.966-4.797 6.045A13.978 13.978 0 011.671 1.149a4.93 4.93 0 001.523 6.574 4.903 4.903 0 01-2.229-.616c-.054 2.281 1.581 4.415 3.949 4.89a4.935 4.935 0 01-2.224.084 4.928 4.928 0 004.6 3.419A9.9 9.9 0 010 17.54a13.94 13.94 0 007.548 2.212c9.142 0 14.307-7.721 13.995-14.646A10.025 10.025 0 0024 2.557z"/></svg>
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"><path fill="#33323D" d="M21.6 0H2.4C1.08 0 0 1.08 0 2.4v19.2C0 22.92 1.08 24 2.4 24h19.2c1.32 0 2.4-1.08 2.4-2.4V2.4C24 1.08 22.92 0 21.6 0zM7.2 20.4H3.6V9.6h3.6v10.8zM5.4 7.56c-1.2 0-2.16-.96-2.16-2.16 0-1.2.96-2.16 2.16-2.16 1.2 0 2.16.96 2.16 2.16 0 1.2-.96 2.16-2.16 2.16zm15 12.84h-3.6v-6.36c0-.96-.84-1.8-1.8-1.8-.96 0-1.8.84-1.8 1.8v6.36H9.6V9.6h3.6v1.44c.6-.96 1.92-1.68 3-1.68 2.28 0 4.2 1.92 4.2 4.2v6.84z"/></svg>
                </div>
            </article>
        </section>
        <section class="contact-me">
            <h2>Contact Me</h2>
            <form action="" @submit.prevent="submitForm" novalidate>
                <label for="name">Name</label>
                <input type="text" name="name" id="name" placeholder="Jane Appleseed"  v-model="name.value" @focus="focusInput" :class="name.error">
                <div :class="name.error" v-if="name.errorMessage.length > 0"><span v-for="message in name.errorMessage" :key="message">{{ message }}</span></div>

                <label for="email">Email Address</label>
                <input type="email" name="email" id="email" placeholder="email@example.com"  v-model="email.value" @focus="focusInput" :class="email.error">
                <div :class="email.error" v-if="email.errorMessage.length > 0"><span v-for="message in email.errorMessage" :key="message">{{ message }}</span></div>

                <label for="message">Message</label>
                <textarea name="message" id="message" cols="30" rows="10" placeholder="How can I help?"  v-model="message.value" @focus="focusInput" :class="message.error"></textarea>
                <div :class="message.error" v-if="message.errorMessage.length > 0"><span v-for="message in message.errorMessage" :key="message">{{ message }}</span></div>

                <input type="submit" value="send message" class="btn-submit">
            </form>
        </section>
        <Footer/>
    </div>
</template>

<script>
import Footer from '../components/ContactFooter'

export default {
    components: {
        Footer
    },
    data () {
        return {
            name: {
                value: "",
                error: "",
                errorMessage: []
            },
            email: {
                value: "",
                error: "",
                errorMessage: []
            },
            message: {
                value: "",
                error: "",
                errorMessage: []
            },
        }
    },
    methods: {
        submitForm() {

            this.verifyInputEmpty(this.name)
            this.verifyInputEmpty(this.email)
            this.verifyInputEmpty(this.message)
            

            if(this.name.value !== "" && this.email.value !== "" && this.message.value !== "" && this.verifyValidEmail()) {
                alert('Votre message à bien été envoyé')
                this.name.value = ""
                this.email.value= ""
                this.message.value = ""
            }
        },
        verifyInputEmpty(variable) {
        variable.errorMessage = []
        if(!variable.value){
          variable.error = "error"
          variable.errorMessage.push("This field is required")
        }
      },
      focusInput(e){
        this.actionFocusInput(e, "name", this.name)
        this.actionFocusInput(e, "email", this.email)
        this.actionFocusInput(e, "message", this.message)
      }, 
      actionFocusInput(e, value, variable){
        if(e.target.name == value) {
          variable.errorMessage = ""
          variable.error = ""
        }
      },
      verifyValidEmail() {
        let emailValid = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
        if(emailValid.test(this.email.value) ) {
          return true
        }
        this.email.errorMessage.push("This address is not valid")
        this.email.error = "error"
      }
    }
}
</script>

<style lang="scss" scoped>
@import './public/sass/colors.scss';

.contact {
    padding-top: 43px;
    .get-in-touch {
        width: 1110px;
        margin: auto;
        height: 354px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-top: 1px solid #DCDCDE;
        border-bottom: 1px solid #DCDCDE;
        margin-bottom: 47px;
        h2 {
            width: 350px;
            height: 258px;
            margin: 0;
        }
        article {
            width: 635px;
            height: 258px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            p {
                width: 100%;
                height: 210px;
                margin: 0;
                opacity: 0.8;
            }
            .icon {
                width: 100%;
                height: 24px;
                svg {
                    margin-right: 15px;
                    cursor: pointer;
                }
            }
        }
    }
    .contact-me {
        width: 1110px;
        margin: auto;
        height: 426px;
        display: flex;
        justify-content: space-between;
        margin-bottom: 109px;
        h2 {
            width: 350px;
            height: 100%;
            margin: 0;
        }
        form {
            width: 635px;
            height: 426px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            label {
                width: 100%;
                height: 30px;
            }
            input {
                width: 90%;
                height: 48px;
                background-color: #ECEBED;
                border-color: transparent;
                padding: 0  16px;
                &::placeholder {
                    color: #33323D;
                    opacity: 0.4;
                }
                &:focus {
                    outline: none;
                    border: 1px #5FB4A2 solid;
                }
            }
            input.error {
                border: 1px #F43030 solid;
            }
            textarea {
                width: 90%;
                height: 96px;
                background-color: #ECEBED;
                border-color: transparent;
                padding: 9px 16px;
                
                    &::placeholder {
                    color: #33323D;
                    opacity: 0.4;
                }
                    &:focus {
                    outline: none;
                    border: 1px #5FB4A2 solid;
                }
            }
            textarea.error {
                border: 1px #F43030 solid;
            }
            .error {
                font-family: 'Livvic', sans-serif;
                font-style: italic;
                font-weight: bold;
                font-size: 10px;
                line-height: 13px;
                color: #F43030;
                span {
                margin-right: 5px;
                }
            }
            .btn-submit {
                width: 200px;
                height: 48px;
                background-color: $darkBlue;
                color: $white;
                font-size: 12px;
                font-weight: 400;
                text-transform: uppercase;
                margin-top: 24px;
                letter-spacing: 2px;
                cursor: pointer;
            }
        }
    }
}

@media screen and (max-width: 1200px) {
    .contact {
        .get-in-touch {
            width: 689px;
            height: 388px;
            flex-direction: column;
            align-items: flex-start;
            h2 {
                width: 281px;
                height: 42px;
                margin-top: 32px;
                margin-bottom: 24px;
            }
            article {
                margin-bottom: 32px;
            }
            article p {
                margin-bottom: 24px;
                width: 689px;
                height: 180px;
            }
        }
        .contact-me {
            height: 500px;
            h2 {
                width: 281px;
                height: 42px;
            }
            width: 689px;
            flex-direction: column;
            form {
                width: 689px;
                margin-top: 32px;
            }
        }
    }
}

@media screen and (max-width: 600px) {
    .contact {
        .get-in-touch {
            width: 311px;
            height: auto;
            margin-bottom: 0;
            h2 {
                width: 311px;
                margin-top: 24px;
            }
            article {
                width: 311px;
                height: 433px;
            }
            article p {
                margin-bottom: 24px;
                width: 311px;
                height: 386px;
            }
        }
        .contact-me {
            width: 311px;
            height: 492px;
            h2 {
                width: 311px;
                margin-top: 32px;
            }
            form {
                width: 311px;
                height: 426px;
                margin-top: 24px;
            }
        }
    }
}
</style>