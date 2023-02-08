<template>
  <div id>
        <h1>Sales cart 총 갯수 : {{cnt}}개, 총가격{{totalPrice}}원</h1>
        <strong>구입 목록</strong>
        <ul class="selected" >
           <li v-for="(item,i) in selectedChips" :key="item.name">
            <strong>{{item.name}}</strong>  
            <span>{{item.price}}원</span>
            <a href="" @click.prevent="deleteItem(i,item.price)" >삭제</a>
            <hr>
           </li> 
        </ul>

      <product-list 
        :chips-data="chips"
        @add-item="addWork"
        like="10">
      </product-list>
    </div>
</template>

<script>
import productList from './components/ProductList.vue'

export default {
  components: {productList},
  data(){
        return {
            cnt:0,
            selectedChips:[],
            chips:[
                        {
                        img:`mango.jpg`,
                        title:`자연그대로 망고칩`,
                        desc:`단맛이 그대로 살아있는 망고칩입니다.`,
                        price:2500
                        },
                        {
                        img:`apple.jpg`,
                        title:`천연 오가닉 사과칩`,
                        desc:`깨끗한 재료를 엄선하여 자연을 그대로 담았습니다.`,
                        price:2000
                        },
                        {
                        img:`jujube.jpg`,
                        title:`아이깨끗 대추칩`,
                        desc:`새콤함이 살아있는 반건조 대추그대로.`,
                        price:3000 }]

        }
        },
  computed:{
            totalPrice(){
                let result=0;
                this.selectedChips.forEach(item=>{
                    result += item.price;
            })
            return result}
   },
  methods:{
            deleteItem(num,price){
                this.selectedChips.splice(num, 1)
                console.log(this.selectedChips)
                this.cnt-=1;
                this.total-=Number(price)
            },
            addWork(num){
                 this.cnt+=1;
                this.selectedChips.push({name:this.chips[num].title,price:this.chips[num].price})
            
        }}
}
</script>

<style>
        * {margin:0; padding:0}
        li {list-style: none;}
        body {padding:30px;}
        .list {display:flex;  margin:20px 0;}
        .list > li { margin: 20px ; width:200px; border:1px solid gray; padding:10px;}
        .list > li > * {display:block}
        .list > li > img {width:200px; margin-bottom:20px;}
        .list > li > strong {font-size:20px; color:#666; margin-bottom:10px}
        .list > li > span{margin-bottom:10px;}
        a{color: red;} 
</style>
