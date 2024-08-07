<template>
   <div class="overflow-hidden">
    <div  :style="{background :`url(${test})` , filter : 'hue-rotate(-194deg)' , position: 'relative' ,  backgroundSize: 'cover'  }" class="relative h-100 lg:h-screen pb-10 bg-cover  w-full  ">
       <img class="w-full lg:hidden" height="200px" src="../assets//images//key7.jpg" alt="">
       
       
       <div  class="flex flex-col container justify-center lg:flex-row lg:justify-center " >
           <div class=" ml-5 lg:mt-64">
               <h1 style="color:rgb(19, 255, 255)" class="text-white lg:text-3xl  uppercase text-3xl text-center my-2 text-bold ">PRO STORE</h1>
               <h1 style="color:rgb(255, 255, 255)" class="text-white   uppercase text-lg text-bold ">اكبر متجر متكامل لكل المنتجات  في السودان </h1>
              <div class="flex justify-center">
                <router-link  to="/shop">
                    <button style="border: 1px solid blueviolet; border-radius: 10px;" class="text-white   uppercase text-xl p-2 mt-4 w-64  text-bold">
                تسوق الان 
               </button>
                </router-link>   
              </div>  
            </div>
            <div  class="lg:w-1/2">

            </div>
        </div>
    </div>
    <div 
    class="mb-20 container mx-auto " >
        <div data-aos="zoom-out-up" class="mt-20">
                <!-- <h1 style="direction: rtl;" class="text-2xl  px-5 font-bold text-maincolor "> اخر المنتجات >  </h1> -->

              <div class="flex gap-4 mt-2 flex-wrap justify-center">
                <!-- <div>
             
             <Card   :card="card" v-for="item in carditem" :productImg ='item.img_url' :idProduct="item._id"  :key="item.id" :title="item.title" :price="item.price" /> 
        
         </div> -->
              </div>
               
        </div>
        <!-- <div data-aos="zoom-out-up" class="mt-20">
            <h1 style="direction: rtl;" class="text-2xl  px-5 font-bold text-maincolor ">  الافضل >  </h1>

              <div class="flex gap-4 mt-2 flex-wrap justify-center">
                <prodduct v-for="item in carditem"  :key="item.id" :name="item.name" :price="item.price"  />
              </div>
               
        </div> -->
        

    </div>
   </div>
</template>

<script setup>
// import AOS from 'aos'
//  import prodduct from '../components/carD.vue'
// import { onMounted, ref  } from 'vue'
import tessst from "../assets//images//key7.jpg";
// import store from '../store'
// import {ref , onMounted} from 'vue'
// import Card from '../components/carD.vue';
// import store from '../store/index'
// let carditem = ref([])
let test = tessst
// let getProduct = ()=>{

//   store.dispatch('product/get').then((res)=>{

//     carditem.value = res
//   })
  
// }

// onMounted(()=>{
//  getProduct()
// })


// export default {
//     components :{
//         // prodduct
//     } ,
//     data(){
//         return {
//        test : tessst ,
//      carditem : [] 
//         }
//     } ,
//    computed :  {
//      getProduct : ()=>{

// store.dispatch('product/get').then((res)=>{
// console.log(this.carditem)
// console.log(res)
// })

// }
//    } , 
//    created (){
//     this.getProduct
//    }
   


    
// }
</script>
<style scoped>


.imfly {
    animation: bgfly 2s infinite;
}
.background {
  background-image: url("../src/assets/images/key7.jpg");
 /* filter  :   hue-rotate(-194deg) ; 
  background-size: cover;
  width: 100%;
  height: 83vh;
  position: relative; */
}
@keyframes bgfly {
    0% {
   transform: translateY(8px);
}
50% {
    
    transform: translateY(0px);

}
100%{
    
    transform: translateY(8px);
    }
}
</style>