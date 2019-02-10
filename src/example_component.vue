<template>
  <div id="example_component">

    <h1>{{desertWelcome}}</h1> <!-- mustache is interpolating from data in the script below-->
    <button v-on:click="hideDesert" v-bind:disabled="btnState"> Hide Desert</button> <!--call a piece of data, if true disabled, if false clickable -->
    {{ hideDesert ? 'display desert' : 'do not display desert' }}

    <div class="holder">
      <ul>
        <li v-for ="(eachDesertInArray,index) in desertsAllOverTheWorld" :key="index">{{ index }}. {{eachDesertInArray.desert}} </li>
        <!-- index gives access to actual index number. Index not necessary. -->
        <!--desertsAllOverTheWorld is an array found in the data object below -->
        <!-- eachDesertInArray is a variable given to each desert object.
            Once you have this variable you can call each by their key 'desert' -->
      </ul>

      <p v-if="desertsAllOverTheWorld.length >= 5"> You know a lot of different deserts!</p>
      <p v-else> You don't know that many deserts. Pretty sad :( </p>
      <!-- if statement using v-directives. -->

    </div>

    <img v-bind:class="{ hide_class: hideDesert, flip: flipImage }"
          :src="DesertImageFileToUseAsBackground"/> <!-- no mustache with attribute (source is an attribute) use quotes-->
    <!--conditional classes, only will attach the class of hide_class if the boolean value of hideDesert is true -->
    <!--can not use '-' only use '_' in class names to use '-' needs quotes 'hide-class' -->
    <!-- use !hideDesert for opposit -->

    <img v-bind:class="desertClassObject" :src="DesertImageFileToUseAsBackground"/>
    <!-- add multiple classes using an object for some simpler syntax. Classes are held within object below-->

    <h1 v-bind:style="{backgroundColor: '#2b4b33', color: fontColor}"> STYLE BINDING</h1>
    <!--bind styles using camel case for CSS attributes. Values are variables stored below. You can also directly input values using ' ' -->
    <h1 v-bind:style="colorStyleObject"> STYLE BINDING OBJECT</h1>
    <!-- use an object instead for simpler syntax. See below. Do not need variables. CSS attribute: value -->

    <form @submit.prevent="addSkill">
      <input type="text" placeholder="Enter a desert" v-model="desert">
    </form>
    <!-- a form that will add a desert to the list. Uses addSkill method below. (prevent stops the page from reloading) -->
    <!-- the v-model variable is included below with an open string. This variable holds onto whatever the user types. -->

  </div>
</template>

<script>

import DesertImageFile from "/Users/user/kristina-coding/a-room-with-a-vue/src/assets/desert_background.jpg"

export default {
  name: 'example_component',
  data(){
    return {
      desertWelcome : "I'M THE DESERT I AM SO DRY :(", //text to interpolate in the template
      DesertImageFileToUseAsBackground: DesertImageFile,
      hideDesert: false,
      flipImage: false,
      textStyleObject: {

      },
      desertClassObject: {
        hideDesert: false,
        flipImage: false,
      },
      fontColor: "#ffb6c1",
      colorStyleObject: {
        backgroundColor:"#ffb6c1",
        color: "#2b4b33",
      },
      btnState: true,
      desertsAllOverTheWorld: [
        {desert: 'Death Valley'},
        {desert: 'Saudi Arabia'},
        {desert: 'Arizona'}
      ],
      desert: '',
      checked: false,
    }
  },
  methods: {
    addSkill() {
      this.desertsAllOverTheWorld.push({desert: this.desert}) // pushes the new desert to the desert array
      console.log(this.desert) //example of a console log
      this.desert = ''; // clears the skill box each time it is submitted so that only one thing is submitted at a time and data doesn't fill up there.
      ;
    }
  }
}
</script>


<style src="./example_component.css">

</style>
