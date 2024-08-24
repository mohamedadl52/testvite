<template>
   <div class="overflow-hidden">
  
    <div v-if="loading" class="loading-spinner"></div>
    <div v-else>
               
    
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
            
        </div>
          </div>
        <div v-if="carditem" class="mt-20 ">
       
                <h1 v-if="carditem" style="direction: rtl;" class="text-2xl  px-5 font-bold text-maincolor "> اخر المنتجات >  </h1>

              <div class="flex gap-4 mt-2 flex-wrap flex-row-reverse justify-center">
          
                
                <Card v-for="item in filteredCardItems" :key="item._id" 
          :productImg="item.img_url[0]" :idProduct="item._id" :title="item.title" :price="item.price" />  
        
        </div>
              
        

        <p class="text-blue-500 text-xl font-bol
         ml-20 mt-2">عرض المزيد</p>
        

    </div>
        <div v-if="carditem" class="mt-20 ">
                <h1 style="direction: rtl;" class="text-2xl  px-5 font-bold text-maincolor "> منتجات الهواتف >  </h1>

              <div v-if="carditem" class="flex gap-4 mt-2 flex-wrap flex-row justify-center">
            
             
                <Card v-for="item in filterephoensItems" :key="item._id" 
          :productImg="item.img_url[0]" :idProduct="item._id" :title="item.title" :price="item.price" />   </div>
              
        

        <p class="text-blue-500 text-xl font-bol
         ml-20 mt-2 mb-10">عرض المزيد</p>
        

    </div>
    </div>
      </div>
   
       
</template>

<script setup>
// import AOS from 'aos'
//  import prodduct from '../components/carD.vue'
// import { onMounted, ref  } from 'vue'
import tessst from "../assets//images//key7.jpg";
// import store from '../store'
import {ref , onMounted , computed} from 'vue'
import Card from '../components/carD.vue';
import store from '../store/index'
let carditem = ref([])
let test = tessst
let getProduct = ()=>{
let loading = ref(true) 
  store.dispatch('product/get').then((res)=>{
    console.log(res)
     loading.value = false
    carditem.value = res.reverse()
  })
  
}


const filteredCardItems = computed(() => {
      return carditem.value.slice(0, 3); // Returns the first 3 items from carditem array
    });


const filterephoensItems = computed(() => {
  return carditem.value.filter(item => item.catogres._id == "66ab7a9d86053eabe1abd716" ).slice(0,3).reverse();
    });


// const getImageUrl = (img) => `https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/${img}.png`;
   

onMounted(() => {
  
  getProduct()
    });

</script>
<style scoped>
/* Add any custom styling for the slider here */


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
   
.swiper-container {
  width: 100%;
  height: 100%;
   
}

.swiper-slide img {
  width: 100%;
  height: 200px; /* Adjust the height as needed */
}

   .loading-spinner {
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-top: 4px solid #3498db;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 1s linear infinite;
  margin: 20% auto;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
.bunny-text {
  font-size: 2rem;
  font-weight: bold;

  text-align : center ;

  color: #ff69b4; /* Pink color for the bunny style */
}
@keyframes bounce-in {
  0% {
    transform: translateY(-20px);
  }
  50% {
    transform: translateY(5px);
  }
  100% {
    transform: translateY(0);
  }
}
.bounce-enter-active {
  animation: bounce-in 0.5s;
}


</style>
