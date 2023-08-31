<template>
  <div class="home">
    <div id="myCarousel" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item active" v-for="contact in this.listOfPublication">
          <ContactObject :id="contact.id"></ContactObject>
        </div>
        <div :class="this.listOfPublication.length===0 ? 'carousel-item active' : 'carousel-item'">
          <ContactObject :create-new="true" @updateListOfAllContacts="updateListOfAllContacts"></ContactObject>
        </div>

        <!--        <div class="carousel-item">-->
<!--          <ContactObject :id="1"></ContactObject>-->

<!--        </div>-->
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#myCarousel" data-bs-slide="prev">
<!--        <span class="carousel-control-prev-icon" aria-hidden="true"></span>-->
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#myCarousel" data-bs-slide="next">
<!--        <span class="carousel-control-next-icon" aria-hidden="true"></span>-->
        <span class="visually-hidden">Next</span>
      </button>
    </div>
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ContactObject from "@/components/ContactObject";
export default {
  name: 'HomeView',
  components: {
    ContactObject,
    HelloWorld
  },
  data() {
    return {
      listOfPublication: this.getListOfAllContacts(),
    };
  },
  methods:{
    getListOfAllContacts(){
      console.log("getListOfAllContacts")
      var result = (document.cookie.match(new RegExp("listOfAllContacts" + '=([^;]+)')) || [])[1] && JSON.parse((document.cookie.match(new RegExp("listOfAllContacts" + '=([^;]+)')) || [])[1]) || [];
      console.log(result);
      return result;
    },
    updateListOfAllContacts(){
      console.log("updateListOfAllContacts")
      this.listOfPublication = this.getListOfAllContacts();
    }
  }

}
</script>
