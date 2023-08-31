<template>
<div>
  <div v-if="createNew" class="card">
    <button @click="addNew" class="btn btn-secondary mt-2">create new</button>
  </div>
  <div v-else-if="editing" class="card">
    <textarea v-model="editedText" rows="4" class="form-control"></textarea>
    <div class="input-group input-group-lg" v-for="socialNetwork in this.listOfNetworks" v-bind="socialNetwork">
      <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-default" v-html="socialNetwork.icon">
        </span>
      </div>
      <input type="text" class="form-control" aria-label="Large" aria-describedby="inputGroup-sizing-sm" v-model="this.valuesOfSocialNetworkList[socialNetwork.title]">
    </div>

    <button @click="saveEdit" class="btn btn-primary mt-2">Save</button>
    <button @click="cancelEdit" class="btn btn-secondary mt-2">Cancel</button>
  </div>
  <div v-else class="card">

    <div class="dropdown" align="right">
      <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-three-dots-vertical" viewBox="0 0 16 16">
          <path d="M9.5 13a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"/>
        </svg>
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" @click="startEdit">Edit</a></li>
        <li><a class="dropdown-item" href="#">Delete</a></li>
      </ul>
    </div>
    <h5 class="card-title">{{ cardTitle }}</h5>
    <p class="card-text">Last update: {{ lastUpdate }}</p>

    <div class="card-text" v-for="(value, key) in this.valuesOfSocialNetworkList" :key="key">
      <div class="input-group input-group-lg">
        <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-default" v-html="listOfNetworks.find(network => network.title === key).icon">
        </span>
        </div>
        {{value}}
      </div>
    </div>

  </div>
</div>
</template>

<script>
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
  name: "ContactObject",
  props: {
    id: Number,
    createNew: Boolean
  },
  data() {
    return {
      editing: false,
      editedText: "",
      cardTitle: "Title",
      lastUpdate: "28.08.2023 5:22",
      valuesOfSocialNetworkList: {

      }
    };
  },

  mounted() {
    console.log(this.createNew === 0)
    console.log(this.editing === 0)
    if (this.createNew === false && this.editing === false) {
      console.log("create new")
      this.getInformationAboutContact();
    }
  },
  methods: {
    startEdit() {
      this.editing = true;
      this.editedText = this.cardTitle;
    },
    saveEdit() {
      this.cardTitle = this.editedText;
      this.editing = false;
      this.saveChanges();
    },
    cancelEdit() {
      this.editing = false;
    },
    createNewCard() {

    },
    getListOfAllContacts(){
      var result = (document.cookie.match(new RegExp("listOfAllContacts" + '=([^;]+)')) || [])[1] && JSON.parse((document.cookie.match(new RegExp("listOfAllContacts" + '=([^;]+)')) || [])[1]) || [];
      console.log(result);
      return result;
    },
    addNew(){
      var listOfAllContacts = this.getListOfAllContacts();
      listOfAllContacts.push({id:listOfAllContacts.length, valuesOfSocialNetworkList: this.valuesOfSocialNetworkList});
      document.cookie = "listOfAllContacts" + "=" + JSON.stringify(listOfAllContacts) + "; path=/";
    },
    saveChanges(){
      var listOfAllContacts = this.getListOfAllContacts();
      listOfAllContacts[this.id]["valuesOfSocialNetworkList"]= this.valuesOfSocialNetworkList;
      listOfAllContacts[this.id]["cardTitle"]= this.cardTitle;
      document.cookie = "listOfAllContacts" + "=" + JSON.stringify(listOfAllContacts) + "; path=/";
    },
  getInformationAboutContact(){
    this.valuesOfSocialNetworkList = this.getListOfAllContacts().filter(contact => contact.id === this.id)[0]["valuesOfSocialNetworkList"];
    this.cardTitle = this.getListOfAllContacts().filter(contact => contact.id === this.id)[0]["cardTitle"];
  },
  },
}
</script>

<style scoped>
/* Custom styling for the card */
.card {
  width: 300px;
  margin: 20px;
  border: none;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  background-size: cover;
}
.card-title {
  font-size: 24px;
  font-weight: bold;
  margin-top: 10px;
}
.card-text {
  font-size: 14px;
}
</style>

