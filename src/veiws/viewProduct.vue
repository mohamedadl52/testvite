<template>
    <div>
    <div class="flex justify-center mt-10">
      <div class=" w-64 lg:w-1/2  relative">

        <div>
          <img   :src="'https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/'+ selectImg +'.png'" class="w-full h-64 lg:h-1/2 bg-cover mb-10  " alt="">
        </div>
     <div   class="flex gap-2">

    <img @click="selectimage(img)" v-for="img in productImg" :key="img"  :src="'https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/'+ img +'.png'" class="w-16  h-16 " alt="">

     </div>
     <div class="w-full  bgwork2 flex justify-center  items-center h-48 absolute top-0 left-0 " >  
       <div class="absolute  iconspage top-1/2 left-1/3">
       <a href="#jbdv">
         <font-awesome-icon
                  
                class="
                     text-white
                     bg-maincolor
                     p-2
                     rounded-full
                     hover:text-gray-600
                     transition-all
                     duration-500
                     text-xl
                     mx-2
                     cursor-pointer
                   "
                   :icon="['fas', 'cart-plus']"
                
                   />
       </a>
                 <font-awesome-icon
                   class="
                   text-white
                     bg-maincolor
                     p-2
                     rounded-full
                     hover:text-red-600
                     transition-all
                     duration-500
                     text-xl
                     mx-2
                     cursor-pointer
                   "
                   :icon="['fas', 'heart']"
                 />
     </div>
     </div>
      <div class="px-2 py-1">
       <div class="flex justify-between mt-2">
         
       <p class="text-xl font-bold text-seconcolor">{{ product.title }}</p>
       <font-awesome-icon
                   class="
                   text-white
                     bg-maincolor
                     p-2
                     rounded-full
                     hover:text-red-600
                     transition-all
                     duration-500
                     text-xl
                     mx-2
                     cursor-pointer
                   "
                   :icon="['fas', 'heart']"
                 />
       </div>
       <p class="text-center flex gap-2 justify-center"> <span class="text-maincolor text-2xl font-bold">جنيه</span> <span class="text-maincolor text-2xl font-bold"> {{product.price}}  </span> </p>
        <p> 
         <!-- <font-awesome-icon
                   class="
                     text-yellow-500
                     rounded-full
                     transition-all
                     duration-500
                     text-xl
                     cursor-pointer
                   "
                   :icon="['fas', 'star']"
                 /> 
               
                 <font-awesome-icon
                   class="
                     text-yellow-500
                     rounded-full
                     transition-all
                     duration-500
                     text-xl
                     cursor-pointer
                   "
                   :icon="['fas', 'star']"
                 />
                 <font-awesome-icon
                   class="
                     text-yellow-500
                     rounded-full
                     transition-all
                     duration-500
                     text-xl
                     cursor-pointer
                   "
                   :icon="['fas', 'star']"
                 />
                 <font-awesome-icon
                   class="
                     text-yellow-500
                     rounded-full
                     transition-all
                     duration-500
                     text-xl
                     cursor-pointer
                   "
                   :icon="['fas', 'star']"
                 />
                 <font-awesome-icon
                   class="
                     text-yellow-500
                     rounded-full
                     transition-all
                     duration-500
                     text-xl
                     cursor-pointer
                   "
                   :icon="['fas', 'star']"
                 /> -->
               
           <!-- <span class="text-lg ml-2 text-seconcolor ">(150)</span> -->
              
         </p> 

         <p class="text-center p-2">
                <a href="https://wa.me/249907452551" class="text-white bg-maincolor p-1 text-center font-bold px-4">
                
                اطلب الان</a>
               </p>
     </div>
  
  </div>
</div>
<div style="direction: rtl;">
     <p class=" lg:px-10  text-center leading-8 bg-red-500 font-bold text-lg lg:text-xl  uppercase w-64 mt-10 rounded-l-2xl  pl-10 text-white">
       الوصف
     </p>

     <div class="text-xl text-center font-bold px-2 mt-4  mb-20 lg:px-10  ">
        {{ product.description }}
     </div>
</div>
</div>
</template>

<script>
import store from "@/store/index.js";
import Product from "../models/product";

export default {
  components : {
   
  } ,
  data: function () {
    return {
      product: new Product("", "" , "" , "" , ""),
      fileimg: "",
      productImg : [] , 
      catogress: null,
      selectImg : '',
      news : true ,
            cat : true ,
            modelV : true
    };
  },
  computed: {
    // currentUser() {
    //   return store.state.auth.user;
    // },
  },
  mounted() {
    // if (!this.currentUser) {
    //   this.$router.push("/login");
    // }
    this.getproductId()
  },
  methods: {
    getproductId(){
      store.dispatch('product/getProduct' , this.$route.params.id).then((res)=>{
        this.product.title = res.title
        this.product.price = res.price
        this.product.description = res.description
        this.product.qyt = res.qyt
        this.productImg = res.img_url
        this.selectImg = res.img_url[0]
      })
    } ,
    selectimage (img){

this.selectImg =  img
    }
 
 
  },
};
</script>

<style scoped>

.bgwork   {
background: rgba(0, 0, 0, 0.4);
transition: all 0.5s;
}
.bgwork2 , .iconspage {
 transition: all 1s;
}
.iconspage {
 display: none;
}
/* .bgwork:hover {
 background: rgba(0, 0, 0, 0.8);
 cursor :pointer
}
.bgwork2:hover {
 background: rgba(0, 0, 0, 0.8);
 cursor :pointer
} */
/* .bgwork2:hover  .iconspage{
 display: block;
} */
.img:first-child {
  width: 100%;
}

</style>
