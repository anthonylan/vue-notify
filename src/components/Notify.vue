<template>
  <div class="home">
    <div class="container">
      <h1 v-bind:class="{change: changed}">Vue Notify</h1>
        <button @click="notifyL">Notify Left</button>
        <button @click="notifyR">Notify Right</button>
        <a href="https://github.com/anthonylan/vue-notify">Make it better on github</a>
    </div>
 <!-- Left Notification -->
    <div class="notify left">
      <ul>
        <transition-group name="fade" enter-active-class="animated fadeInUp" leave-active-class="animated fadeOutDown">
        <li v-for="(data, index) in notifyLeft" :key="data">
          {{data}}
          <span @click="removeL(index)">dismiss</span>
        </li>
        </transition-group>
      </ul>
    </div>

    <!-- Right Notification -->
    <div class="notify right">
      <ul>
        <transition-group name="fade" enter-active-class="animated fadeInRight" leave-active-class="animated fadeOutRight">
        <li v-for="(data, index) in notifyRight" :key="data">
          {{data}}
          <span @click="removeR(index)">dismiss</span>
        </li>
        </transition-group>
      </ul>
    </div>


        <div class="block-sm">
          <h2>Sorry!</h2>
          <p>We don't have support for this screen size</p>
        </div>

  </div>
</template>

<script>
export default {
  name: 'Notify',
  data(){
    return{
      notifyRight:[],
      notifyLeft:[],

      //Change Heading color
      changed: false
    }
  },
  methods:{
    //Left notify function
    notifyL(){
      this.notifyLeft.push('A simple notification made with vue')
    },
     removeL(id){
      this.notifyLeft.splice(id, 1)
    },
    
    //Right notify function
      notifyR(){
      this.notifyRight.push('A simple notification made with vue')
    },
    removeR(id){
      this.notifyRight.splice(id, 1)
    },
    
  },
  mounted(){
    //Interval for heading color
    setInterval(() => {
     if(this.changed == false){
       this.changed = true
     }else{
       this.changed = false
     }
    }, 8000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.0/animate.min.css');
:root{
  --main-color: #ff5252;
  --primary: #448aff;
}
h1 {
  color: #448aff;
  font-weight: 300;
  margin: 10rem 0 2rem 0;
  font-size: 7rem;
}
@media (max-width:550px) {
  h1, button{
    display: none !important;
  }
  .block-sm{
    width: 100%;
    height: 100vh;
    z-index: 100;
  }
}
@media (min-width:550px) {
  .block-sm{
    display: none;
  }
}
.change{
  color: #ff5252;
  transition: all .5s ease-in-out;
}
button{
  display: inline-block;
  background: #26a69a;
  color: #fff;
  text-transform: uppercase;
  border: none;
  border-radius: 3px;
  padding: 1rem 1.2rem;
  margin: .5rem;
  cursor: pointer;
  outline: none;
  box-shadow: 0 10px 10px -4px #eaeded;
}






/*VUE NOTIFY STYLES*/
.notify {
  position: fixed;
  bottom: 0;
  z-index: 10;
}
.left{
  left: 2rem;
}
.right{
  right: 4rem;
}
li {
  list-style: none;
  display: block;
  padding: 1rem;
  background: #323232;
  margin: 1rem 0;
  color: #fff;
  text-align: left;
  text-transform: none;
  max-width: 500px;
}
span{
  color: #ff5252;
  float: right;
  padding-left: 1rem;
  text-transform: uppercase;
}







</style>
