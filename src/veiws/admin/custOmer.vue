<template>
    <div>
   
      <div  class="flex min-h-screen  w-full flex-row">
          <!-- start aside left part  -->   
          
       <navbar :cat="cat" :news="news" /> 
          <!-- end aside left part  -->
        
             <!-- start right aside  -->

                      <div  class="w-full" style="background-color : #22222F">
                          <div class="bars ml-4 mt-2" @click="news =! news">
                              <div class="w-10 h-1 bg-white  my-1"></div>
                              <div class="w-10 h-1 bg-white  my-1"></div>
                              <div class="w-10 h-1 bg-white  my-1"></div>
                          </div>
                                 <div>
                                    <div>
                                         <select id="" class="w-64 ml-12 px-5 py-2 mt-4" name="">
                                            <option value="">all</option>
                                            <option value="">user</option>
                                            <option value="">mods</option>
                                            <option value="">admin</option>
                                         </select>
                                    </div>
                                    <div class="p-2 bg-cyan-900 text-white w-32 ml-10 mt-10 text-center cursor-pointer"><router-link to="product/add">اضف منتج</router-link></div>
                                        <table border="1" class="text-white text-center  border-2 w-full mx-auto font-semibold  mt-10 ">
                                           
                                           <tbody>
                                            <tr v-for="product in products" :key="product.id">
                                                <td class="border-2 flex gap-2 items-center">
                                                    <img v-if="product.img_url[0] " class="w-20" :src="'https://res.cloudinary.com/dekh1kgki/image/upload/v1722212103/'+ product.img_url[0] + '.png' " alt="">
                                                    
                                                    {{product.title}}</td>
                                           
                                                <td class="border-2"><span @click="deleteProduct(product._id , product.catogres)" class="text-red-500 cursor-pointer">delete </span>/ <span class="text-green-500 cursor-pointer"><router-link :to="'/admin/product/update/'+product._id">edit</router-link></span> / <router-link :to="'/viewProduct/'+product._id" class="text-orange-400">veiw
                                                </router-link></td>
                                            </tr>
                                         
                                           </tbody>
                                        </table>

                                 </div>
                      </div>

                      <div id="model" :class="modelV ? 'hidden' :'flex' " class="absolute w-1/2 h-1/2 flex justify-center items-center top-1/4 left-1/4 shadow-xl  bg-white
                      ">
                        <span class="absolute cursor-pointer right-3 top-1 text-2xl" @click="modelV = true">X</span>
                            <div class="w-full flex justify-center items-center flex-col p-2">
                                <input id="" type="text" class="p-2 border border-black w-full" name="" placeholder="add catogress"> <br>
                                <input
type="submit" value="add" class="bg-maincolor text-white font-semibold
                                 p-1 mt-4  px-4">
                            </div>
                      </div>
             <!-- end right aside   -->
  
              </div>
      </div>
  
  </template>
  
  <script>
import store from '../../store';
import navbar from "/src/components/admin/navBar.vue";
export default {
components : {
    navbar
},
    data(){
        return{
            news : true ,
            cat : true ,
            modelV : true , 
            products : null
    } }, 
    methods : {
        getProduct(){
         store.dispatch('product/get').then((res)=>{
             this.products = res
         })
        }, 
        deleteProduct(product , catogress){
         store.dispatch('product/delete' , {product , catogress}).then(()=>{
            this.getProduct()
         })
        } 
    } ,
    created(){
        this.getProduct()
    }
} 
  </script>

<style scoped>
table td {
    padding: 10px;
}
table td:last-child {
    padding-left: 20px;
}
</style>
  
