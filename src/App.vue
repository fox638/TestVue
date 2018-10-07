<template>

    <div>
      <Contacts/>
      <Offices/>
      <ContactForm />
    </div>
</template>

<script>
import Contacts from './components/Contacts.vue'
import Offices from './components/Offices.vue'
import ContactForm from './components/ContactFrom.vue'
export default {
  name: 'App',
  components: {
    Contacts,
    Offices,
    ContactForm
  }
}
</script>

<style lang="scss">

</style>
