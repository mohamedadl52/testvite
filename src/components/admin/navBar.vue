<template>
            <div  :class=" news ? '  lg:static -left-64' : '  lg:static left-0'" class="transition-all duration-700 absolute w-64 h-full top-[2rem] p-top-20 z-10 bg-gray-600"  >
  
  
  <!-- header of site -->

  <!-- end of header site -->

<!-- start list  -->
  <div>
    <ul class="">
        <router-link to="/admin">
        <li  style="background-color : #22222F" class="p-2 ml-2 rounded-l-xl" >
       <div style="background-color: #DE5634" class="p-2 mx-2  rounded-xl text-white  text-center">
        <span>
          <font-awesome-icon class="text-2xl" :icon="['fas', 'home']"></font-awesome-icon>
        </span>

        <span :class=" news ? 'opacity-0' : 'opacity-100'" class="ml-1 font-bold  transtion-all  duration-1000 delay-300">الصفحة الرئيسية</span>
       </div>
      </li>
      </router-link>

    
      <router-link to="/admin/products">
      <li class="p-2 ml-2 rounded-l-xl">
           <div style="background-color: #DE5634" class="p-2 mx-2  rounded-xl text-white text-center">
            <span>
          <font-awesome-icon class="text-2xl pointer" :icon="['fas', 'user']"></font-awesome-icon>
        </span>

        <span :class=" news ? 'opacity-0' : 'opacity-100'" class="ml-1 font-bold transtion-all duration-1000 delay-300 ">المنتجات</span>
       </div>
      </li>
      </router-link>
      <router-link to="/admin/catogress">
      <li class="p-2 ml-2 rounded-l-xl">
           <div style="background-color: #DE5634" class="p-2 mx-2 opacity-100 rounded-xl text-white text-center">
            <span>
          <font-awesome-icon class="text-2xl pointer" :icon="['fas', 'user']"></font-awesome-icon>
        </span>

        <span :class=" news ? 'opacity-0' : 'opacity-100'" class="ml-1 font-bold transtion-all duration-1000 delay-300 ">الاقسام</span>
       </div>
      </li>
 
      </router-link>
      <router-link to="/admin/catogress">
      <li class="txet-center p-2">
        <router-link style="  --tw-bg-opacity: 1;
    background-color: rgb(126 36 36 / var(--tw-bg-opacity));" class="text-white ml-4 p-2 flex justify-center"  @click="logout()" to="/logout">
           <span>
            <font-awesome-icon :icon="['fas', 'sign-out']" />
            تسجيل خروج
           </span>
          </router-link>
      </li>
      </router-link>
    </ul>
  </div>
<!-- end list  -->
</div> 
</template>

  <script>
  import store  from '../../store';
  export default {
 props : {
    news : Boolean , 
    cat :Boolean
 }  , 
 methods : {
  logout() {
       store.dispatch("auth/logout").then(()=>{
        this.$router.push("/login");
       })
    }
 }
  };
  </script>
