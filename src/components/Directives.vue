<template>
<p>1. Adding a raw HTML value</p>
<p v-html="rawHTML"></p>
<p>2. Dynamic Attributes</p>
<button :disabled="isDisabled">Sa</button> <br>
<p>3. Binding an object of attributes to an element</p>
<a v-bind="objectOfAttributes">Hello</a>
<p>4. Built-in Directives</p>
<!-- v-text -->
<button @click="methodForVtextDirective" v-text="text"></button> <br>
<!-- v-html, v-if, v-else, v-else-if  ALREADY KNOW-->
<!-- v-for FOR ARRAY -->
<div v-for="(item, index) in listArray" :key="index+1">  
  <span>{{index + 1}} - {{item}}</span>
</div> <br>
<!-- v-for FOR OBJECT -->
<div v-for="(value, key) in listObj" :key="key">
  <span>{{key}} - {{value}}</span>
</div> <br>
<div v-for="(value, key, index) in listObj" :key="key">
  <span>{{key}} - {{value}} - {{index}}</span>
</div> <br>
<!-- v-for FOR MAPS or SETS -->
<div v-for="(item, index) in listSet" :key="index">
  <span>{{item}} - {{index}}</span>
</div>
<!-- v-on === @ but if you want to use multiple events in an obj just like v-bind we will use v-on-->
<button v-on="{ click: handleClickForVOn, mouseover: handleMouseOverForVOn, mouseleave: handleMouseLeaveForVOn}">{{text}}</button> <br>
<!-- v-model INTO ITS OWN COMPONENT -->
<input>
<select></select>
<textarea></textarea> <br>
<!-- v-pre -->
<span v-pre>{{ this will not be compiled <a href="#">get to top</a>}} 
</span>
</template>

<script>
export default {
  name: 'Directives',
  data() {
    return {
      rawHTML: `<span style="color:red">I'm an HTML tag</span>`,
      isDisabled: true, //false
      objectOfAttributes: {
        style: 'text-transform: uppercase;',
        class: 'class-for-link'
      },
      text: 'text1',
      listArray: ['Potato', 'Tomato', 'Carrot'],
      listObj: {
        veg: 'Potato',
        fruit: 'Apple',
        amount: 4,
        sex: false, 
      },
      listSet: new Set([1,2,3,4,1,2,3,4,5,5]),
    }
  },
  methods: {
    methodForVtextDirective() {
      if(this.text === 'text1')
      this.text = 'text2'
      setTimeout(() => {
        if(this.text === 'text2')
        this.text = 'text3'
      }, 1000);
      setTimeout(() => {
        if(this.text === 'text3')
        this.text = 'text1'  
      }, 3000);
         
    },
    handleClickForVOn() {
      this.text = 'clicked';
    },
    handleMouseOverForVOn() {
      this.text = 'hovering';
    },
    handleMouseLeaveForVOn() {
      this.text = 'text1'
    }
  }
}
</script>


<style scoped>
  .class-for-link {
    text-decoration: underline;
    color: aqua;
  }
</style>
