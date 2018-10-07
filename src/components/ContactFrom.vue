<template lang="pug">
    .contact-form
      .contact-form__contener
        .contact-form__header
            h2.contact-form__title Contact Us
        .contact-form__wrapper
            .contact-form__box
                form.contact-form__form( v-on:submit.prevent="submit" )
                    .contact-form__col-cont
                        .contact-form__left-col
                            .contact-form__row(v-bind:class="{'contact-form__row--error': $v.userName.$error }")
                                .contact-form__label-wrap
                                    label(for="userName") Name
                                .contact-form__input-wrap
                                    input(type="text" id="userName" v-model.trim="$v.userName.$model")
                                .contact-form__row-message(v-if="$v.userName.$error") Please enter Name

                            .contact-form__row(v-bind:class="{'contact-form__row--error': $v.phone.$error }")
                                .contact-form__label-wrap
                                    label(for="phone") Phone
                                .contact-form__input-wrap
                                    input(type="text" id="phone" v-model.trim="$v.phone.$model")
                                .contact-form__row-message(v-if="$v.phone.$error") Please enter correct phone

                            .contact-form__row(v-bind:class="{'contact-form__row--error': $v.email.$error }")
                                .contact-form__label-wrap
                                    label(for="email") E-mail
                                .contact-form__input-wrap
                                    input(type="email" id="email" v-model.trim="$v.email.$model")
                                .contact-form__row-message(v-if="$v.email.$error") Please enter correct email
                        .contact-form__right-col
                            .contact-form__row-text(v-bind:class="{'contact-form__row--error': $v.text.$error}")
                                textarea(v-model.trim="$v.text.$model" placeholder="Please tell us more about your request and give us info about your company and country")
                                .contact-form__row-message(v-if="$v.text.$error") Text is required

                    .contact-form__row-agree
                        .contact-form__checkbox-wrap
                            input(type="checkbox" id="agree" name="agree" v-model="$v.agree.$model")
                        .contact-form__ch-label-wrap
                            label(for="agree") I agree the processing of personal data
                        .contact-form__row-message(v-if="$v.agree.$error") Must agree the processing of personal data

                    .contact-form__row-button
                      button(type="submit" :disabled="submitStatus === 'PENDING'" :class="{active:submitStatus === 'PENDING'}") Get in touch
</template>

<script>
import { required, email, numeric } from 'vuelidate/lib/validators'

const bolltest = (value) => !!value
export default {
  name: 'contact-from',
  data () {
    return {
      userName: '',
      phone: '',
      email: '',
      agree: true,
      submitStatus: null,
      text: ''
    }
  },
  methods: {
    async submit () {
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        this.submitStatus = 'PENDING'
        const message = {
          userName: this.userName,
          phone: this.phone,
          email: this.email,
          text: this.text
        }
        fetch('http://httpbin.org/post', {
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
          method: 'POST',
          body: JSON.stringify(message)
        })
          .then(res => {
            this.submitStatus = 'OK'
            return res.json()
          })
          .then(res => console.log(res))
      }
    }
  },
  validations: {
    userName: {
      required
    },
    email: {
      required,
      email
    },
    phone: {
      required,
      numeric
    },
    agree: {
      bolltest
    },
    text: {
      required
    }
  }
}
</script>
