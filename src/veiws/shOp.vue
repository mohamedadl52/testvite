<template>

<div>
        
  <div class="visitor-count-container">
    <h2 :style="{ color: visitorColor }" class="visitor-count visitor-count-animation">عدد الزوار: {{ visitorCount }}</h2>
  </div>
        <!-- Your existing template code here -->
        <div>
            
        <p class="px-20 mt-4">
    
    <font-awesome-icon
      class="text-seconcolor hover:text-gray-600 transition-all duration-500 text-2xl "
      :icon="['fas', 'home']"
    />  <font-awesome-icon
      class="text-seconcolor hover:text-gray-600 transition-all duration-500 text-xl mr-1"
      :icon="['fas', 'chevron-right']"
    />  
     <span class="text-lg text-seconcolor font-bold">shop</span>
    </p>
    
    <div class="container lg:flex p-4  mx-auto">
         <div :class="hidecat ? 'left-0' : '-left-64'" class="catogress z-20 bg-white transition-all  duration-500  absolute   lg:static  shadow-lg p-10 mr-10 hidden ">
            <div>
                <h1>Catogress</h1>
              <ul>
                <li>
                    <input id="" type="checkbox" name=""> <span>bathroom</span> <span>(200)</span>
                </li>
                <li>
                    <input id="" type="checkbox" name=""> <span>sofa</span> <span>(100)</span>
                </li>
                <li>
                    <input id="" type="checkbox" name=""> <span>office</span> <span>(120)</span>
                </li>
              </ul>
            </div>
            <div>
                <h1>brands</h1>
              <ul>
                <li>
                    <input id="" type="checkbox" name=""> <span>brand1</span> <span>(200)</span>
                </li>
                <li>
                    <input id="" type="checkbox" name=""> <span>brand2</span> <span>(100)</span>
                </li>
                <li>
                    <input id="" type="checkbox" name=""> <span>brand3</span> <span>(120)</span>
                </li>
              </ul>
            </div>
            <div>
              <h1>price</h1>
              <div class="flex">
                <input type="text" class="w-16 border " placeholder="min">  -  <input class="w-16 border " type="text" placeholder="max">
                
                </div>
            </div>
    
            <div>
                <h1>size</h1>
                <div class="flex gap-1">
                    <span class="p-1 text-sm bg-maincolor font-bold text-white">XS</span>
                    <span class="p-1 text-sm bg-maincolor font-bold text-white">S</span>
                    <span class="p-1 text-sm bg-maincolor font-bold text-white">M</span>
    
                </div>
            </div>
            <div>
                <h1>color</h1>
                <div class="flex gap-1">
                    <span class="p-1 text-sm w-4 h-4 bg-maincolor font-bold text-white"></span>
                    <span class="p-1 text-sm w-4 h-4 bg-red-400 font-bold text-white"></span>
                    <span class="p-1 text-sm w-4 h-4 bg-yellow-200 font-bold text-white"></span>
    
                </div>
            </div>
            
         </div>
         <div class="w-full">
                <div class="flex justify-between flex-row-reverse w-full items-center ">
                     <div  >
                        <select  @change="filterPro()" v-model="selected[0]" class="border bg-maincolor text-white border-seconcolor p-2 px-5 font-semibold text-left">
                          <option value="all" selected>كل الخدمات</option>  
                          <option v-for="(item) in catogress" :value="item._id" :key="item.id" >{{item.type}}</option>
            
                        </select>
                      
                     </div>
                     <div>
                        <!-- <font-awesome-icon
              class="text-white bg-maincolor hidden p-2 hover:text-gray-600 transition-all  duration-500 text-2xl mx-2"
              :icon="['fas', 'bars']"
              @click="hidecat =! hidecat"
            /> -->
               
                        <!-- <font-awesome-icon
              class="text-white hidden   bg-maincolor p-2  transition-all duration-500 text-2xl mx-2"
              :icon="['fas', 'bars']"
              @click="card =! card"
              :class="card ? 'lg:inline animationCard' : 'lg:hidden animationCard2'"
    
            />
               
                        <font-awesome-icon
    
              class="text-white hidden lg:inline  bg-maincolor p-2  transition-all duration-500 text-2xl mx-2"
              :icon="['fas', 'home']"
              @click="card =! card"
              :class="card ? 'lg:hidden animationCard' : 'lg:inline animationCard2'"
            /> -->
    
    
            <!-- <select v-model="selected[0]" class="border bg-maincolor text-white border-seconcolor p-2 px-5 font-semibold text-left">
                          <option value="all" selected>كل الخدمات</option>  
                          <option v-for="(item) in catogress" :value="item.type" :key="item.id" >{{item.type}}</option>
            
                        </select> -->
                     </div>
    
                </div>
                  <div v-if="carditem" :class="card ? 'flex-row animationCard' : 'flex-col animationCard2'" class="flex gap-4 flex-row transition-all duration-500 items-center  mt-2 flex-wrap justify-center  ">
                 
                      <Card   :card="card" v-for="item in carditem" :productImg ='item.img_url[0]' :idProduct="item._id"  :key="item.id" :title="item.title" :price="item.price" /> 
                 
                  </div>
         </div>
    </div>
        </div>
        
        <!-- Loading overlay -->
        <div v-if="loading" class="loading-overlay">
            <div class="loading-spinner"></div>
            <p class="loading-text">الرجاء الانتظار</p>
        </div>
    </div>


    
