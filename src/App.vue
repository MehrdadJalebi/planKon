<template>
  <div id="app">
    <header>پلن کن !</header>
    <div class="container">
      <div class="person-list" v-for="(person, index) in persons" :key="index">
      {{person.name}} - {{person.date}}
      </div>
      <input type="text" v-model="name" :class="dir" placeholder="نام">
      <date-picker
        inputClass="datepicker"
        type="datetime"
        format="YYYY-MM-DD HH:mm:ss"
        display-format="dddd jDD jMMMM jYYYY"
        placeholder="تاریخ"
        v-model="date"></date-picker>
      <button class="button" @click="addPerson">افزودن</button>
    </div>
  </div>
</template>

<script>

import VuePersianDatetimePicker from 'vue-persian-datetime-picker'
export default {
  name: 'App',
  components: {
    datePicker: VuePersianDatetimePicker
  },
  data() {
    return {
      dir: 'rtl',
      name:'',
      date: '',
      persons: [],
    }
  },
  methods: {
    addPerson () {
      if (this.name){
        this.persons.push({name: this.name, date: this.date})
        this.name = null
        this.date = null
      }
    }
  }
}
</script>

<style lang='scss'>
  @import './sass/main';
</style>
