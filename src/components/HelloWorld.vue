<template>
  <div class="hello">
    <input name="nama" v-model="msg">
    <input name="age" v-model.number="profile.age">
    <h1 v-show="isShowName">Hai, <strong>{{ msg }}</strong></h1>
    <h3>{{ getMyAddress }}</h3>
    <h4><a :href="facebookURL" :title="title">Facebook Url</a></h4>
    <h5>Sekarang umur {{ getMyAge }} Tahun depan berumur {{ profile.age + 1 }} tahun & saya  {{ address.office ? 'bekerja' : 'tidak bekerja' }}</h5>
    <h5>
      <span v-if="false">If pertama</span>
      <span v-else-if="false">Else if Here</span>
      <span v-else="true">Im else</span>
    </h5>
    <p>
      <ul>
        <li v-for="todo in todos">{{ todo.name }}</li>
      </ul>
    </p>
    <hr>
    <button :disabled="isDisabled" v-on:click="showPopup(false)">Klik aku dong</button>
    <button @click="showName">toggle name</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Prima Muhamad Rasyid",
      address: {
        home: 'Jln. Ibrahim Adjie',
        office: 'Jln. Tubagus Ismail'
      },
      profile: {
        age: 999
      },
      facebookURL: 'https://fb.com/prima.muhamadrasyid',
      title: 'Facebook Url',
      isDisabled: false,
      isShowName: true,
      todos: [
        { name: 'Raisa' },
        { name: 'Isyana' }
      ]
    };
  },
  methods: {
    showPopup(condition){
      condition ? alert('Hai Prima') : alert('Who you are?')
    },
    meh(){
      alert('Meh :D')
    },
    showName(){
      this.isShowName = !this.isShowName
    }
  },
  computed: {
    getMyAge(){
      return this.profile.age
    },
    getMyAddress(){
      let { home, office } = this.address
      return home + ' & ' + office
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
