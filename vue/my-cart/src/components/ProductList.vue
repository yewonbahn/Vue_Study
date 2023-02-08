<template>
  <ul class="list">
            <li v-for="(item,i) in chipsData" :key="item.title">
                <img v-bind:src="require(`@/assets/${ item.img}`)" />
                <strong>{{ item.title }}</strong>
                <span>{{ item.desc }}</span>
                <b>{{ item.price }}</b>
                <button @click="add(i)">구입하기</button>
            </li>
    </ul>
  </template>
  
  <script>
  export default {
    data(){
        return{}
    },
    props:['chipsData'],
    methods:{
        add(index){
            this.$emit('add-item',index)
        }
    }

  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style>
  </style>
  