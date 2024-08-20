<template>
     <div class=" w-64 h-auto shadow-2xl relative">
  <img  v-if="typeof productImg === 'string'"   :src="'https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/'+ productImg +'.png'" class="w-full h-56 object-contain mx-auto" alt="">
      <div v-if="typeof productImg !== 'string'">
    <img  v-for="img in productImg" :key="img"  :src="'https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/'+ img +'.png'" class="w-full h-56 object-contain mx-auto" alt="">
 
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
      <div class=" justify-between mt-2">
        
        <!-- <font-awesome-icon
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
                  /> -->
      <p style="text-align: center;"   class="text-sm font-bold text-center text-seconcolor ">{{ title }}</p>
      </div>
      <p class="text-center flex gap-2 justify-center"> <span class="text-maincolor text-lg font-bold">جنيه</span> <span class="text-maincolor text-lg font-bold"> {{price}}  </span> </p>
       <p class="text-center p-1"> 
       
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
                />
              
          <span class="text-lg ml-2 text-seconcolor ">(150)</span> -->
          <router-link  :to="'/viewProduct/'+idProduct" class="text-blue-500  text-center font-bold text-sm" > 
 تفاصيل
          </router-link>
        
        </p> 
               <p class="text-center p-2">
                <a href="https://wa.me/249907452551" class="text-white bg-maincolor p-1 text-center font-bold px-4">
                
                اطلب الان</a>
               </p>
        
    </div>
  </div>
</template>

<script>
export default {
    props: {
        title : {
          type :String , 
          default : ''
        }, 
        productImg : {
             validator: function(value) {
        return typeof value === 'string' || Array.isArray(value);
      }, 
          default : '' 
        }, 
        price : {
          type : Number , 
          default : null
        } , 
        card : {
          type : String , 
          default : null
        } ,
        idProduct : {
          type : String , 
          default : null
        }
    }
}
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



</style>