</template>
<script setup>
// import AOS from 'aos'


import {ref , onMounted} from 'vue'
import Card from '../components/carD.vue';
import store from '../store/index'
let carditem = ref([])
let catogress = ref([])
let selected = ref(['all'])
let loading = ref(false);


let getProduct = ()=>{

  store.dispatch('product/get').then((res)=>{

    carditem.value = res
  })
  
}
        
let fetchVisitorCount = () => {
  fetch('https://shop-le2d.onrender.com/visitorCount')
    .then(response => response.json())
    .then(data => {
      visitorCount.value = data.count;
    });
};

let incrementCount = () => {
  fetch('https://shop-le2d.onrender.com/incrementCount', { method: 'POST' })
        .then(response => response.json())
        .then(data => {
          if (data.success) {
            this.fetchVisitorCount();
          }
        });
};
let getCatogress = ()=>{
  loading.value = true;

  store.dispatch('catogress/get').then((res)=>{
    
    catogress.value = res.Catogress
    loading.value = false;
         })

}
let filterPro  =  ()=>{
  console.log(selected.value[0])

  if(selected.value[0] == "all") {
    getProduct()

  }else {
    store.dispatch('catogress/filter' , selected.value[0]).then(res =>{
      carditem.value = res
    })

  }
}
onMounted(()=>{
  incrementCount() ;
  fetchVisitorCount();
 getProduct()
 getCatogress()

})
let card = ref(true)

let hidecat = ref(false)
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&display=swap');

.catogress h1 {
 @apply text-seconcolor text-xl font-bold my-4 mb-2 uppercase
}
.catogress ul li  {
    @apply text-lg whitespace-nowrap
}
.animationCard  { 
     animation: test 2s 1;
}
.animationCard2  { 
     animation: test2 2s 1;
}

@keyframes test {
  0%{
  /* transform: translateX(0px); */
  opacity: 0;
}

100%{
  
  /* transform: translateX(0px); */
  opacity: 1;
  }
}
@keyframes test2 {
  0%{
  /* transform: translateX(0px); */
  opacity: 0;
}

100%{
  
  /* transform: translateX(0px); */
  opacity: 1;
  }
}

.loading-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.8);
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    z-index: 9999;
}

.loading-spinner {
    border: 8px solid rgba(0, 0, 0, 0.1);
    border-top: 8px solid #3498db;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
}
.loading-text {
    margin-top: 10px;
    font-size: 16px;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

.visitor-count {
  
  font-size: 20px;
  margin: 0;
  font-weight: bold;
  font-family: 'Amiri', sans-serif; /* Applying a nice Arabic font */
        }
        
.visitor-count-animation {
  animation: colorChange 2s infinite alternate; /* Alternate color change animation */
}
/* Loading spinner styles */
        
@keyframes colorChange {
  0% { color: #f00; } /* Start color */
   100% { color: #00f; } /* End color */
}
</style>
