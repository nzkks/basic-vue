<template>
  <div class="test">
    <div v-html="title"></div>

    <p v-if="showName">{{user.firstName}} {{user.lastName}}</p>
    <p v-else="showName">Nobody</p>

    <p v-text="user.firstName"></p>

    <input type="text" v-model="jobTitle"> {{jobTitle}}

    <ul>
      <li v-for="item in items">{{item.title}}</li>
    </ul>

    <button v-on:click="greet('Hello World')">Say Greeting</button>
    <br /><br />

    Enter few characters / press 'enter' key and see the console. <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterKeyHit">
    <br /><br />

    <label for="firstName">First Name</label> <input type="text" name="firstName" v-model="user.firstName">
    <label for="lastName">Last Name</label> <input type="text" name="lastName" v-model="user.lastName">
    <h3>{{fullName}}</h3>
    <h2>{{msg}}</h2>
  </div>
</template>

<script>
export default {
  name: 'test',
  props: {
    msg: {
      type: String,
      default: 'Foobar'
    }
  },
  data() {
    return {
      title: '<h1>Hello World</h1>',
      jobTitle: 'Web Developer',
      user: {
        firstName: 'John',
        lastName: 'Doe'
      },
      showName: true,
      items: [
        {title: 'Item One'},
        {title: 'Item Two'},
        {title: 'Item Three'}
      ]
    }
  },
  methods: {
    greet: function(greeting){
      alert(greeting);
    },
    pressKey: function(e){
      console.log('pressed: ' + e.target.value);
    },
    enterKeyHit: function(){
      console.log('Enter key pressed');
    }
  },
  computed: {
    fullName: function(){
      return this.user.firstName + ' ' + this.user.lastName;
    }
  }
}
</script>

<style scoped>

</style>
