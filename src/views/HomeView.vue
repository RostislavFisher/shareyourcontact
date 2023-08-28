<template>
  <div class="home">

    <div class="waveStrength-3">
      <div class="wv3 wave" style="">
        <div class="wv2 wave" style="">
          <div class="wv1 wave">
          </div>
        </div>
      </div>
    </div>

    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>

.waveStrength-3{
  /*transform: rotate(90deg);*/
  margin-left: auto;
  margin-right: auto;

}

.wave {
  display: inline-block;
  border: 25px solid transparent;
  border-top-color: currentColor;
  border-radius: 50%;
  border-style: solid;
  margin: 5px;
}


.waveStrength-3 .wv4.wave,
.waveStrength-2 .wv4.wave,
.waveStrength-2 .wv3.wave,
.waveStrength-1 .wv4.wave,
.waveStrength-1 .wv3.wave,
.waveStrength-1 .wv2.wave {
  border-top-color: #eee;

}


</style>